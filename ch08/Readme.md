### packet tracer 명령어

1. 주요 모드 구분 및 프롬프트

- 유저 모드 (>): 장비에 접속했을 때의 기본 모드 (제한적인 조회만 가능)
- 특권 모드 (#): 관리자 모드 (설정 변경, 저장, 확인 가능)
- 전역 설정 모드 ((config)#): 라우터 전체에 영향을 미치는 기본 환경 설정 모드

2. 모드 전환 및 기본 명령어

- 유저 모드 $\rightarrow$ 특권 모드: enable (줄여서 en)
- 특권 모드 $\rightarrow$ 유저 모드: disable
- 특권 모드 $\rightarrow$ 전역 설정 모드: configure terminal (줄여서 conf t)
- 전역 설정 모드 $\rightarrow$ 특권 모드: exit (또는 Ctrl + Z)
- 명령어 도움말: ? (예: ip ? 또는 show ?)
- 오타 방지 설정 (잘못된 명령어 입력 시 도메인 룩업으로 인해 멈추는 현상 방지):text

```
- Router(config)# no ip domain-lookup
코드를 사용할 때는 주의가 필요합니다.
  ```

3. 호스트 이름(장비 이름) 설정

text Router> enable Router# configure terminal Router(config)# hostname R1 R1(config)# 

4. 인터페이스(포트) IP 주소 할당 및 활성화

- text R1(config)# interface gigabitethernet 0/0    # 인터페이스 진입 (장비 모델에 따라 f0/0, g0/0 등 다름)
- R1(config-if)# ip address 192.168.1.1 255.255.255.0
- \# IP 주소와 서브넷 마스크 입력 R1(config-if)# no shutdown
- \# 인터페이스 활성화 (전원 켜기) R1(config-if)# exit 

5. 비밀번호 설정

- 평문(암호화되지 않은) 특권 모드 암호:
  text R1(config)# enable password cisco
- 암호화된 특권 모드 암호 (권장):
  text R1(config)# enable secret cisco   
• 모든 비밀번호 암호화 적용 (설정 파일 내 평문 암호 보호):
  text R1(config)# service password-encryption   
• 콘솔 접속 암호 설정:
  text R1(config)# line con 0 R1(config-line)# password cisco R1(config-line)# login R1(config-line)# exit   

6. 설정 저장 및 초기화

- 설정 저장 (RAM의 running-config를 NVRAM의 startup-config로 복사):
  ```text
R1# copy running-config startup-config
또는 특권모드에서 줄여서:

R1# write
  ```
- 설정 초기화 (저장된 시작 설정 삭제):
  text R1# erase startup-config   
- 장비 재부팅:
  text R1# reload   

7. 상태 확인 명령어 (특권 모드 #에서 입력)

- 현재 적용된 설정 확인: show running-config (줄여서 sh run)
- 라우팅 테이블 확인: show ip route
- 인터페이스 상태 요약 확인: show ip interface brief
