### 설치
```
sudo apt-get update
sudo apt-get install -y xinetd telnetd
```
### 환경설정
```
sudo vi /etc/xinetd.d/telnet
```
- i를 입력해서 명령어 모드
```
service telnet
{
    disable = no
    flags = REUSE
    socket_type = stream
    wait = no
    user = root
    server = /usr/sbin/in.telnetd
    log_on_failure += USERID
}
```
- esc 키로 명령어모드로 이동
- :wq 엔터

### 데몬 실행
```
sudo service xinetd restart
```

