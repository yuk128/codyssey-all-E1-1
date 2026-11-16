[진행 상황 요약 - 2026-11-16 기준]

■ 환경
- Windows + PowerShell, Docker Desktop (OrbStack 아님), Docker 29.9.2, Compose v5.6.1
- 작업 폴더: ...\코디세이\codyssey-all-E1-1 (practice/, my-web/ 포함)
- GitHub 저장소: https://github.com/yuk128/codyssey-all-E1-1 (VSCode 연결됨, 커밋/푸시는 내가 직접 함)
- 증거는 전부 스크린샷으로 첨부함 (README에는 evidence/ 폴더 링크로 넣을 계획)

■ 완료 (스크린샷 있음)
1. 터미널 조작: pwd, ls -Force, mkdir, cd, New-Item, echo>, cat, cp, mv(이름 변경/이동), rm
2. 권한 실습(PowerShell icacls): a.txt 읽기 전용 → 쓰기 거부 확인, sub 디렉토리 읽기 전용 → 파일 생성 거부 확인
3. docker --version, docker info (캡처에 Client 부분만 있음, Server 부분 없음)
4. 기본 운영: images, ps -a, run -d(log-test), logs, stats --no-stream, stop, rm -f
5. hello-world 실행, ubuntu 컨테이너 진입(ls, echo, cat /etc/os-release)
6. attach vs exec 관찰: attach 후 exit → 컨테이너 종료, exec 후 exit → 계속 Up (설명 글은 README에 아직 안 씀)
7. 커스텀 이미지: my-web/ (Dockerfile + site/index.html), nginx:alpine 기반 + COPY site/, my-nginx:1.0 빌드 성공
8. 포트 매핑 1회: docker run -d -p 8080:80 --name web1 my-nginx:1.0 → localhost:8080 "Hello, Docker!" (주소창 포함 캡처)

■ 남은 필수
1. 포트 매핑 2회째 (8081:80, name web2) + curl.exe/브라우저 접속 증거
2. 바인드 마운트: 실행 명령 + 호스트 파일 변경 전/후 비교
3. Docker 볼륨: 생성, 연결, 컨테이너 삭제 전/후 데이터 유지 확인
4. Git 증거: git config --list 결과, VSCode GitHub 연동 화면 (토큰/코드 가리기)
5. README 작성: 프로젝트 개요, 실행 환경 표, 체크리스트, 수행 로그+증거 링크, 트러블슈팅 2건 이상, 개념 정리 6개(절대/상대 경로, 권한 r/w/x와 755/644, 커스텀 이미지, 포트 매핑 이유, 볼륨, Git vs GitHub), 보안 확인(마스킹)
6. 정리 작업: icacls로 잠근 a.txt, sub를 icacls <이름> /reset 으로 복구, docker info는 Server 부분까지 다시 캡처

■ README에 꼭 넣을 메모
- 환경 차이: Windows/Docker Desktop 사용, 미션은 OrbStack 기준 → 대체 방법으로 명시, chmod 대신 icacls 사용
- 트러블슈팅 후보: ① icacls 명령 중복 붙여넣기 오류(매개 변수가 잘못되었습니다) ② 읽기 전용 파일에 >> 쓰기 거부 ③ OrbStack 대신 Docker Desktop 사용
- 루트의 빈 Dockerfile/site/와 my-web/ 중 무엇을 제출 대상으로 할지 정리

■ 보너스 (전부 미착수, 필수 끝낸 후)
Compose 기초 / Compose 멀티 컨테이너 / Compose 운영 명령(up, down, ps, logs) / 환경 변수 활용 / GitHub SSH 키

■ 다음에 바로 할 것
포트 매핑 2회째 → 바인드 마운트 → 볼륨 → Git 증거 → README 정리 → (여유 되면) 보너스

■ 답변 방식 (내 선호)
- 한두 문단으로 짧게: ① 결과 해석(미션상 지금 무엇을 한 것인지) ② 이제 할 것 ③ 한 번에 붙여넣을 수 있는 명령어 ④ 다음에 할 것
- 명령어에는 설명 주석, 적당한 덩어리로 나누기, 캡처할 줄에는 "# 결과캡쳐" 표시
- 답만 주지 말고 개념을 비전공자도 알 수 있게 설명
- 커밋/푸시 안내는 불필요


