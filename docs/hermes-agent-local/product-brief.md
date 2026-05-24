# Product Brief: Hermes Agent Local Docs

## 문제 정의

현재 local에서 사용하는 Hermes Agent에는 profile, Docker backend, GitHub 인증, Discord 운영 규칙, Virtual Main sync 등 여러 운영 지식이 존재합니다. 하지만 이 지식이 코드, 설정, 대화 기억, host 환경, 컨테이너 환경에 흩어져 있으면 다음 문제가 생깁니다.

1. 동일한 문제를 반복 진단해야 합니다.
2. host와 Docker 컨테이너의 상태 차이 때문에 원인을 오해하기 쉽습니다.
3. 어떤 설정이 공식 Hermes Agent와 local customization 중 어디에 속하는지 불명확합니다.
4. Discord delivery/attachment 같은 사용자 가시 문제의 해결 이력이 누락됩니다.
5. gateway/profile/skill/provider 변경 시 복구 절차가 불안정해집니다.

## 목표

이 저장소는 local Hermes Agent 운영과 커스텀을 재현 가능한 문서로 정리하는 것을 목표로 합니다.

## 핵심 사용자

- 운영자: local Hermes Agent profile, gateway, Docker backend, GitHub 인증을 유지보수합니다.
- 사용자/소유자: 어떤 bot/profile이 어떤 역할과 제약을 갖는지 확인합니다.
- 미래의 agent: 이전 운영 판단, 장애 원인, 해결 절차를 빠르게 파악합니다.

## Hermes Dashboard와의 관계

Hermes Dashboard는 실행 중인 agent/gateway의 상태를 관찰하거나 조작하는 UI입니다. 이 저장소는 dashboard 자체를 대체하지 않습니다. 대신 dashboard에서 보이지 않는 운영 배경, 커스텀 의도, 복구 절차, 정책을 문서화합니다.

## MVP 범위

1. 현재 local Hermes 구성 상태 정리
2. profile/gateway/provider/Docker backend 용어 정리
3. GitHub CLI 인증 문제와 Docker mount 해결책 문서화
4. Discord long-response/attachment 운영 원칙 문서화
5. Virtual Main sync의 source-of-truth와 symlink 구조 문서화
6. local customization 기록 템플릿 작성

## 비범위

- Hermes Agent 공식 문서 전체 복제
- Hermes Dashboard 기능 구현
- local provider fork 유지보수
- secret/token 값 저장
- 회사 프로젝트 문서와 개인 프로젝트 문서의 혼합

## 성공 기준

- 새 세션의 agent가 5분 안에 local Hermes 운영 구조를 이해할 수 있습니다.
- GitHub 인증/Docker mount 이슈를 재현 없이 설명하고 해결 방향을 제시할 수 있습니다.
- Discord delivery 문제가 발생했을 때 운영 규칙과 코드-path 조사 원칙을 찾을 수 있습니다.
- local customization마다 목적, 범위, rollback 기준이 기록됩니다.
