# Nmap(Network Mapper)

---

### **1. 소개**

- Nmap은 네트워크 스캔 툴이다. 주로 네트워크 호스트 및 서비스 식별하고 취약점 탐지를 위해 사용되며, 열려있는 포트(서비스)·버전 등 수집 가능하다.
- nmap은 모의해킹 시 시작단계에서 많이 사용된다(실제 서비스 대상으로 사전 허가 없이 사용하는 것은 불법).

### **2. 설치**

- kali linux에는 nmap이 기본적으로 깔려 있어서 설치는 불필요하다.
- 그 외 OS에서는 nmap 공식 사이트 접속하여 OS, 버전에 맞게 설치하면 된다.

### 3. **주요 기능**

- **호스트 탐색**: 네트워크 상에서 활성화된 시스템 및 기기 식별 [-sn]
- **포트 스캔**: 대상 시스템에서 열려 있는 TCP 및 UDP 포트 확인 [-sS, -sT, -sU]
- **서비스 및 버전 탐지**: 포트별로 구동 중인 애플리케이션 이름과 상세 버전 파악 [-sV]
- **운영체제(OS) 추정**: 원격 호스트의 OS 종류 및 버전 판별 [-O]
- **취약점 점검**: NSE(Nmap Scripting Engine)를 활용한 보안 취약점 진단

### **4. 사용법**

```bash
nmap [target IP]
```

- 타겟 IP에 대한 네트워크 스캔이 실행된다. 해당 결과로 타겟에서 어떤 포트가 열려있는지 확인할 수 있다.
- filtered 상태: 방화벽 등과 같은 장비로 패킷 통신 차단하고 있음을 나타낸다. 다만, 이것만으로는 해당 포트가 실제 사용 중인지는 알 수 없다.

### **5. 주로 사용하는 옵션**

- p [포트 번호]: 특정 포트 범위에 대한 스캔 가능

```bash
nmap -p [port number] target IP]

# 예시
nmap -p 22,80,10000 [target IP]
```

- oA 파일명: 다양한 형태로 출력 가능(텍스트 파일로만 받으려면 -oN 사용)

```bash
nmap -oA result.txt [target IP]
```

- sV: 서비스 및 버전에 대한 자세한 정보 확인 가능

```bash
nmap -sV [target IP]
```

- script [스크립트 이름]: NSE(Nmap Scripting Engine) 스크립트를 실행하여 서비스에 대한 취약점 탐지 가능

```bash
nmap --scrip http-enum,http-xssed [target IP]
```
https://nmap.org/docs.html

https://www.stationx.net/nmap-cheat-sheet/

https://linuxize.com/cheatsheet/nmap/

---
<img width="1091" height="442" alt="캡처" src="https://github.com/user-attachments/assets/5b6a71d4-cb99-4a24-9504-60e5f36b1f00" />

