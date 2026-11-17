# 코디세이 미션 증거 이미지 정리 (이미지 32장 → 텍스트)

> 목적: 다른 대화에서 이미지 대신 이 파일을 올려 토큰을 절약하기 위한 요약본. 각 항목의 `파일명`으로 원본 이미지를 찾을 수 있음 (확장자는 모두 .png).
> 환경: Windows / PowerShell / VSCode 터미널, 저장소 경로 `C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1`
> 표기: `PS ...\폴더>` 는 전체 프롬프트를 줄여 쓴 것. 해시/ID/지문은 이미지에서 읽은 그대로이며 판독 오차 가능. 잘린 부분은 `[잘림]`/`[판독 불가]`로 표시.
> 마스킹: 이메일은 원본 캡처에서 이미 가려져 있어 `[MASKED]`로 표기. 이미지 04/05의 PC 이름은 공개 전 마스킹 검토 권장.

## 이미지 인덱스

| 번호 | 파일명 | 증거 항목 |
|---|---|---|
| 01 | `터미널(1).png` | 현재 위치 확인, 숨김 파일 포함 목록, 폴더 생성, 이동 |
| 02 | `터미널(2).png` | 빈 파일 생성, 내용 있는 파일 생성/조회, 복사, 이름 변경 |
| 03 | `터미널(3).png` | 파일 이동, 삭제, 원상복구 |
| 04 | `권한 실습(1).png` | 파일 권한 변경 (명령 오타 에러 → 재실행 성공 → 권한 확인) |
| 05 | `권한 실습(2).png` | 읽기 전용 파일에 쓰기 시도 → 거부 확인 |
| 06 | `권한 실습(3).png` | 디렉터리 권한 변경 실험 (읽기 전용 폴더에 파일 생성 거부) |
| 07 | `도커(1).png` | Docker 버전 확인, 데몬 정보 확인 (`docker --version; docker info`) |
| 08 | `도커(2).png` | 컨테이너 목록, 이미지 목록, 컨테이너 백그라운드 실행, 로그 확인 |
| 09 | `도커(3).png` | 리소스 확인, 컨테이너 정지, 상태 확인, 삭제 |
| 10 | `git.png` | Git 버전, `git config --list`, 원격 저장소, 브랜치 |
| 11 | `step1_hello-world.png` | Docker 버전 + hello-world 실행 성공 |
| 12 | `step2_ubuntu.png` | ubuntu 컨테이너 진입 후 `ls`, `echo`, `cat /etc/os-release`, 종료 후 `docker ps -a` |
| 13 | `step3_repot.png` | attach / exec 차이 관찰 (컨테이너 종료 vs 유지) |
| 14 | `step4-1.png` | 프로젝트 파일 구조 (VSCode 탐색기) |
| 15 | `step6.png` | 커스텀 이미지 빌드 성공 + 이미지 목록 |
| 16 | `step7.png` | 포트 매핑 `-p 8080:80` 컨테이너 실행 |
| 17 | `step8-2.png` | 브라우저 접속 (주소창 + 응답 화면) |
| 18 | `step8-1.png` | 포트 매핑 `-p 8080:80` 컨테이너 재실행 (이미지 16과 같은 명령, 컨테이너 ID만 다름) |
| 19 | `step9.png` | 바인드 마운트로 호스트 변경이 컨테이너에 즉시 반영됨 |
| 20 | `step10.png` | Docker 볼륨 `mydata` 생성/연결, 데이터 쓰기, 컨테이너 삭제 후 볼륨 잔존 |
| 21 | `step11.png` | `vol-test2` 삭제 + `docker info` (명령이 두 번 중복 입력됨) |
| 22 | `보너스1.png` | `docker-compose.yml` 작성, `docker compose up -d`, `ps`, curl 접속 (포트 8090) |
| 23 | `보너스2.png` | 브라우저 접속 (Compose로 띄운 서비스, 주소창 + 응답) |
| 24 | `보너스3.png` | `docker compose logs`, `docker compose down`, 종료 후 `docker compose ps` |
| 25 | `보너스4.png` | `.env` + compose 변수 치환(`${HOST_PORT}`, `${APP_MODE}`), 포트 변경 확인, 컨테이너 안 환경변수 확인 |
| 26 | `보너스5.png` | compose-basic 정리(`down`) 후 `compose-multi` 폴더 생성, 멀티 서비스 `docker-compose.yml` 작성 |
| 27 | `보너스6.png` | 멀티 컨테이너 실행, 네트워크 확인, web → api 통신 |
| 28 | `보너스7.png` | api → web 반대 방향 통신, 호스트에서 8092 접속 |
| 29 | `보너스8.png` | SSH 키 생성 결과(파일 목록)와 공개키 내용 |
| 30 | `보너스9.png` | GitHub 웹 설정 > SSH keys에 공개키 등록 |
| 31 | `보너스10.png` | SSH 인증 테스트 (`ssh -T git@github.com`) 2회 |
| 32 | `보너스11.png` | 원격 URL을 HTTPS → SSH로 변경하고 SSH 경로로 원격 접근 확인 |

---

## A. 터미널 기본 조작 (현재 위치, 목록, 이동, 생성, 복사, 이름변경, 삭제)

### 이미지 01
- 파일명: `터미널(1).png`
- 증거 항목: 현재 위치 확인, 숨김 파일 포함 목록, 폴더 생성, 이동
- 명령/출력 (명령어 입력 + 출력 모두 보임)

```powershell
PS C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1> pwd # 현재 위치

Path
----
C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1

PS ...\codyssey-all-E1-1> ls -Force # 숨김 파일 포함 목록

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d--h--      2026-11-14   오후 2:11                .git
d-----      2026-11-14   오후 2:11                evidence
d-----      2026-11-14   오후 2:11                site
-a----      2026-11-14   오후 2:11              0 Dockerfile
-a----      2026-11-14   오후 2:31          12081 Mission.md
-a----      2026-11-14   오후 2:08           2184 README.md

PS ...\codyssey-all-E1-1> mkdir practice # 폴더 생성

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-14   오후 3:35                practice

PS ...\codyssey-all-E1-1> cd practice # 이동
PS ...\codyssey-all-E1-1\practice>
```

- 관찰: `.git`의 Mode가 `d--h--` (h = 숨김 속성). Dockerfile은 아직 0바이트.

### 이미지 02
- 파일명: `터미널(2).png`
- 증거 항목: 빈 파일 생성, 내용 있는 파일 생성/조회, 복사, 이름 변경
- 명령/출력

