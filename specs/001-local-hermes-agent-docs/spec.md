# Spec: Local Hermes Agent Docs MVP

## 목적

현재 local에서 사용하는 Hermes Agent 운영, 설정, 커스텀, 복구 절차를 문서화해 다음 세션과 미래 agent가 같은 문제를 반복 조사하지 않게 합니다.

## 사용자 시나리오

### US-001: 현재 Hermes 운영 구조 파악

운영자로서 나는 hub profile, Docker backend, GitHub auth, Virtual Main sync의 현재 관계를 빠르게 파악하고 싶다.

#### Acceptance Criteria

- host와 container 상태가 다를 수 있음을 명시한다.
- GitHub auth 확인 명령과 현재 확인 상태를 문서화한다.
- Virtual Main source-of-truth와 symlink 구조를 기록한다.

### US-002: local customization 이력 확인

운영자로서 나는 공식 Hermes Agent와 local customization의 차이를 알고 싶다.

#### Acceptance Criteria

- customization마다 목적, 적용 위치, 영향 범위, rollback 기준을 기록한다.
- openai-codex provider 유지, local-claude-code provider 미사용 원칙을 포함한다.
- Discord delivery 이슈 대응 원칙을 포함한다.

### US-003: GitHub repo 작업 재현

agent로서 나는 Docker backend 안에서 GitHub repo 생성/push 전 인증 상태를 검증하고 싶다.

#### Acceptance Criteria

- `gh auth status`, `GH_CONFIG_DIR`, `hosts.yml` 확인 절차가 있다.
- host auth directory mount 방식의 장기 해결책을 기록한다.
- push 후 local/remote SHA 비교 방법이 있다.

### US-004: Hermes Dashboard와 문서 repo 역할 구분

사용자로서 나는 dashboard와 이 문서 repo가 각각 무엇을 책임지는지 알고 싶다.

#### Acceptance Criteria

- dashboard는 runtime UI, 이 repo는 운영 문서 source-of-truth로 정의한다.
- dashboard가 대체하지 않는 문서화 영역을 명시한다.

## 기능 요구사항

1. README 문서 인덱스 작성
2. product brief, domain state, glossary 작성
3. customizations 문서 작성
4. operations runbook 작성
5. GitHub auth troubleshooting 문서 작성
6. Discord delivery notes 작성
7. 기존 AI Resource Platform 문서 archive 보존

## 비기능 요구사항

- secret/token 값은 저장하지 않는다.
- 사실과 추정을 구분한다.
- host/container 경계가 드러나도록 작성한다.
- 공식 Hermes Agent repo와 이 문서 repo의 목적을 혼동하지 않는다.
