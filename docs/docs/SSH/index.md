# 원격 연결

- Telnet에서 SSH로
- 설치 및 실행, 접속, key 이용해서 접속

## OpenSSH 설치 및 실행
- openssh-client와 openssh-server

1. ssh 설치 확인
  * systemd
  * dpkg -s openssh-client
  * dpkg -s openssh-server

2. ssh 실행 확인
  - systemctl status ssh
  - Main PID에서 실행 중인 프로세스의 ID 확인 필요함

3. ssh 실행 및 정지
  - systemctl start ssh
  - systemctl stop ssh

4. 부팅할 때, SSH 활성화/비활성화
  - systemctl enable ssh
  - systemctl disaable ssh

## SSH로 접속

=== "Docker"
    lxc-ls --fancy

=== "VirtualBox"
    * [참조링크](https://sarc.io/index.php/miscellaneous/2279-virtualbox-linux-ssh)
    * ip addr 혹은 ifconfig: VirtualBox에서 IP 주소 확인하기
    * ipconfig/all: Windows에서 VirtualBox의 IP 확인
    * VirtualBox의 네트워크 설정. 아래 내용은 virtual Box 기본 IP 기준임. 포트 22는 ssh.
      - 호스트 IP: 192.168.56.1
      - 호스트 포트: 22
      - 게스트 IP: 10.0.2.15
      - 게스트 포트: 22
    * ssh [사용자명]@192.168.56.1
    * ssh [사용자명]@192.168.56.1 -p 2222: ssh port 번호를 2222로 정의한 경우

    
## ssh 접속 with keyfile

- 설정 파일: /etc/ssh/sshd_config, /etc/ssh/ssh_config
- 설정: 기본은 no로 되어 있음.
```
#EC2 users keys for remote access
PasswordAuthentication yes
```
1. 클라이언트 PC에서 key 생성 및 확인
  * ssh-keygen
    - 저장 위치 꼭 확인하기
    - ssh-keygen -t rsa -b 2048: 옵션으로 알고리즘, 키 길이 등을 정할 수 있음.
  * ls -l .ssh
    - id_rsa 이름으로 2개 생성되며, .pub 확장자 파일이 공개 key이다.

2. 클라이언트에서 서버로 Key 복사
  * [참조링크](https://light-tree.tistory.com/232)
  * scp는 윈도우, 리눅스에 상관없이 복사 가능함.
  * ssh-copy-id는 리눅스에서 사용가능한 원격 복사이다.
  * 클라이언트가 윈도우인 경우
    * type으로 한줄로 할 수도 있고, scp로 복사한 뒤에 ssh로 접속해서 복사한 파일을 .ssh/authorized_keys 파일에 추가하기
    * type C:\D_Drive\linux/.ssh/id_rsa.pub | ssh kali@192.168.56.1 "cat >> .ssh/authorized_keys"
    * scp -P 22 C:\D_Drive\linux/.ssh/id_rsa.pub kali@192.168.56.1:.
      * cat id_rsa.pub >> .ssh/authorized_keys

  * 클라이언트가 Linux인 경우
    * ssh-copy-id -i $HOME/.ssh/id_rsa.pub kali@192.168.56.1
    * cat .ssh/id_rsa.pub | ssh kali@192.168.56.1 "cat >> .ssh/authorized_keys"

3. 접속히기
  * private 키 위치가 필요한 경우, -i 옵션을 사용한다.
  * 윈도우
    - ssh -i C:\D_Drive\linux/.ssh/id_rsa kali@192.168.56.1
    - ssh -i C:\D_Drive\linux/.ssh/id_rsa -p 2222 kali@192.168.56.1
  * 리눅스: 다중키를 사용하는 경우, Private 키 위치가 필요함.
    - ssh kali@192.168.56.1
    - ssh -i .ssh/id_rsa -p 2222 kali@192.168.56.1


## 프로세스 관리
* ps: 2개(Bash 명령 인터프리터, ps 명령어. Root인 경우, su로 3개까지)만 보이며, 실제 실행되고 있는 프로세스 확인은 아래 명령어로 확인. 
* ps -ef | grep init
* ps -e
* pstree -p
* /sbin/init vs /lib/systemd/systemd
* 프로그램 중에 "d"로 끝나는 도구들은 백그라운드에서 실행되는 시스템 프로세스인 Daemon을 나타낸다.


