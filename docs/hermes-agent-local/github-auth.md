# GitHub Auth in Docker Backend

## 문제 요약

hub profile은 Docker terminal backend를 사용합니다. 따라서 host의 GitHub 인증 상태가 컨테이너 안에서 자동으로 보이지 않습니다.

초기 실패 원인은 repo 자체 문제가 아니라 다음 상태 차이였습니다.

- host에는 hub profile GitHub token/auth가 존재
- container에는 `GH_TOKEN` / `GITHUB_TOKEN`이 없음
- host의 `/Users/jihoonkim/.hermes/profiles/hub/gh`가 container에 mount되어 있지 않음
- 따라서 container에서 `gh auth status`는 not logged in으로 보일 수 있음

## 확인 명령

```bash
gh auth status
echo "$HOME"
echo "$GH_CONFIG_DIR"
test -f "$GH_CONFIG_DIR/hosts.yml" && echo exists || echo missing
env | grep -E '^(GH_TOKEN|GITHUB_TOKEN)='
```

## 현재 확인된 상태

현재 세션에서는 다음 상태가 확인되었습니다.

```text
GH_CONFIG_DIR=/root/.config/gh
Logged in to github.com account shaul1991
Git operations protocol: https
Token scopes: gist, read:org, repo, workflow
```

Token 값은 문서에 기록하지 않습니다.

## 단기 해결책

container 안에서 직접 `gh auth login` 또는 token 기반 인증을 수행합니다.

```bash
gh auth login
```

또는 운영자가 안전한 방법으로 token을 주입한 뒤:

```bash
gh auth login --with-token
```

## 장기 해결책

hub profile Docker config에서 host의 hub profile gh auth directory를 container의 `GH_CONFIG_DIR`로 mount합니다.

예시 방향:

```yaml
terminal:
  docker_env:
    HOME: /workspace/home
    GH_CONFIG_DIR: /workspace/home/.config/gh
  docker_volumes:
    - /Users/jihoonkim/personal/shaul-hub/hermes-agent-local-docs:/workspace
    - /Users/jihoonkim/.hermes/profiles/hub/gh:/workspace/home/.config/gh
```

실제 path는 현재 host의 repo 위치와 profile config에 맞게 조정해야 합니다.

## repo 생성/push 전 checklist

- [ ] `gh auth status`가 성공한다.
- [ ] 계정이 의도한 계정이다.
- [ ] token scope에 repo 작업 권한이 있다.
- [ ] `git remote -v`가 의도한 repo를 가리킨다.
- [ ] secret 파일이 git에 포함되지 않는다.
