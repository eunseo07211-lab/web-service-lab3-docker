웹서비스설계 한국어 분반 · 13주차 Docker 실습

1. Docker Desktop 또는 Docker Engine을 실행합니다. Linux 컨테이너를 사용합니다.
2. 압축을 해제한 이 폴더에서 터미널을 엽니다.
   Dockerfile과 index.html이 현재 폴더에 있어야 합니다.
3. Week13_Docker_Lab_KO.html 안내를 0번 준비부터 7번 정리까지 순서대로 진행합니다.

시작 파일: index.html, Dockerfile, .dockerignore
Dockerfile은 확장자가 없는 파일입니다. Dockerfile.txt로 바꾸지 마세요.
HTML의 변경은 실습 6에서 수행합니다. 시작할 때는 v1 상태를 유지합니다.
첫 이미지 다운로드에는 인터넷이 필요합니다.

이 자료는 실습 자료입니다. 제출 마감: 2026년 12월 6일(일) 23:59 (한국시간). GitHub 저장소 URL과 실습 보고서 PDF를 제출합니다.

---
[실행 방법]
1. 이미지 빌드 (v1)
   docker build -t wsd13ko:v1 .
2. 컨테이너 실행 (A: 18381, B: 18382)
   docker run -d --name wsd13ko-a -p 127.0.0.1:18381:80 wsd13ko:v1
   docker run -d --name wsd13ko-b -p 127.0.0.1:18382:80 wsd13ko:v1
3. v2 수정 및 빌드/실행 (v2: 18383)
   index.html 수정 후 이미지 빌드 및 실행
   docker build -t wsd13ko:v2 .
   docker run -d --name wsd13ko-v2 -p 127.0.0.1:18383:80 wsd13ko:v2
4. 브라우저 접속 확인
   - v1: http://127.0.0.1:18381/?step=6 (Release v1 is online.)
   - v2: http://127.0.0.1:18383/?step=6 (Release v2 is online.)

[v1 / v2 차이]
- v1 (wsd13ko:v1): 초기 index.html 기준으로 빌드한 이미지이며, 포트 18381(wsd13ko-a), 18382(wsd13ko-b)에서 'Release v1 is online.' 화면을 제공합니다.
- v2 (wsd13ko:v2): index.html 내용을 'Release v2 is online.' 및 한글 안내 문구로 수정한 뒤 새로 빌드한 이미지이며, 별도 포트 18383(wsd13ko-v2)으로 실행해 기존 v1 컨테이너(18381)와 공존하며 v2 화면을 제공합니다.