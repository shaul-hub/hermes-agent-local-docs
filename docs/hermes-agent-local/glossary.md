# Glossary

## Hermes Agent

Discord, local terminal, file tools 등을 통해 작업을 수행하는 agent runtime과 운영 체계를 가리킵니다.

## Profile

Hermes Agent의 실행 단위 설정입니다. 예: `hub` profile. profile마다 memory, provider, platform 연결, terminal backend가 다를 수 있습니다.

## Gateway

model provider, platform, tool backend 등을 연결하는 Hermes 실행 구성 요소입니다.

## Hermes Dashboard

실행 중인 Hermes Agent/Gateway 상태를 관찰하거나 조작하는 UI입니다. 이 저장소는 dashboard가 아니라 local 운영 문서입니다.

## Docker terminal backend

agent의 terminal/read/write/search 도구가 host가 아닌 Docker 컨테이너 안에서 실행되는 구성입니다. host 인증, path, environment가 자동으로 보이지 않을 수 있습니다.

## GH_CONFIG_DIR

GitHub CLI(`gh`)가 인증 정보를 찾는 설정 디렉터리입니다. Docker 컨테이너 안의 `GH_CONFIG_DIR`과 host의 profile auth directory는 다를 수 있습니다.

## Virtual Main

Hermes 설정과 skill 등을 여러 환경에서 동기화하기 위한 source-of-truth mirror입니다. 현재 운영 원칙상 home-server가 source-of-truth입니다.

## Provider

LLM 요청을 처리하는 backend입니다. 현재 shaul-hub 운영에서는 `openai-codex`를 기본 provider로 유지합니다.

## local customization

공식 Hermes Agent 동작 위에 local 운영 필요에 따라 추가/변경한 설정, 규칙, 문서, 코드 수정입니다. 목적과 rollback 방법을 기록해야 합니다.

## Discord delivery

Discord 응답, long response 분할, 파일 첨부, attachment 안내 등 사용자에게 실제로 보이는 전달 경로입니다.

## Source-of-truth

특정 설정이나 문서의 최종 기준이 되는 위치입니다. 이 저장소는 local Hermes 운영 문서의 source-of-truth를 목표로 합니다.