```powershell
PS ...\practice> New-Item empty.txt # 빈 파일 생성

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-14   오후 3:44              0 empty.txt

PS ...\practice> echo "hello" > a.txt ; cat a.txt # 내용이 있는 파일 생성 및 결과 조회
hello
PS ...\practice> cp a.txt b.txt; cat b.txt # 복사
hello
PS ...\practice> mv b.txt c.txt; ls # 이름 변경

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-14   오후 3:45             16 a.txt
-a----      2026-11-14   오후 3:45             16 c.txt
-a----      2026-11-14   오후 3:44              0 empty.txt

PS ...\practice>
```

- 관찰: `echo "hello"` 결과 파일 크기가 16바이트 (PowerShell 기본 UTF-16 인코딩 + 줄바꿈 때문으로 추정, 5글자 아님).

### 이미지 03
- 파일명: `터미널(3).png`
- 증거 항목: 파일 이동, 삭제, 원상복구
- 명령/출력

```powershell
PS ...\practice> mkdir sub; mv c.txt sub/ # 파일 이동

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-14   오후 3:54                sub

PS ...\practice> rm a.txt; rm -r -Force sub; ls; cd .. # 삭제, 원상복구

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-14   오후 3:44              0 empty.txt

PS ...\codyssey-all-E1-1>
```

- 관찰: a.txt, sub(안의 c.txt 포함) 삭제 후 empty.txt만 남음. `cd ..`로 상위 폴더 복귀.

---

## B. 권한 실습 (변경 전/후 비교)

> Windows이므로 Linux `chmod` 대신 `icacls` 사용.

### 이미지 04
- 파일명: `권한 실습(1).png`
- 증거 항목: 파일 권한 변경 (명령 오타 에러 → 재실행 성공 → 권한 확인)
- 명령/출력

```powershell
PS ...\practice> echo "HELLO" >> a.txt
PS ...\practice> cat a.txt
helloHELLO

PS ...\practice> icacls a.txt /inheritance:r /grant:r "$($env:USERNAME):R"icacls a.txt /inheritance:r /grant:r "$($env:USERNAME):R"
"icacls" 매개 변수가 잘못되었습니다.

PS ...\practice> icacls a.txt /inheritance:r /grant:r "$($env:USERNAME):R"
처리된 파일: a.txt
1 파일을 처리했으며 0 파일은 처리하지 못했습니다.

PS ...\practice> icacls a.txt
a.txt BOOK-GA1SOH1UUT\iyeeu:(R)

1 파일을 처리했으며 0 파일은 처리하지 못했습니다.
PS ...\practice>
```

- 관찰:
  - 변경 전: `>>`로 추가 쓰기 성공 (`helloHELLO`).
  - 첫 icacls는 명령이 두 번 붙여넣기 되어(`..."R"icacls a.txt ...`) 에러 → 트러블슈팅 후보 1.
  - 변경 후: 상속 제거 + 본인 계정 읽기 전용 `(R)`만 남음.
  - 화면에 PC 이름(`BOOK-GA1SOH1UUT`)과 계정명이 보임 (토큰/비밀번호는 아님, 필요하면 마스킹 검토).

### 이미지 05
- 파일명: `권한 실습(2).png`
- 증거 항목: 읽기 전용 파일에 쓰기 시도 → 거부 확인
- 명령/출력

```powershell
PS ...\practice> icacls a.txt /inheritance:r /grant:r "$($env:USERNAME):R"
처리된 파일: a.txt
1 파일을 처리했으며 0 파일은 처리하지 못했습니다.
PS ...\practice> icacls a.txt
a.txt BOOK-GA1SOH1UUT\iyeeu:(R)

1 파일을 처리했으며 0 파일은 처리하지 못했습니다.
PS ...\practice> echo "HELLO" >> a.txt
out-file : 'C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice\a.txt' 경로에 대한 액세스가 거부되었습니다.
위치 줄:1 문자:1
+ echo "HELLO" >> a.txt
+ ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Out-File], UnauthorizedAccessException
    + FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.OutFileCommand

PS ...\practice> cat a.txt
helloHELLO
PS ...\practice>
```

- 관찰: 읽기 권한(R)만 있으므로 쓰기는 `UnauthorizedAccessException`으로 거부, 읽기(`cat`)는 정상. 내용은 `helloHELLO` 그대로 유지.

### 이미지 06
- 파일명: `권한 실습(3).png`
- 증거 항목: 디렉터리 권한 변경 실험 (읽기 전용 폴더에 파일 생성 거부)
- 명령/출력

```powershell
PS ...\practice> New-item sub/b.txt

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-14   오후 5:12              0 b.txt

PS ...\practice> icacls sub /inheritance:r /grant:r "$($env:USERNAME):(OI)(CI)R"
처리된 파일: sub
1 파일을 처리했으며 0 파일은 처리하지 못했습니다.
PS ...\practice> ls sub

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice\sub

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-14   오후 5:12              0 b.txt

PS ...\practice> New-item sub/c.txt
New-item : 'C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\practice\sub\c.txt' 경로에 대한 액세스가 거부되었습니다.
위치 줄:1 문자:1
+ New-item sub/c.txt
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : PermissionDenied: (C:\Users\iyeeu\...ctice\sub\c.txt:String) [New-Item], UnauthorizedAccessException
    + FullyQualifiedErrorId : NewItemUnauthorizedAccessError,Microsoft.PowerShell.Commands.NewItemCommand
PS ...\practice>
```

- 관찰:
  - 변경 전: `sub/b.txt` 생성 성공.
  - 변경 후: 폴더에 `(OI)(CI)R`(하위 상속, 읽기 전용) 적용 → 목록 조회(`ls`)는 되지만 `sub/c.txt` 생성은 거부.
  - 이후 `sub` 폴더는 쓰기 불가 상태라 정리 시 권한 복구(`icacls sub /grant ...:F` 등) 필요할 수 있음.

---

## C. Docker 설치 및 기본 점검

### 이미지 07
- 파일명: `도커(1).png`
- 증거 항목: Docker 버전 확인, 데몬 정보 확인 (`docker --version; docker info`)
- 명령/출력 (화면 하단에서 잘림, `docker info`의 Plugins 목록까지만 보임)

```powershell
PS C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1> docker --version; docker info
Docker version 29.9.2, build a82e528
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.98.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     C:\Program Files\Docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Program Files\Docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     C:\Program Files\Docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Program Files\Docker\cli-plugins\docker-model.exe
[이하 잘림 - Server 정보 등은 이 이미지에 없음]
```

- 핵심 값: Docker 버전 **29.9.2** (build a82e528), Docker Desktop CLI 플러그인 4.98.0, Compose v5.6.1, Context `desktop-linux`.
- 주의: 이 이미지에는 `Server:` 부분이 없어 "데몬 동작 확인" 증거로는 부족할 수 있음 (다른 캡처에 Server 섹션이 있는지 확인 필요).

---

## D. Docker 기본 운영 명령 (이미지/컨테이너/로그/리소스)

