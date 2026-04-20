GitHub (myrail-pal_data) 설정 방법
1. 현재 데이터 파일 업로드
https://github.com/hju28009-ship-it/myrail-pal_data 에 아래 4개 파일을 올리세요:

trains.json — src/data/trains.json 복사
dia.json — src/data/dia.json 복사
stations.json — src/data/stations.json 복사
version.json — 직접 생성:

{ "month": "2026-04" }
2. 이후 데이터 업데이트할 때
해당 repo에서 trains.json / dia.json / stations.json 수정
version.json의 month를 해당 월로 변경 (예: "2026-05")
commit & push → 사용자들이 그달 첫 실행 시 자동 다운로드
동작 방식 요약:

앱 실행 시 이번 달에 체크했는지 확인
안 했으면 version.json fetch → 앱 내 버전과 비교
다르면 3개 파일 전부 다운로드 → localStorage 저장 → 앱 재시작
이후 실행부터는 localStorage의 최신 데이터 사용
gitHub에서 직접 생성한 version.json은 내가 확인하기 편하게 업데이트 때마다 version1.json, version2.json, version3.json... 으로 바꿔도 돼?
안 됩니다. 앱 코드가 version.json이라는 고정된 파일명으로 fetch하기 때문에 파일명이 바뀌면 404 오류가 납니다.

대신 파일 내용에 버전 번호를 추가하면 됩니다:


{ "month": "2026-05", "revision": 3 }
업데이트할 때마다 revision을 1씩 올리면 GitHub에서 파일을 열었을 때 몇 번째 업데이트인지 바로 확인할 수 있습니다. 파일명은 항상 version.json으로 유지해야 합니다.
