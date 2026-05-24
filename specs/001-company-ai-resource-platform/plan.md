# Plan: Company AI Resource Platform MVP

## 접근 방식

1. 문서 기반 MVP로 시작한다.
2. 리소스 스키마와 운영 규칙을 먼저 고정한다.
3. 초기 리소스 샘플을 등록해 사용성을 검증한다.
4. 이후 필요하면 웹 UI 또는 사내 포털 연동으로 확장한다.

## 단계

### Phase 1: Foundation

- Product Brief 정리
- Glossary 정리
- Resource 메타데이터 스키마 초안 작성
- 정책 상태 값 정의

### Phase 2: Catalog MVP

- 리소스 등록 템플릿 작성
- 카탈로그 페이지 구조 작성
- 태그 체계 초안 작성
- 샘플 리소스 5~10개 등록

### Phase 3: Review Workflow

- 신규 리소스 제안 양식 작성
- 검토 체크리스트 작성
- 승인/수정 요청/반려 기준 정리

### Phase 4: Validation

- 실제 사용자 3~5명에게 탐색 태스크 테스트
- 운영자에게 리소스 등록/검토 태스크 테스트
- 누락된 필드와 불명확한 정책 표현 개선

## 산출물

- `docs/company-ai-resource-platform/product-brief.md`
- `docs/company-ai-resource-platform/domain-state.md`
- `docs/company-ai-resource-platform/glossary.md`
- `docs/company-ai-resource-platform/research.md`
- `specs/001-company-ai-resource-platform/spec.md`
- `specs/001-company-ai-resource-platform/status.md`
- `templates/resource-template.md`
- `templates/review-checklist.md`

## 의사결정 필요 항목

- GitHub repository 이름
- 공개/비공개 여부
- 초기 리소스 owner 후보
- 승인 상태 값 최종안
- 회사 내부 정책 문서 연결 방식