### 이미지 08
- 파일명: `도커(2).png`
- 증거 항목: 컨테이너 목록, 이미지 목록, 컨테이너 백그라운드 실행, 로그 확인
- 명령/출력 (출력 순서가 터미널에서 섞여 보임)

```powershell
PS ...\codyssey-all-E1-1> docker ps -a # 목록확인(종료포함)
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS ...\codyssey-all-E1-1> docker images # 이미지 목록
>> docker run -d --name log-test ubuntu bash -c "while true; do echo hello; sleep 1; done" # 컨테이너
>> Start-Sleep 3 # 3초뒤
>> docker logs log-test # 기록확인

IMAGE                 ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest         f59abe656b69         13MB         3.94MB
hello-world:latest    cf1b20a0c89a       25.9kB         9.49kB
ubuntu:latest         065aa8626841        163MB         45.9MB
d2fd2901bb2bbfdaf9573abbff2e9785e075a02157e712a1017299f1331afce9
hello
hello
hello
hello
PS ...\codyssey-all-E1-1>
```

- 관찰:
  - 시작 시 컨테이너 0개 (`docker ps -a` 빈 목록).
  - 로컬 이미지: alpine, hello-world, ubuntu (모두 latest).
  - `docker run -d`가 컨테이너 전체 ID(`d2fd2901bb2b...`) 출력 → 백그라운드 실행 성공.
  - 3초 후 `docker logs`에 `hello` 4줄 → 1초 간격 루프 동작 확인.

### 이미지 09
- 파일명: `도커(3).png`
- 증거 항목: 리소스 확인, 컨테이너 정지, 상태 확인, 삭제
- 명령/출력

```powershell
PS ...\codyssey-all-E1-1> docker stats --no-stream # 사용량 출력
>> docker stop log-test # 컨테이너 정지
>> docker ps -a # 목록확인(종료포함)
CONTAINER ID   NAME       CPU %   MEM USAGE / LIMIT    MEM %   NET I/O         BLOCK I/O   PIDS
d2fd2901bb2b   log-test   0.22%   2.723MiB / 15.38GiB  0.02%   1.17kB / 126B   0B / 0B     2
log-test
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                          PORTS     NAMES
d2fd2901bb2b   ubuntu    "bash -c 'while true…"   52 seconds ago   Exited (137) Less than a second ago         log-test
PS ...\codyssey-all-E1-1> docker rm -f log-test keep-test # 삭제
>> docker ps -a # 목록
log-test
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS ...\codyssey-all-E1-1>
```

- 관찰:
  - `docker stats`: CPU 0.22%, 메모리 2.723MiB / 15.38GiB (0.02%), PIDS 2.
  - `docker stop` 출력은 컨테이너 이름 `log-test`.
  - 정지 후 상태 `Exited (137)` → 137 = 128+9(SIGKILL). `docker stop`의 SIGTERM에 bash 루프가 응답하지 않아 유예 시간 후 강제 종료된 것으로 해석 가능 (문서 설명 포인트로 활용 가능).
  - `docker rm -f log-test keep-test` 후 목록이 비어 있음. `keep-test`는 존재하지 않았을 가능성이 높으나, 이 이미지에는 그에 대한 에러 메시지가 보이지 않음.

---

## E. Git 설정 및 GitHub 연동

### 이미지 10
- 파일명: `git.png`
- 증거 항목: Git 버전, `git config --list`, 원격 저장소, 브랜치
- 명령/출력 (이메일은 캡처에서 이미 검은 선으로 가려져 있음 → `[MASKED]`)

```powershell
PS ...\my-web> git --version
git version 2.55.0.windows.2
PS ...\my-web> git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=schannel
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.name=Hana
user.email=[MASKED]
init.defaultbranch=main
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
remote.origin.url=https://github.com/yuk128/codyssey-all-E1-1.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
branch.main.vscode-merge-base=origin/main
PS ...\my-web> git remote -v
origin  https://github.com/yuk128/codyssey-all-E1-1.git (fetch)
origin  https://github.com/yuk128/codyssey-all-E1-1.git (push)
PS ...\my-web> git branch
* main
PS ...\my-web>
```

- 핵심 값: Git **2.55.0.windows.2**, user.name=Hana, 기본 브랜치 `main`, 원격 `origin` = `https://github.com/yuk128/codyssey-all-E1-1.git`, 현재 브랜치 `main`.
- 관찰: `init.defaultbranch`가 두 번 나옴 (앞쪽 `master`, 뒤쪽 `main`). 앞쪽은 전역/시스템 설정, 뒤쪽이 이후(로컬 또는 전역 재설정) 값으로 보이며 **마지막 값(main)이 적용됨**. 설명 시 활용 가능.
- 미확인: VSCode에서 GitHub 로그인한 화면은 이 묶음에 없음.

---

## F. 컨테이너 실행 실습 (hello-world, ubuntu, attach/exec)

### 이미지 11
- 파일명: `step1_hello-world.png`
- 증거 항목: Docker 버전 + hello-world 실행 성공
- 명령/출력

```powershell
PS ...\my-web> docker --version
Docker version 29.9.2, build a82e528
PS ...\my-web> docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
PS ...\my-web>
```

- 핵심: "Hello from Docker!" 출력 = hello-world 실행 성공. 설명문 4단계(클라이언트 → 데몬 → 이미지 pull → 컨테이너 생성/출력 전달)가 곧 Docker 동작 구조 설명.

### 이미지 12
- 파일명: `step2_ubuntu.png`
- 증거 항목: ubuntu 컨테이너 진입 후 `ls`, `echo`, `cat /etc/os-release`, 종료 후 `docker ps -a`
- 명령/출력 (여러 명령을 한꺼번에 붙여넣어서 입력줄이 먼저 모두 찍히고 결과가 뒤따라 나옴)

```powershell
PS ...\my-web> docker run -it ubuntu bash
root@af1aa9f3ee54:/# ls
echo hello
cat /etc/os-release
exit
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hello
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo
exit
PS ...\my-web> docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                     PORTS     NAMES
af1aa9f3ee54   ubuntu        "bash"     16 seconds ago   Exited (0) 7 seconds ago             relaxed_antonelli
8b1f4d054f23   hello-world   "/hello"   3 minutes ago    Exited (0) 3 minutes ago             bold_matsumoto
PS ...\my-web>
```

- 핵심: 컨테이너 안 프롬프트 `root@af1aa9f3ee54:/#`, 루트 디렉터리 목록, `hello`, Ubuntu 26.04.1 LTS 확인. 종료 후 두 컨테이너 모두 `Exited (0)`.
- 관찰: `ls`가 입력된 상태에서 나머지 3줄이 대기열로 들어가 `ls` 결과 다음에 순서대로 실행된 모양.

