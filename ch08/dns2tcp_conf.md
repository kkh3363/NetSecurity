
### /etc/dns2tcpd_config
```
listen = 0.0.0.0
port = 53
user = nobody
chroot = /home/nobody
pid_file = /var/run/dns2tcp.pid
domain = dns2tcp.wishfree.com)
key = secret_key
resources = ssh:127.0.0.1:22
```
