# Kali 기본기

## 주요 용어
- binary
  - 실행 가능한 파일
  - /usr/bin 또는 /usr/sbin 폴더 내부
  - 유틸리티도 포함: ps, cat, ls, ifconfig
  - 애플리케이션도 포함: 무선 해킹도구 aircrack-ng, 침입 탐지 시스템 intrusion detection system, IDS Snort
- Case sensitivity (대소문자 구분)
- directory
- home
  - /home 폴더
  - 생성된 파일이 기본적으로 저장되는 위치
- Kali
  - 칼리 리눅스는 침투 테스트를 위해 특수하게 설계횐 리눅스 배포판
  - 여러 도구가 미리 설치되어 있기 때문에 효율성 극대화
- root
  - supersuer 계정
  - 시스템의 재설정, 사용자 추가, 비밀 번호 변경
- script
  - Bash 인터프리터 환경에서 실행되는 명령어의 집합
  - python, perl, ruby
- shell
  - 리눅스 명령어 실행을 위한 환경 및 인터 프리터
  - Bash(Bourne-again shell), C 쉘, Z 쉘, ....
- Terminal
  - command line interface(CLI)

## 파일 구조

* 기본 구조
  - /root: root 사용자의 홈 디렉토리
  - /boot: 커널 이미지
  - /etc: 시스템 환경 설정 파일
  - /home: 사용자의 홈 디렉토리
  - /mnt: 리눅스와 다른 시스템 간의 인터페이스용 디렉토리
  - /media: CD, USB 장치가 마운팅되는 디렉토리
  - /proc: 내부 커널 데이터 조회
  - /sys: 커널의 하드웨어 통제
  - /dev: 특수 장치 파일
  - /bin: 바이너리
  - /sbin: 바이너리
  - /lib: 라이브러리로 dll과 비슷한 공유 프로그램
  - /usr
  - /usr/sbin
  - /usr/bin
  - /usr/lib


## 기본 명령어

- sudo passwd: root 비밀번호 변경
- su -: root로 사용자 변경
- pwd: 현재 위치
- whoami: 현재 로그인한 사용자 확인
- cd: 폴더 변경 .. ../.. ../../..
- ls(list)
  * 폴더 내용 확인
  * ls -l(long)
  * ls -a(all)
  * ls --help
- 도움말 및 매뉴얼
  * ls --help vs man ls
  * 도움말: "바이너리" --help, -help, -h, -?
  * 메뉴얼: man "바이너리"
- 파일 검색
  - locate: 현재 하위 폴더에서 파일 위치 찾기
  - whereis: 전체 바이너리 위치
  - which: PATH에 등록된 바이너리 위치, 즉 실제 실행되는 바이너리의 위치
  - find
    * find [디렉토리] [옵션] [표현식]
    * find / -type f -name apache2
    * 와일드카드: * . , ? []
- grep: 출력물 필터링
  * ps aux
  * ps aux | grep apache2

### 파일 및 디렉토리
- 파일 생성
  * cat
  * touch
- mkdir: 폴더 생성
- cp: 파일 복사
  * cp [source] [destination]
- mv: 이동 혹은 이름 바꾸기
  * mv [source] [destination]
- 삭제
  * rm: 파일 삭제
  * rmdir: 폴더 삭제
  * rm -r: 폴더 및 파일 모두 삭제