### 이미지 13
- 파일명: `step3_repot.png`
- 증거 항목: attach / exec 차이 관찰 (컨테이너 종료 vs 유지)
- 명령/출력

```powershell
PS ...\my-web> docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                     PORTS     NAMES
af1aa9f3ee54   ubuntu        "bash"     16 seconds ago   Exited (0) 7 seconds ago             relaxed_antonelli
8b1f4d054f23   hello-world   "/hello"   3 minutes ago    Exited (0) 3 minutes ago             bold_matsumoto
PS ...\my-web> docker run -dit --name u1 ubuntu
901862af93b60792488a1a9f9ddc412ba94821f0bbe55af684007ca587845508
PS ...\my-web> ^C
PS ...\my-web> docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
901862af93b6   ubuntu    "/bin/bash"   12 seconds ago   Up 11 seconds             u1
PS ...\my-web> docker attach u1
root@901862af93b6:/# exit
exit
PS ...\my-web> docker ps -a
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                     PORTS     NAMES
901862af93b6   ubuntu        "/bin/bash"   36 seconds ago   Exited (0) 6 seconds ago             u1
af1aa9f3ee54   ubuntu        "bash"        7 minutes ago    Exited (0) 6 minutes ago             relaxed_antonelli
8b1f4d054f23   hello-world   "/hello"      10 minutes ago   Exited (0) 10 minutes ago            bold_matsumoto
PS ...\my-web> docker start u1
u1
PS ...\my-web> docker exec -it u1 bash
root@901862af93b6:/# exit
exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug u1
    Learn more at https://docs.docker.com/go/debug-cli/
PS ...\my-web> docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
901862af93b6   ubuntu    "/bin/bash"   About a minute ago   Up 23 seconds             u1
PS ...\my-web>
```

- 핵심 관찰 (미션 요구 "attach/exec 차이"의 증거):
  - `docker attach u1` 후 `exit` → 메인 프로세스(PID 1 bash)가 끝나므로 컨테이너도 `Exited (0)`.
  - `docker start u1` 후 `docker exec -it u1 bash` → 새 bash를 추가로 띄운 것이라 `exit`해도 컨테이너는 `Up` 유지.

---

## G. Dockerfile 커스텀 이미지, 포트 매핑

### 이미지 14
- 파일명: `step4-1.png`
- 증거 항목: 프로젝트 파일 구조 (VSCode 탐색기)

```text
my-web
 └ site
    └ index.html      (U)
 └ Dockerfile         (U)
practice
Mission.md
README.md             (M)
```

- 관찰: `U` = Git 추적 전 새 파일(Untracked), `M` = 수정됨(Modified). 커스텀 이미지 소스가 `my-web/` 아래(`Dockerfile` + `site/index.html`).

### 이미지 15
- 파일명: `step6.png`
- 증거 항목: 커스텀 이미지 빌드 성공 + 이미지 목록
- 명령/출력 (화면 위쪽에 `cd my-web`, 아래 프롬프트 줄이 터미널 재그리기로 일부 겹쳐 보임)

```powershell
cd my-web
>> docker build -t my-nginx:1.0 .
>> docker images my-nginx
[+] Building 2.3s (7/7) FINISHED
 => [internal] load build definition from Dockerfile
 => => transferring dockerfile: 404B
 => [internal] load metadata for docker.io/library/nginx:alpine
 => [internal] load .dockerignore
 => => transferring context: 2B
 => [internal] load build context
 => => transferring context: 93B
 => CACHED [1/2] FROM docker.io/library/nginx:alpine@sha256:fed7e14be83cbd2661a75cdc5b872d936cf155d46c327084d30b8df19ae88d72
 => => resolve docker.io/library/nginx:alpine@sha256:fed7e14be83cbd2661a75cdc5b872d936cf155d46c327084d30b8df19ae88d72
 => [2/2] COPY site/ /usr/share/nginx/html/
 => exporting to image
 => => exporting layers
 => => exporting manifest sha256:22468b93326b9ab0856f7d4837d358edb65f988e18308135cfe17a53fda72eda
 => => exporting config sha256:ff4377134f8810ae91f8462ad63526ed1f02a2329db086c462155ecf379459d6
 => => exporting attestation manifest sha256:3caf54fed09f9e633901bdd7e73bc1e8e335dd09e0eff24533be09e064d54289
 => => exporting manifest list sha256:c246f4f04936ed11807ffaeb7702acf5856072273f0fa36b325bc1ef2d71e311
 => => naming to docker.io/library/my-nginx:1.0
 => => unpacking to docker.io/library/my-nginx:1.0

IMAGE          ID             DISK USAGE   CONTENT SIZE   EXTRA
my-nginx:1.0   c246f4f04936        93.7MB         26.4MB
PS C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1\my-web>
```

- 핵심 값: Dockerfile 404B, 베이스 `nginx:alpine`(1단계는 `CACHED` = 이미 받아둔 이미지 재사용), 2단계 `COPY site/ /usr/share/nginx/html/`, 결과 이미지 `my-nginx:1.0` (ID c246f4f04936, 93.7MB).
- 선택한 방식: 미션 (A) 웹 서버 베이스 이미지(NGINX) + 정적 콘텐츠 교체.

### 이미지 16
- 파일명: `step7.png`
- 증거 항목: 포트 매핑 `-p 8080:80` 컨테이너 실행
- 명령/출력

```powershell
PS ...\my-web> docker rm -f web1
>> docker run -d -p 8080:80 --name web1 my-nginx:1.0
>> docker ps
web1
b5e761e72bed6f07e6faa7b8faedc04b05bfe981c465718413a5626e0ecee132
CONTAINER ID   IMAGE          COMMAND                  CREATED                  STATUS                  PORTS                                         NAMES
b5e761e72bed   my-nginx:1.0   "/docker-entrypoint.…"   Less than a second ago   Up Less than a second   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp       web1
PS ...\my-web>
```

- 핵심: PORTS `0.0.0.0:8080->80/tcp` = 호스트 8080 → 컨테이너 80. (`web1`은 `docker rm -f web1`의 출력, 이전 web1 제거 후 재생성)

### 이미지 17
- 파일명: `step8-2.png`
- 증거 항목: 브라우저 접속 (주소창 + 응답 화면)

```text
[브라우저] 주소창: localhost:8080
화면 본문: "Hello, Docker!" (굵은 제목 글씨)
```

- 핵심: 주소창에 포트(`:8080`)와 응답 화면이 함께 보임 → 포트 매핑 접속 증거 요건 충족.

### 이미지 18
- 파일명: `step8-1.png`
- 증거 항목: 포트 매핑 `-p 8080:80` 컨테이너 재실행 (이미지 16과 같은 명령, 컨테이너 ID만 다름)
- 명령/출력

