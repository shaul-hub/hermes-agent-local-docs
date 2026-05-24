# Status: Local Hermes Agent Docs

## 2026-05-24

### 완료

- GitHub repo 생성 완료
- `shaul-hub/company-ai-resource-platform`에서 `shaul-hub/hermes-agent-local-docs`로 repository rename
- local git remote를 새 repo URL로 변경
- 기존 AI Resource Platform 문서를 `archive/ai-resource-platform-initial/`에 보존
- Hermes Agent local docs용 README 작성
- Architecture HTML 문서 작성
- Product Brief 작성
- Domain State 작성
- Glossary 작성
- Customizations 작성
- Operations Runbook 작성
- GitHub Auth 문서 작성
- Discord Delivery 문서 작성
- MVP Spec/Plan 작성

### 확인된 사실

- 현재 컨테이너에서 `gh` 인증은 `shaul1991` 계정으로 확인됨
- `GH_CONFIG_DIR=/root/.config/gh` 기준 `hosts.yml` 존재
- token 값은 문서화하지 않음
- 기존 repo remote는 `https://github.com/shaul-hub/hermes-agent-local-docs.git`로 갱신됨

### 다음 작업

- Virtual Main sync 상세 문서 추가
- Hermes Dashboard와 이 문서 repo의 관계를 별도 문서로 보강
- customization record template 추가
- incident report template 추가
- 실제 host profile Docker mount config 확인 후 GitHub auth 문서 보강

### 주의

이 저장소는 Hermes Agent source fork가 아니라 local 운영 문서 저장소입니다.
