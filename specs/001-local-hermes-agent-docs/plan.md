# Plan: Local Hermes Agent Docs MVP

## 전환 결정

기존 `Company AI Resource Platform` 프로젝트는 Hermes Dashboard와 성격이 겹칠 수 있어, local Hermes Agent 운영/커스텀 문서화 프로젝트로 전환합니다.

## Repository rename

- 이전: `shaul-hub/company-ai-resource-platform`
- 이후: `shaul-hub/hermes-agent-local-docs`

## 작업 단계

### Phase 1: Repository transition

- GitHub repository rename
- git remote URL 갱신
- 기존 AI Resource Platform 문서 archive 이동
- README를 새 프로젝트 성격으로 교체

### Phase 2: Core docs

- Product Brief 작성
- Domain State 작성
- Glossary 작성
- Customizations 작성
- Operations Runbook 작성

### Phase 3: Focus docs

- GitHub Auth in Docker Backend 작성
- Discord Delivery Notes 작성
- Virtual Main sync 상세 문서 추가
- Dashboard relationship 문서 보강

### Phase 4: Validation

- 새 세션 기준 문서만 보고 GitHub auth 문제를 설명할 수 있는지 확인
- dashboard와 repo 역할이 혼동되지 않는지 확인
- Discord delivery 원칙이 사용자 요구와 일치하는지 확인

## Archive 정책

기존 AI Resource Platform 문서는 삭제하지 않고 `archive/ai-resource-platform-initial/`에 보존합니다. 이유는 다음과 같습니다.

- 초기 프로젝트 방향 전환 이력 보존
- 이후 별도 AI resource project로 재사용 가능
- repo history를 더 명확하게 유지

## 다음 작업 후보

1. `docs/hermes-agent-local/virtual-main-sync.md` 추가
2. `docs/hermes-agent-local/dashboard.md` 추가
3. `templates/customization-record.md` 추가
4. `templates/incident-report.md` 추가
5. 실제 host profile config를 근거로 Docker mount 문서 보강