```powershell
PS ...\my-web> docker rm -f web1
>> docker run -d -p 8080:80 --name web1 my-nginx:1.0
>> docker ps
web1
c236c85ac5d42b3bd334ce3d656b588243cb2763ff988043d08cbd981c8aadac
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS                  PORTS                                     NAMES
c236c85ac5d4   my-nginx:1.0   "/docker-entrypoint.…"   1 second ago   Up Less than a second   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   web1
PS ...\my-web>
```

- 관찰: 이미지 16(ID b5e761e72bed)과 이미지 18(ID c236c85ac5d4)은 서로 다른 시점의 실행. 이미지 20의 `docker ps -a`에서 `web1`이 `c236c85ac5d4`(25시간 전 생성)로 나오므로 **이미지 18이 나중 실행**으로 보임.

---

## H. 바인드 마운트, 볼륨 영속성

### 이미지 19
- 파일명: `step9.png`
- 증거 항목: 바인드 마운트로 호스트 변경이 컨테이너에 즉시 반영됨
- 명령/출력 (오른쪽 끝이 잘려 일부 명령이 보이지 않음 → `[판독 불가]`, 줄바꿈 때문에 명령과 출력이 섞여 보임)

```powershell
>> Remove-Item site/index.html …                    [위쪽 일부 잘림]
PS ...\my-web> docker run -d -p 8082:80 --name web-bind -v "${PWD}/site:/usr/share/nginx/html" my-nginx:1.0; curl.exe http://localhost:8082
64ee9165aceb44e3799cdd155a97c4210c0e5cb1a55b524e837ce8a2b81f4002
<h1>Hello, Docker!</h1>
Add-Content site/index.html "<p>bind mount test</p>"; curl.exe http://localhost:8082; Get-Content site/index.html
<h1>Hello, Docker!</h1><p>bind mount test</p>
<h1>Hello, Docker!</h1><p>bind mount test</p>
PS ...\my-web>
```

- 핵심 (호스트 변경 전/후 비교):
  - 변경 전: `curl.exe http://localhost:8082` → `<h1>Hello, Docker!</h1>`
  - `Add-Content`로 호스트의 `site/index.html`에 `<p>bind mount test</p>` 추가
  - 변경 후: curl 응답 → `<h1>Hello, Docker!</h1><p>bind mount test</p>` (컨테이너 재시작/재빌드 없이 반영)
  - `Get-Content site/index.html` 결과도 같은 내용 → 호스트 파일과 컨테이너 응답 일치.
- 주의: 이 방식은 이미지가 아니라 호스트 `site/` 폴더를 `/usr/share/nginx/html`에 덮어 마운트한 것.

### 이미지 20
- 파일명: `step10.png`
- 증거 항목: Docker 볼륨 `mydata` 생성/연결, 데이터 쓰기, 컨테이너 삭제 후 볼륨 잔존
- 명령/출력 (줄이 자동 줄바꿈되어 있음)

```powershell
PS ...\my-web> docker run -d --name vol-test -v mydata:/data ubuntu sleep infinity; docker exec vol-test bash -c "echo hi > /data/hello.txt && cat /data/hello.txt"
535787f8df618dae2f196b6d4be7ff4f0b472378c65ed135409504f05b7ae2ee
hi
PS ...\my-web> docker rm -f vol-test; docker ps -a; docker volume ls
vol-test
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS                       PORTS                  NAMES
c236c85ac5d4   my-nginx:1.0   "/docker-entrypoint.…"   25 hours ago   Exited (255) 13 minutes ago  0.0.0.0:8080->80/tcp   web1
af1aa9f3ee54   ubuntu         "bash"                   27 hours ago   Exited (0) 27 hours ago                             relaxed_antonelli
8b1f4d054f23   hello-world    "/hello"                 27 hours ago   Exited (0) 27 hours ago                             bold_matsumoto
DRIVER    VOLUME NAME
local     mydata
PS ...\my-web>
```

- 핵심:
  - 연결: `-v mydata:/data`, 컨테이너 안에서 `/data/hello.txt`에 `hi` 기록 및 `cat`으로 확인 (`hi`).
  - 삭제: `docker rm -f vol-test` 후 `docker ps -a`에 `vol-test`가 없음.
  - 영속성 단서: `docker volume ls`에 `mydata` 볼륨이 **컨테이너 삭제 후에도 남아 있음**.
- 관찰: `web1`이 `Exited (255)` (13분 전) 상태 → Docker Desktop/PC 재시작 등으로 비정상 종료된 것으로 추정(확인 필요). 이 시점은 앞 묶음 대비 약 25~27시간 뒤(`hello-world`, `ubuntu`가 "27 hours ago").
- 미확인: 새 컨테이너(`vol-test2`)에서 같은 볼륨을 붙여 `cat /data/hello.txt`로 데이터가 남아 있음을 보이는 화면은 이 묶음에 없음.

### 이미지 21
- 파일명: `step11.png`
- 증거 항목: `vol-test2` 삭제 + `docker info` (명령이 두 번 중복 입력됨)
- 명령/출력

```powershell
PS ...\my-web> docker rm -f vol-test2; docker info; docker info
>>
vol-test2
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
[이하 잘림 - Server 정보 없음]
```

- 관찰: `docker rm -f vol-test2` 출력 `vol-test2` → 컨테이너 `vol-test2`가 존재했고 삭제됨 (즉 볼륨 재연결 테스트를 한 흔적, 그 결과 화면은 별도 캡처로 확보 필요). `docker info`는 `;`로 두 번 입력되어 같은 내용이 반복 출력되는 상태. 이 이미지에서도 `Server:` 섹션은 보이지 않음.

---

## I. Docker Compose 기초 (단일 서비스) + 운영 명령

### 이미지 22
- 파일명: `보너스1.png`
- 증거 항목: `docker-compose.yml` 작성, `docker compose up -d`, `ps`, curl 접속 (포트 8090)
- 명령/출력

```powershell
PS ...\compose-basic> @"
>> services:
>>   web:                       # 서비스 이름
>>     image: my-nginx:1.0     # 이미 만든 이미지 사용
>>     ports:
>>       - "8090:80"           # -p 8090:80 과 같은 뜻
>> "@ | Set-Content docker-compose.yml -Encoding utf8
>> Get-Content docker-compose.yml
services:
  web:                       # 서비스 이름
    image: my-nginx:1.0     # 이미 만든 이미지 사용
    ports:
      - "8090:80"           # -p 8090:80 과 같은 뜻
PS ...\compose-basic> docker compose up -d
[+] up 2/2
 ✓ Network compose-basic_default Created
 ✓ Container compose-basic-web-1 Started
PS ...\compose-basic> docker compose ps
NAME                  IMAGE          COMMAND                  SERVICE   CREATED         STATUS         PORTS
compose-basic-web-1   my-nginx:1.0   "/docker-entrypoint.…"   web       8 seconds ago   Up 8 seconds   0.0.0.0:8090->80/tcp, [::]:8090->80/tcp
PS ...\compose-basic> curl.exe http://localhost:8090
<h1>Hello, Docker!</h1>
PS ...\compose-basic>
```

