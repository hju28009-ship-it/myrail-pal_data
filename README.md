GitHub (myrail-pal_data) 설정 방법
1. 현재 데이터 파일 업로드
https://github.com/hju28009-ship-it/myrail-pal_data 에 아래 4개 파일을 올리세요:

trains.json — src/data/trains.json 복사
dia.json — src/data/dia.json 복사
stations.json — src/data/stations.json 복사
version.json — 직접 생성:

{ "version": "2026-04-23" }

2. 이후 데이터 업데이트할 때
{ "version": "2026-04-23" }     ← 첫 배포
{ "version": "2026-04-23-b" }   ← 같은 날 두 번째
{ "version": "2026-04-24" }     ← 다음 수정 배포일


# myrail-pal_data

MyRailPal 앱이 매일 1회 여기서 데이터를 받아갑니다.

---

## 파일 구성

| 파일 | 설명 |
|------|------|
| `version.json` | 버전 정보 (앱이 가장 먼저 확인) |
| `dia.json` | DIA 출무 데이터 |
| `trains.json` | 열차 목록 |
| `stations.json` | 역 목록 |

---

## version.json 형식

### 즉시 적용
```json
{
  "version": "2026-05-11"
}
→ 앱이 다음 실행 시 바로 다운로드

예약 적용 (특정 날짜 이후 적용)

{
  "version": "2026-05-22",
  "activeFrom": "2026-05-22"
}
→ 2026-05-22 이전에는 다운로드 보류, 당일부터 적용

데이터 업데이트 절차
즉시 반영할 때
dia.json 교체
version.json의 version을 오늘 날짜로 변경 (activeFrom 없음)
특정 날짜 이후 반영할 때
dia.json 교체
version.json을 아래처럼 수정:

{
  "version": "적용날짜",
  "activeFrom": "적용날짜"
}
같은 날 두 번 업데이트할 때
version 값을 다르게 써야 앱이 변경을 감지합니다:


{ "version": "2026-05-11-b" }
앱 동작 원리

앱 실행
  → version.json 확인
  → activeFrom이 오늘 이후면 → 보류 (기존 데이터 유지)
  → activeFrom이 오늘이거나 없으면 → dia.json 등 다운로드 → localStorage 저장 → 재시작
앱 번들(src/data/)보다 GitHub version이 낮거나 같으면 무시합니다.
