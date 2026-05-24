# Local Customizations

이 문서는 현재 local Hermes Agent 운영에서 공식 Hermes Agent와 구분해 관리해야 하는 커스텀/운영 결정을 기록합니다.

## 기록 형식

각 customization은 다음 항목을 포함해야 합니다.

- 이름
- 목적
- 적용 위치
- 영향 범위
- 검증 방법
- rollback 방법
- 관련 이슈/대화/commit

## 현재 기록된 customization / 운영 결정

### 1. shaul-hub hermes-agent checkout은 official upstream 추적

- 목적: local provider fork와 공식 Hermes Agent checkout을 혼동하지 않기 위함
- 적용 위치: personal shaul-hub workspace 운영 원칙
- 영향 범위: `shaul-hub/hermes-agent`
- 결정: NousResearch/hermes-agent의 순수 official checkout을 유지
- 금지: local-claude-code provider fork 유지/운영
- rollback: 사용자가 명시적으로 provider 전략 변경을 지시하기 전까지 rollback 없음

### 2. 기본 provider는 openai-codex 유지

- 목적: 현재 Hermes setup의 안정성을 유지
- 적용 위치: hub gateway/provider 운영
- 영향 범위: agent 응답과 tool orchestration
- 결정: auxiliary/provider resolver support 변경 전까지 gateway default를 `openai-codex`로 유지
- rollback: 사용자가 명시적으로 provider 변경을 요청할 때만 변경

### 3. Virtual Main source-of-truth는 home-server

- 목적: 여러 환경의 Hermes 설정을 일관되게 동기화
- 적용 위치: home-server와 Mac Syncthing mirror
- 영향 범위: `config.yaml`, `.env`, `auth.json`, `skills`
- source: home-server `/root/sync/hermes-virtual-main`
- mirror: Mac `/Users/jihoonkim/Syncthing/hermes-virtual-main`
- symlink: Mac `~/.hermes/{config.yaml,.env,auth.json,skills}`

### 4. Discord long-response/attachment 이슈는 code-path 문제로 취급

- 목적: 사용자 가시 delivery 문제를 단순 대화 규칙으로 덮지 않기 위함
- 적용 위치: Discord platform delivery path, attachment workflow
- 영향 범위: 긴 응답, 파일 첨부, MEDIA delivery
- 운영 원칙: 문제 발생 시 코드와 테스트를 조사/수정
- 검증 기준: tool return이 아니라 실제 Discord 사용자-visible attachment behavior

### 5. hub profile Docker backend와 GitHub auth 분리 인지

- 목적: host의 GitHub 인증과 container의 GitHub 인증 혼동 방지
- 적용 위치: hub profile Docker terminal backend
- 영향 범위: `gh repo create`, `git push`, GitHub API 작업
- 현재 상태: 컨테이너 내 `GH_CONFIG_DIR=/root/.config/gh` 기준 인증 확인됨
- 장기 해결: host의 hub profile gh auth directory를 container `GH_CONFIG_DIR`로 mount

## 추가 수집 필요

- 실제 Hermes Dashboard 관련 local 설정
- hub profile config 파일의 host 경로와 mount 정책
- Discord delivery code-path 수정 이력
- gateway restart/runbook
- skills customizations 목록