- 핵심: 이전에 만든 이미지 `my-nginx:1.0`를 Compose 서비스 `web`으로 실행, `-p 8090:80`과 동일한 `ports` 설정. 네트워크 `compose-basic_default` 자동 생성, 컨테이너 이름은 `프로젝트-서비스-번호`(`compose-basic-web-1`).
- 파일은 PowerShell here-string(`@" ... "@`)으로 만들고 `Set-Content -Encoding utf8`로 저장 → 주석(한글) 포함.

### 이미지 23
- 파일명: `보너스2.png`
- 증거 항목: 브라우저 접속 (Compose로 띄운 서비스, 주소창 + 응답)

```text
[브라우저] 주소창: localhost:8090
화면 본문: "Hello, Docker!" (굵은 제목 글씨)
```

### 이미지 24
- 파일명: `보너스3.png`
- 증거 항목: `docker compose logs`, `docker compose down`, 종료 후 `docker compose ps`
- 명령/출력 (로그 길어서 요약 없이 핵심 줄 모두 포함, 시각은 UTC 표기)

```powershell
PS ...\compose-basic> docker compose logs
web-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
web-1  | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
web-1  | 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
web-1  | /docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
web-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
web-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
web-1  | /docker-entrypoint.sh: Configuration complete; ready for start up
web-1  | 2026/11/17 05:16:47 [notice] 1#1: using the "epoll" event method
web-1  | 2026/11/17 05:16:47 [notice] 1#1: nginx/1.31.8
web-1  | 2026/11/17 05:16:47 [notice] 1#1: built by gcc 15.2.0 (Alpine 15.2.0)
web-1  | 2026/11/17 05:16:47 [notice] 1#1: OS: Linux 6.18.58.1-microsoft-standard-WSL2
web-1  | 2026/11/17 05:16:47 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
web-1  | 2026/11/17 05:16:47 [notice] 1#1: start worker processes
web-1  | 2026/11/17 05:16:47 [notice] 1#1: start worker process 29
web-1  | ... (worker process 30 ~ 35 동일 형식)
web-1  | 2026/11/17 05:16:47 [notice] 1#1: start worker process 36
web-1  | 172.18.0.1 - - [17/Nov/2026:05:17:02 +0000] "GET / HTTP/1.1" 200 23 "-" "curl/8.21.0" "-"
web-1  | 172.18.0.1 - - [17/Nov/2026:05:18:16 +0000] "GET / HTTP/1.1" 200 23 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36" "-"
web-1  | 172.18.0.1 - - [17/Nov/2026:05:18:16 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:8090/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/157.0.0.0 Safari/537.36" "-"
web-1  | 2026/11/17 05:18:16 [error] 30#30: *2 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 172.18.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost:8090", referrer: "http://localhost:8090/"
PS ...\compose-basic> docker compose down
[+] down 2/2
 ✓ Container compose-basic-web-1 Removed   0.4s
 ✓ Network compose-basic_default Removed   0.2s
PS ...\compose-basic> docker compose ps
NAME      IMAGE     COMMAND   SERVICE   CREATED   STATUS    PORTS
PS ...\compose-basic>
```

- 핵심 관찰:
  - 로그에서 요청 2건 확인: `curl/8.21.0`(200), 브라우저 Chrome(200) → 이미지 22의 curl, 이미지 23의 브라우저 접속과 대응. (UTC 05:17~05:18 = 한국 시간 14:17~14:18)
  - `favicon.ico` 404 + error 로그는 브라우저가 자동 요청한 아이콘 파일이 없어서 생기는 정상 로그(서버 오류 아님).
  - `down` 후 컨테이너/네트워크 제거, `compose ps`는 빈 목록 → `up / ps / logs / down` 4개 운영 명령 증거 확보.

---

## J. 환경 변수 활용

### 이미지 25
- 파일명: `보너스4.png`
- 증거 항목: `.env` + compose 변수 치환(`${HOST_PORT}`, `${APP_MODE}`), 포트 변경 확인, 컨테이너 안 환경변수 확인
- 명령/출력 (입력 시 `$` 앞의 백틱은 here-string에서 PowerShell이 변수를 미리 치환하지 않도록 이스케이프한 것, 저장된 파일에는 백틱 없음)

```powershell
PS ...\compose-basic> @"
>> HOST_PORT=8091
>> APP_MODE=dev
>> "@ | Set-Content .env -Encoding utf8
>>
>> @"
>> services:
>>   web:
>>     image: my-nginx:1.0
>>     ports:
>>       - "`${HOST_PORT}:80"      # .env의 HOST_PORT 값 사용
>>     environment:
>>       - APP_MODE=`${APP_MODE}   # 컨테이너 안에 환경 변수로 주입
>> "@ | Set-Content docker-compose.yml -Encoding utf8
>>
>> Get-Content docker-compose.yml
services:
  web:
    image: my-nginx:1.0
    ports:
      - "${HOST_PORT}:80"      # .env의 HOST_PORT 값 사용
    environment:
      - APP_MODE=${APP_MODE}   # 컨테이너 안에 환경 변수로 주입
PS ...\compose-basic> docker compose up -d
>> docker compose ps
>> curl.exe http://localhost:8091
[+] up 2/2
 ✓ Network compose-basic_default Created   0.0s
 ✓ Container compose-basic-web-1 Started   0.2s
NAME                  IMAGE          COMMAND                  SERVICE   CREATED                  STATUS                  PORTS
compose-basic-web-1   my-nginx:1.0   "/docker-entrypoint.…"   web       Less than a second ago   Up Less than a second   0.0.0.0:8091->80/tcp, [::]:8091->80/tcp
<h1>Hello, Docker!</h1>
PS ...\compose-basic> docker compose exec web printenv APP_MODE
dev
PS ...\compose-basic>
```

- 핵심: `.env`의 `HOST_PORT=8091`이 `ports`에 반영되어 이전(8090)과 다른 포트(8091)로 접속 성공, `APP_MODE=dev`가 컨테이너 안에서 `printenv APP_MODE` → `dev`로 확인. "설정과 코드의 분리" 증거.

---

## K. Docker Compose 멀티 컨테이너

### 이미지 26
- 파일명: `보너스5.png`
- 증거 항목: compose-basic 정리(`down`) 후 `compose-multi` 폴더 생성, 멀티 서비스 `docker-compose.yml` 작성
- 명령/출력

