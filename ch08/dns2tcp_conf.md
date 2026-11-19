
### 서버에서 ./dns2tcpd_config
```
listen = 0.0.0.0
port = 53
user = nobody
chroot = /home/nobody
pid_file = /var/run/dns2tcp.pid
domain = dns2tcp.wishfree.com
key = secretkey
resources = ssh:127.0.0.1:22
```
```
(sudo) dns2tcpd -d 3 -f ./dns2tcpd_config
```

### 클라이언트 설정 ./dns2tcpc_config
```
domain = dns2tcp.wishfree.com
resource = ssh
local_port = 2222
key = secretkey
debug_level = 3
server = 192.168.138.132
```
- vi /etc/hosts
  ```
  192.168.133.130  dns2tcp.wishfree.com
```
- sudo dns2tcpc -f ./dns2tcp_config
```

## 문제 해결
- 특정 포트 상태 확인
  ```
   netstat -anp | grep :53
  ```
- 특정 포트를 사용 중인 프로세스와 PID(프로세스 ID)를 한 번에 조회
  ```
  sudo lsof -i :포트번호
  ```
- 1단계: 53번 포트 점유 프로세스 확인
  ```
  sudo ss -lntup '( sport = :53 )'
  ```
- 2단계: systemd-resolved의 53번 포트 점유 해제 (가장 흔한 경우)
  - 관리자 권한으로 /etc/systemd/resolved.conf 파일을 엽니다
  ```
  [Resolve]
  DNS=8.8.8.8
  DNSStubListener=no
  ```
  ```
  sudo ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
  ```
  - 서비스 재시작. 변경 사항을 적용하기 위해 서비스를 재시작합니다
  ```
  sudo systemctl restart systemd-resolved
  ```
  
