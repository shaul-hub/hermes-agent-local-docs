# Hermes Agent Local Docs

현재 local/Discord 환경에서 사용하는 Hermes Agent 운영, 설정, 커스텀, 복구 절차를 문서화하는 저장소입니다.

## 목적

Hermes Dashboard가 실행 상태를 관찰하고 조작하는 UI라면, 이 저장소는 다음 정보를 보존하는 문서 source-of-truth입니다.

- local Hermes Agent profile 구성
- Docker terminal backend 운영 방식
- GitHub CLI 인증과 repo 작업 절차
- Hermes Virtual Main sync 구성
- Discord bot 운영 규칙과 attachment/long-response 이슈 대응 원칙
- 공식 Hermes Agent checkout과 local customizations의 경계
- 장애 복구와 재현 가능한 setup/runbook

## 현재 상태

- 기존 `company-ai-resource-platform` 저장소를 `hermes-agent-local-docs`로 전환했습니다.
- 기존 AI Resource Platform 초기 문서는 `archive/ai-resource-platform-initial/`에 보존했습니다.
- 이 저장소는 현재 문서 중심이며, Hermes Agent 소스코드 fork가 아닙니다.

## 문서 인덱스

- [Architecture HTML](docs/hermes-agent-local/architecture.html)
- [Product Brief](docs/hermes-agent-local/product-brief.md)
- [Domain State](docs/hermes-agent-local/domain-state.md)
- [Glossary](docs/hermes-agent-local/glossary.md)
- [Customizations](docs/hermes-agent-local/customizations.md)
- [Operations](docs/hermes-agent-local/operations.md)
- [GitHub Auth](docs/hermes-agent-local/github-auth.md)
- [Discord Delivery](docs/hermes-agent-local/discord-delivery.md)
- [Spec](specs/001-local-hermes-agent-docs/spec.md)
- [Plan](specs/001-local-hermes-agent-docs/plan.md)
- [Status](specs/001-local-hermes-agent-docs/status.md)

## 원칙

1. 공식 Hermes Agent 소스와 local 운영 문서를 분리합니다.
2. local customizations는 이유, 적용 위치, rollback 방법을 함께 기록합니다.
3. Discord에서 드러나는 사용자 경험 문제는 단순 운영 팁이 아니라 코드/설정/테스트 관점으로 추적합니다.
4. Docker 컨테이너 내부 상태와 host profile 상태가 다를 수 있음을 명시합니다.
5. 토큰, secret, auth 파일 내용은 저장소에 커밋하지 않습니다.