```powershell
PS ...\compose-basic> docker compose down
[+] down 2/2
 ✓ Container compose-basic-web-1 Removed
 ✓ Network compose-basic_default Removed
PS ...\compose-basic> cd ..
>> mkdir compose-multi
>> cd compose-multi

    디렉터리: C:\Users\iyeeu\Desktop\코디세이\codyssey-all-E1-1

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-17   오후 2:29                compose-multi

PS ...\compose-multi> @"
>> services:
>>   web:                       # 서비스 1: 내가 만든 웹 서버
>>     image: my-nginx:1.0
>>     ports:
>>       - "8092:80"            # 외부에서 접속하는 문
>>     depends_on:
>>       - api                  # api가 먼저 뜨도록 순서 지정
>>   api:                       # 서비스 2: 보조 서비스 (외부 포트 없음)
>>     image: nginx:alpine
>> "@ | Set-Content docker-compose.yml -Encoding utf8
>>
>> Get-Content docker-compose.yml
services:
  web:                       # 서비스 1: 내가 만든 웹 서버
    image: my-nginx:1.0
    ports:
      - "8092:80"            # 외부에서 접속하는 문
    depends_on:
      - api                  # api가 먼저 뜨도록 순서 지정
  api:                       # 서비스 2: 보조 서비스 (외부 포트 없음)
    image: nginx:alpine
PS ...\compose-multi> docker compose up -d
```

- 핵심: 서비스 2개 — `web`(내 이미지 `my-nginx:1.0`, 호스트 8092 공개, `depends_on: api`)와 `api`(`nginx:alpine`, 외부 포트 없음). 마지막 줄 `docker compose up -d`는 입력만 보이고 결과는 다음 이미지에 이어짐.

### 이미지 27
- 파일명: `보너스6.png`
- 증거 항목: 멀티 컨테이너 실행, 네트워크 확인, web → api 통신
- 명령/출력 (`wget` 출력이 화면 아래쪽에서 이어서 잘림 → 다음 이미지 28에서 마무리, 오른쪽 아래에 Windows 캡처 도구 알림 팝업이 겹쳐 보임)

```powershell
PS ...\compose-multi> docker compose up -d
>> docker compose ps
[+] up 4/4
 ✓ Image nginx:alpine Pulled
 ✓ Network compose-multi_default Created
 ✓ Container compose-multi-api-1 Started
 ✓ Container compose-multi-web-1 Started
NAME                  IMAGE          COMMAND                  SERVICE   CREATED                  STATUS                  PORTS
compose-multi-api-1   nginx:alpine   "/docker-entrypoint.…"   api       1 second ago             Up Less than a second   80/tcp
compose-multi-web-1   my-nginx:1.0   "/docker-entrypoint.…"   web       1 second ago             Up Less than a second   0.0.0.0:8092->80/tcp, [::]:8092->80/tcp
PS ...\compose-multi> docker network ls
NETWORK ID     NAME                   DRIVER    SCOPE
41420e06e361   bridge                 bridge    local
0a402ea843a1   compose-multi_default  bridge    local
5cb873d16fc7   host                   host      local
ad03f27ef4d9   none                   null      local
PS ...\compose-multi> docker compose exec web wget -qO- http://api
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy,
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>
[... 다음 이미지에서 이어짐]
[화면 오른쪽 아래: Windows "캡처 도구" 알림 팝업 일부 "스크린샷이 클립보드에 복사됨 … 스크린샷 폴더에 자동으로 저장" (텍스트 잘림)]
```

- 핵심:
  - `api`는 `80/tcp`만 표시(호스트 포트 매핑 없음), `web`은 `0.0.0.0:8092->80/tcp`.
  - Compose가 `compose-multi_default` 브리지 네트워크를 자동 생성.
  - `web` 컨테이너에서 `http://api` (서비스 이름)로 접근해 nginx 기본 페이지 응답 → 서비스 이름이 DNS처럼 동작(서비스 디스커버리).

### 이미지 28
- 파일명: `보너스7.png`
- 증거 항목: api → web 반대 방향 통신, 호스트에서 8092 접속
- 명령/출력

```powershell
<p><em>Thank you for using nginx.</em></p>
</body>
</html>
PS ...\compose-multi> docker compose exec api wget -qO- http://web
<h1>Hello, Docker!</h1>
PS ...\compose-multi> curl.exe http://localhost:8092
<h1>Hello, Docker!</h1>
PS ...\compose-multi>
```

- 핵심: (맨 위 3줄은 이미지 27의 nginx 기본 페이지 마지막 부분) `api` 컨테이너에서 `http://web` 호출 → `Hello, Docker!`(내 커스텀 페이지) 응답. 즉 **web ⇄ api 양방향 통신 확인**. 호스트에서 `localhost:8092`도 정상.

---

## L. GitHub SSH 키 설정

### 이미지 29
- 파일명: `보너스8.png`
- 증거 항목: SSH 키 생성 결과(파일 목록)와 공개키 내용
- 명령/출력 (공개키 `.pub`만 출력됨, 개인키 `id_ed25519` 내용은 노출 없음. 맨 위에 `[SHA256]` 일부 줄이 잘려 있음)

```powershell
PS ...\compose-multi> ls ~/.ssh

    디렉터리: C:\Users\iyeeu\.ssh

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-09-27   오후 9:44             57 config
-a----      2026-11-17   오후 2:34            411 id_ed25519
-a----      2026-11-17   오후 2:34             97 id_ed25519.pub
-a----      2026-09-27   오후 9:09            840 known_hosts
-a----      2026-09-27   오후 8:41             96 known_hosts.old

PS ...\compose-multi> Get-Content ~/.ssh/id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEDSRAS+iszgD9PSaAnrRHVZSGoQcSKbpA6WlqjqtHK5 codyssey-bonus
PS ...\compose-multi>
```

- 핵심: ed25519 키 쌍이 오늘(2026-11-17 오후 2:34) 생성됨(`id_ed25519` = 개인키 411B, `id_ed25519.pub` = 공개키 97B). 공개키 끝 코멘트 `codyssey-bonus`.
- 보안: 공개키는 GitHub에 등록하는 용도라 노출되어도 괜찮음. **개인키(`id_ed25519`)는 절대 올리거나 출력하면 안 됨** (이 이미지에는 내용 없음).

### 이미지 30
- 파일명: `보너스9.png`
- 증거 항목: GitHub 웹 설정 > SSH keys에 공개키 등록
- 화면 내용 (브라우저 캡처, 어두운 테마)

```text
This is a list of SSH keys associated with your account. Remove any keys that you do not recognize.

Authentication keys
  [열쇠 아이콘] [SSH 배지]
  제목: my-pc
  SHA256:PRTze12MrcFQ5NHAVxsPBqYr7DHcRsfIxMNF8L5wowo
  Added on Nov 17, 2026
  Never used — Read/write
  [Delete 버튼]

Check out our guide to connecting to GitHub using SSH keys or troubleshoot common SSH problems.
```

