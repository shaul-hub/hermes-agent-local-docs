# Domain State: Local Hermes Agent

## 현재 확인된 상태

이 문서는 현재 Discord hub bot 세션과 사용자 제공 정보를 기준으로 작성되었습니다. 실제 host 파일은 Docker 컨테이너에 mount되어 있지 않을 수 있으므로, host 상태와 container 상태를 구분해야 합니다.

## 주요 구성

### Discord hub profile

- 현재 대화는 Discord의 hub profile에서 진행됩니다.
- hub profile은 Docker terminal backend를 사용합니다.
- repo 작업 시 컨테이너 내부 경로와 host 경로가 다를 수 있습니다.

### Docker terminal backend

- terminal/read/write/search 도구는 Docker 컨테이너 안에서 동작합니다.
- 현재 repo는 컨테이너에서 `/workspace/company-ai-resource-platform` 경로로 확인되었습니다.
- 사용자가 설명한 host 기준으로는 `/workspace`가 프로젝트 repo로 mount될 수 있습니다. 실제 세션마다 mount 구성이 다를 수 있으므로 작업 전 `pwd`, `git rev-parse --show-toplevel`, `git remote -v` 확인이 필요합니다.

### GitHub CLI 인증

- 초기에 컨테이너는 host의 hub profile GitHub auth config를 보지 못했습니다.
- 이후 현재 컨테이너에서는 `GH_CONFIG_DIR=/root/.config/gh` 기준으로 `shaul1991` 계정 인증이 확인되었습니다.
- 인증 파일이나 token 값은 저장소에 기록하지 않습니다.

### Hermes Virtual Main sync

- 사용자의 운영 원칙상 home-server가 Hermes Virtual Main sync의 source-of-truth입니다.
- home-server `/root/sync/hermes-virtual-main`이 Syncthing을 통해 Mac `/Users/jihoonkim/Syncthing/hermes-virtual-main`로 동기화됩니다.
- Mac의 `~/.hermes/{config.yaml,.env,auth.json,skills}`는 해당 mirror에 symlink됩니다.
- local-only directory는 local에 유지됩니다.

### Provider / backend 원칙

- 현재 Hermes setup에서는 gateway default를 `openai-codex`로 유지합니다.
- local-claude-code provider fork는 사용하지 않습니다.
- shaul-hub의 `hermes-agent` checkout은 공식 NousResearch/hermes-agent를 추적하는 순수 official checkout으로 유지합니다.

### Discord delivery 이슈 운영 원칙

- long-response/attachment 문제는 단순 대화 규칙이 아니라 code-path 문제로 취급합니다.
- 향후 유사 문제가 생기면 코드와 테스트를 조사/수정하는 방향을 우선합니다.
- 문서를 작성하는 bot이 attachment를 직접 첨부하고, 독자에게 첨부를 확인하라고 명시해야 합니다.

## 현재 repository 상태

- GitHub repo: `shaul-hub/hermes-agent-local-docs`
- Visibility: private
- 이전 repo 이름: `shaul-hub/company-ai-resource-platform`
- 기존 AI Resource Platform 문서: `archive/ai-resource-platform-initial/`에 보존

## 열린 질문

1. host의 hub profile GitHub auth config를 컨테이너에 mount하는 장기 해결책을 적용할 것인가?
2. 이 문서 repo를 Virtual Main sync 문서와 어느 정도 연결할 것인가?
3. Discord delivery 관련 실제 코드 수정 이력은 별도 changelog로 관리할 것인가?
4. dashboard에서 확인 가능한 정보와 이 repo에서 관리할 정보를 어떻게 분리할 것인가?
