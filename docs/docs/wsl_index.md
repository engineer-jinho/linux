# introductin
[wsl tutorial (official)](https://learn.microsoft.com/en-us/windows/wsl/) 자료를 참조하여 만듬

# 설치
버전 확인 --> 설치 --> 재부팅 --> 사용자 설정 --> 설치확인

- 버전 확인  
"Windows key + r" --> winver  
[Microsoft official information](https://learn.microsoft.com/en-us/windows/wsl/install), windows 10( version 2004, build 19041) 

- 설치  
명령어 프롬프트를 관리자 권한으로 실행

```shell
wsl.exe --install
```

- 사용자 설정
재부팅하면 "username, pw 입력"하도록 화면 뜸

- update and upgrade packages
사용자 설정하고나서 해당 화면에서 packages 업데이트하기
```shell
sudo apt update && sudo apt upgrade
```

- 설치확인
명령어 프롬프트에서 확인  
기본 배포판: verbos로 확인했을 때, "*"가 표기

```shell
wsl --list
wsl --list --running
wsl --list --verbose
```

# wsl 명령어

## wsl 배포판 변경

wsl --set-version "배포판 이름" "버전"으로 변경 가능

```shell
wsl --set-version Ubuntu 2
```

## 프롬프트에서 linux 명령어 실행

프롬프트에서 linux 명령어를 실행할 수 있음.  
'-d'를 이용하면 기본 배포판 이외에도 가능.  
root로 변경할 일이 가장 많을 듯.  

=== "기본 배포판"
    ```shell
    wsl ls ~
    wsl cat /etc/issue
    ```
=== "특정 배포판"
    ```shell
    wsl -d Ubuntu-20.04 ls ~
    wsl cat /etc/issue
    ```
=== "현재 사용자 확인"
    ```shell
    wsl whoami
    ```
=== "사용자로 변경"
    ```shell
    wsl -u root whoami
    ```
=== "특정 배포판 정지"
    ```shell
    wsl --terminate Ubuntu-20.04
    ```
=== "모든 배포판 종료"
    ```shell
    wsl --shutdown
    ```

# windows terminal

- Windows Store --> Windows Terminal 설치

## 단축키
- 새 인스턴스: Ctrl + shift + t
- 프로필 선택: Ctrl + shift + space, Ctrl + shift + 1...n
- Tab 변환: Ctrl + TAB, Ctrl + shift + TAB, Ctrl + Alt + 1...n
- Tab 닫기: Ctrl + shift + w
- 설정: Ctrl + ,


## 윈도우 터미널 설정
- 설정(Ctrl + ,) --> settings.json 파일 열기
- setting.json으로 한번에 정리할 수도 있지만 화면에서 하나씩 선택해도 됨.
- 화면에서 하나씩 변경하고, settings.json 파일을 저장해서 관리하기.

 

