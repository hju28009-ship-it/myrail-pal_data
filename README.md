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
