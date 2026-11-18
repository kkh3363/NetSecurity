
### /etc/dns2tcpd_config
```
listen = 0.0.0.0
port = 53
user = nobody
chroot = /home/nobody
pid_file = /var/run/dns2tcp.pid
domain = dns2tcp.wishfree.com
key = secret_key
resources = ssh:127.0.0.1:22
```

- 특정 포트 상태 확인
  ```
   netstat -anp | grep :53
  ```
- 특정 포트를 사용 중인 프로세스와 PID(프로세스 ID)를 한 번에 조회
  ```
  sudo lsof -i :포트번호
  ```
