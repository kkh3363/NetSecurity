
1. 소스 코드 다운로드
https://github.com/kkh3363/NetSecurity/blob/main/ch09/shijack.gz

2. 압축풀기
```
tar xvzf shijack.gz
```

### tcpdump
```
sudo tcpdump -i eth0 -A -nn port 23
```
 - -i eth0: 패킷을 캡처할 네트워크 인터페이스 지정 (tcpdump -D로 목록 확인 가능)
 - -A: 패킷 페이로드(실제 전송 데이터)를 ASCII 문자로 출력
 - -nn: IP 주소와 포트 번호를 호스트 이름·서비스 이름으로 변환하지 않고 숫자로 표시
 - port 23: 텔넷 기본 포트(23번) 트래픽만 필터링
