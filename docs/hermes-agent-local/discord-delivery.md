# Discord Delivery Notes

## 원칙

Discord에서 사용자가 보는 응답 결과는 tool 내부 성공 여부보다 중요합니다. 특히 긴 응답, 파일 첨부, MEDIA delivery는 실제 Discord 사용자-visible behavior로 검증해야 합니다.

## Long response / attachment 이슈

사용자는 Discord long-response/attachment 문제를 code-path 문제로 봅니다. 따라서 향후 유사 문제가 발생하면 다음 방식으로 다룹니다.

1. 단순히 conversational rule을 추가하고 끝내지 않습니다.
2. Discord platform delivery code-path를 조사합니다.
3. attachment extraction, file upload, MEDIA marker 처리, fallback message를 확인합니다.
4. 테스트를 추가하거나 수정합니다.
5. 실제 사용자-visible attachment behavior로 검증합니다.

## 문서 전달 원칙

- 긴 문서나 결과 파일을 만든 bot이 직접 첨부합니다.
- 응답 본문에는 사용자가 첨부를 확인해야 한다고 명시합니다.
- 파일 생성만 하고 첨부 안내를 생략하지 않습니다.

## Multi-bot handoff 원칙

Discord multi-bot meeting facilitation에서는 bot 이름을 평문으로 쓰지 않고 direct mention을 사용해야 합니다.

예:

```text
<@bot_id> 다음 단계 검토해주세요.
```

## 검증 기준

- 내부 API/tool return 성공만으로 완료 처리하지 않습니다.
- 사용자가 Discord에서 실제 파일/이미지를 볼 수 있는지 확인합니다.
- 실패 시 원인을 conversation rule, platform adapter, file path, MEDIA marker, upload permission으로 나누어 조사합니다.
