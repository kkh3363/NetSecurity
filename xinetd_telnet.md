### 설치
```
sudo apt-get update
sudo apt-get install -y xinetd telnetd
```
### 환경설정
```
sudo nano /etc/xinetd.d/telnet
```

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

### 데몬 실행
```
sudo service xinetd restart
```

