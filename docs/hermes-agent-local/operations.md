# Operations Runbook

## 작업 전 기본 확인

Docker backend 환경에서는 host와 container 상태가 다를 수 있으므로 작업 전 항상 확인합니다.

```bash
pwd
git rev-parse --show-toplevel
git status --short --branch
git remote -v
echo "$HOME"
echo "$GH_CONFIG_DIR"
gh auth status
```

## GitHub 작업 절차

1. `gh auth status`로 인증 계정을 확인합니다.
2. repo remote가 의도한 GitHub repo를 가리키는지 확인합니다.
3. commit 전 `git status --short`로 변경 범위를 확인합니다.
4. push 후 local HEAD와 remote HEAD를 비교합니다.

Remote HEAD 확인 예시:

```bash
local=$(git rev-parse HEAD)
remote=$(gh api repos/shaul-hub/hermes-agent-local-docs/git/ref/heads/main --jq '.object.sha')
printf 'local=%s\nremote=%s\n' "$local" "$remote"
test "$local" = "$remote"
```

## 문서 변경 절차

1. 기존 문서를 읽고 중복/충돌을 확인합니다.
2. 문서 구조 변경은 README 인덱스와 함께 갱신합니다.
3. 운영 사실과 추정은 구분해 작성합니다.
4. secret/token 값은 기록하지 않습니다.
5. commit message는 `docs:` prefix를 사용합니다.

## Dashboard와 문서 repo 역할 분리

- Dashboard: 현재 실행 상태 확인, gateway/profile 조작, runtime 관찰
- 이 repo: 운영 원칙, customizations, 장애 원인, 복구 절차, 문서화된 결정 보존

## 장애 대응 기본 순서

1. 문제가 host인지 container인지 구분합니다.
2. environment variable과 mount 상태를 확인합니다.
3. 인증 문제는 `gh auth status`, `GH_CONFIG_DIR`, `hosts.yml` 존재 여부를 확인합니다.
4. Discord delivery 문제는 실제 사용자-visible 결과를 기준으로 확인합니다.
5. 재발 가능성이 있으면 문서와 테스트/코드 수정 항목으로 남깁니다.