- 핵심: 오늘(Nov 17, 2026) 키 `my-pc` 등록 완료, 이 시점 상태 `Never used`(아직 인증 사용 전), 권한 Read/write. 이 캡처에는 주소창이 보이지 않음.

### 이미지 31
- 파일명: `보너스10.png`
- 증거 항목: SSH 인증 테스트 (`ssh -T git@github.com`) 2회
- 명령/출력

```powershell
PS ...\compose-multi> ssh -T git@github.com
The authenticity of host 'github.com (20.200.245.247)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Hi yuk128! You've successfully authenticated, but GitHub does not provide shell access.
PS ...\compose-multi> ssh -T git@github.com
Hi yuk128! You've successfully authenticated, but GitHub does not provide shell access.
PS ...\compose-multi>
```

- 핵심:
  - 1회차: 처음 접속이라 호스트 지문 확인 질문 → `yes` → `known_hosts`에 github.com 추가.
  - 두 번 다 `Hi yuk128! You've successfully authenticated` → **SSH 키 인증 성공**.
  - "shell access 제공 안 함" 문구는 오류가 아니라 GitHub의 정상 응답.
  - 프롬프트 앞 빨간 ⊗ 아이콘은 이 명령의 종료 코드가 1이어서 표시된 것(GitHub SSH 테스트는 성공해도 종료 코드 1을 반환함).

### 이미지 32
- 파일명: `보너스11.png`
- 증거 항목: 원격 URL을 HTTPS → SSH로 변경하고 SSH 경로로 원격 접근 확인
- 명령/출력

```powershell
PS ...\compose-multi> cd ..
PS ...\codyssey-all-E1-1> git remote -v
origin  https://github.com/yuk128/codyssey-all-E1-1.git (fetch)
origin  https://github.com/yuk128/codyssey-all-E1-1.git (push)
PS ...\codyssey-all-E1-1> git remote set-url origin git@github.com:yuk128/codyssey-all-E1-1.git
PS ...\codyssey-all-E1-1> git remote -v
origin  git@github.com:yuk128/codyssey-all-E1-1.git (fetch)
origin  git@github.com:yuk128/codyssey-all-E1-1.git (push)
PS ...\codyssey-all-E1-1> git ls-remote origin
79f8a503157542609692f2ffede62d5aea25a2e5        HEAD
79f8a503157542609692f2ffede62d5aea25a2e5        refs/heads/main
PS ...\codyssey-all-E1-1>
```

- 핵심: 변경 전 `https://github.com/...` → 변경 후 `git@github.com:yuk128/...` (before/after). `git ls-remote origin`이 SSH로 원격의 `HEAD`와 `refs/heads/main` 커밋 해시(`79f8a50…`)를 가져옴 → SSH 경로 동작 확인.
- 주의: `ls-remote`는 읽기 확인이라 **push 성공 증거는 아님**. "SSH로 푸시 가능 확인"을 말하려면 `git push` 결과 캡처가 별도로 필요할 수 있음.

---

## 전체 진행 현황 (이미지 01~32)

| 미션 항목 | 상태 | 해당 이미지 |
|---|---|---|
| 터미널 기본 조작 | 확보 | 01~03 |
| 권한 실습 (파일 + 디렉터리) | 확보 | 04~06 |
| Docker 버전 | 확보 | 07, 11 |
| Docker 데몬(Server 섹션) | **미확보** | 07, 21 모두 Plugins까지 |
| Docker 운영 (images/ps/logs/stats) | 확보 | 08, 09 |
| hello-world / ubuntu / attach·exec | 확보 | 11~13 |
| 커스텀 이미지 빌드 | 확보 | 14, 15 |
| 포트 매핑 접속 (docker ps + 브라우저) | 확보 (8080) | 16~18 |
| 포트 매핑 2회째 | 부분: 8080 반복, 이후 8090/8091/8092는 Compose | 22, 25, 28 |
| 바인드 마운트 | 확보 | 19 |
| 볼륨 생성/연결/쓰기 | 확보 | 20 |
| 볼륨 컨테이너 삭제 후 `cat`으로 유지 확인 | **미확보** | - |
| Git 설정 + `config --list` | 확보 | 10 |
| VSCode GitHub 로그인/연동 화면 | **미확보** | - |
| 보너스: Compose 기초 | 확보 | 22, 23 |
| 보너스: Compose 멀티 + 통신 | 확보 | 26~28 |
| 보너스: Compose up/down/ps/logs | 확보 | 22, 24, 27 |
| 보너스: 환경 변수 | 확보 | 25 |
| 보너스: GitHub SSH 키 | 확보 (push 증거만 없음) | 29~32 |

## 트러블슈팅 후보 (README용 메모)

1. 이미지 04: 명령어가 두 번 붙여넣기 되어 `icacls` 매개 변수 오류 → 원인: 한 줄에 명령 중복 → 확인: 에러 메시지 + 명령 줄 점검 → 해결: 명령 한 번만 재입력.
2. 이미지 05/06: 권한 변경 후 쓰기/생성이 `UnauthorizedAccessException`으로 거부 → 의도한 결과이며, 권한이 실제 적용됐다는 증거.
3. 이미지 13: `docker run -dit`에서 `^C` 입력 후 컨테이너가 계속 `Up` → `-d`(분리 실행)라 터미널 인터럽트와 무관함을 확인.
4. 이미지 20: `web1`이 `Exited (255)`로 중단됨 → 원인 가설: Docker Desktop/PC 재시작 → 확인: `docker ps -a`, `docker logs web1` → 해결: `docker rm -f web1` 후 재실행(이미지 18의 흐름과 연결 가능).
5. 이미지 21: `docker info` 출력이 길어 Server 섹션이 화면 밖으로 밀림 → `docker info --format` 또는 `docker info | Select-String "Server Version|Containers"`로 핵심만 확인하는 방법 사용 가능.
6. 이미지 24: 브라우저 접속 시 `favicon.ico` 404 + nginx error 로그 → 원인: 브라우저가 자동으로 아이콘을 요청, `site/`에 파일 없음 → 확인: `docker compose logs`의 `GET /favicon.ico 404`, 메인 페이지는 200 → 결론: 정상 동작이며 무시 가능(필요하면 favicon 추가).
7. 이미지 31: `ssh -T` 첫 실행 시 "authenticity of host can't be established" 경고 → 원인: `known_hosts`에 github.com 지문 없음 → 확인: 표시된 ED25519 지문을 GitHub 공식 문서 지문과 대조 → 해결: `yes`로 등록 후 재실행 시 경고 없이 인증 성공.
