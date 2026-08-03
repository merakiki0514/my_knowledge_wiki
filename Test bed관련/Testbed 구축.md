# 1. EU Cyber-MAR
## 전체 아키텍처 (3계층(Technologies - People - Procedure))
### 핵심 구성요소
1. Orchestrator : 전체 시스템의 메인 컨트롤러 / 모든 컴포넌트를 동기화하고 임의의 토폴로지와 공격 시나리오를 구동하며 공통 API를 제공
2. DIATEAM CyberRange : 가상 환경 생성/관리, 실제 IT/OT 장비와 연동, 모든 VM에 대한 뷰 및 상호작용 제공
3. VTT Tools : 오픈소스 네트워크 모니터링 도구 집합, LMS(Learning Management System), 보안 경고 수집/대시보드 제공, 기술 전문가용 및 고위급 관리자용 모듈 2개
4. SIEM/ADS : 보안 이벤트 상관관계 분석, 실시간 네트워크 흐름 기반 행동 분석, 시스템 구성 업데이트 지점 식별
5. MISP(Malware Information Sharing Platform) : 실제 기술/운영 데이터 기반 공격 시나리오 기록 및 재생, CERT/CSIRT 간 정보공유 연동
6. MaCRA Framework : 사이버 위험 노출 평가 프레임 워크
7. Econometic Model : 공격 시나리오의 경제적 영향(다운타임, 복구 시간 등 ) 평가
8. Recommendation Engine : inflict risk + 경제모델 비실시간 평가, 포트 토폴로지/트래픽/MISP 데이터/시나리오 입력
9. Ship Simulator : 선박 시뮬레이터(Plymouth 대학) 연동, 항해/제어 시스템 공격 시나리오 수행
## 세부 구성
![[Screenshot From 2026-08-03 13-48-50.png]]
- Multi-level computer emulation and simulation environment
	- physical equipment (router, probe, industrial PLC ..)
- Network topologies
	- OSI (1 to 3)
		- the network components which they are connected to
		- IP addresses
		- Bandwidth
	- components
		- routing process ranging from no routing, direct routing up to dynamic routing with BGP, OSPF, etc..
		- diffusion mode unicast, multicast and even broadcast data flow rate limiting
		- open services like SSH protocol, log managemnt
- Security technologies
	- set of Defensice(firewalls, IPS/IDS, SIEM, ..)
	- set of offensive(NMAP, Kali Linux..)
	=> security technologies and tools
- Network traffic generator
	- inject legitimate or illegitimate traffic create the noise
## Cyber range tools
### Virualization/Emulation technology
- Cloud -> LAAS Cloud infrastructure / Openstack
- Critical infrastructure -> EMULAB / Hyper-V, NetEM
- Hybrid network -> Virtualbox / VM ware ESXI / KVM/QWMU
- IOT -> Openflow switches / Vmware Vsphere / Qemu system
- SCADA -> Mininte / proxmox VE / Core emulator
- Network -> Xen-VM / Open V-Switch / XORP Router / Open VZ
### Simulation technology
- Critical infra -> Qualnet / SCADASim / Digsilent Power fatory
- SCADA -> Matlab / Analog I/O / Modbus I/O
- Network -> ModelNet / NS2, NS3 / Network Simulator
- Autonomous system -> Qualnet / Transas
### Monitoring Technology
- Cloud -> Netflow / IPFIX 
- Critical Infra -> Zabbix / prometheus / Wireshark
- Hybrid network -> Nagios / OSSEC / Tcpdump
- IOT -> ADB / Opendaylight controller / Wireshark
- SCADA -> SNORT / BRO IDS / Can analyzer
- Network -> Testbed@twisc Monotor / Traceroute / Suricata
### Traffic generation
- Cloud -> Low Orbit lon
- Critical Infra -> Modbus / DITG / Open Flow
- Hybrid network -> ISEAGE / Traffic Collector replayer
- IOT -> Printer / Microworks / SNMP
- SCADA -> Traffic fuzzer / MODBUS / DNP3
- Network -> Hydra / Emulab / tfn2k
## Tools (Open-source)
- Firewall :  solutions such as pfsense
- IDS : solutions such as SURICATA
- IPS/IDS : frameworks such as SELKS
- Traffic generator
	- TRex -> Apache / software / can installed im VM
	- BreakinPoint(IXIA) ->can be both hardware and software
# 2. NTNU (Cyber-Physical Systems Security Lab)
- 해사 부분 전용 Cyber Range
- 선박 항해/제어 시스템의 취약점 발굴과 실무자 훈련 수행
### Equipment
#### Maritime
- AIS
- Furune GP 170 (GNSS)
- Garmin NMEA 2000 network starter kit
- Garmin NMEA 2000 network Updater
- Maretron IPG100 (Internet Protocol Gateway) - Connect onboard NMEA 2000 marine network to IP device
# 3. Ploymouth
- 하드웨어 기반 선박 사이버보안 연구 플랫폼
- 실제 선박 브리지에 탐재되는 장비를 재구성(물리적 트윈 형태)
## 주요 구성 장비
- Radar , VDR, ECDIS, AIS, VSAT, GMDSS 등 실제 선박용 항해/통신 장비
- Custom-built 24V Logic Interface, NMEA200/0183 디바이스, Serial-IP 변환기(converter)
- USV/드론 장비, AIS 수신기, NAVTEX, SatCo,
- Cyber Range(DIATEAM, VTT) + Ship Sinulator + Riskocity(위험평가) + Maritime Simulation Lab과 통합된 시스템
## Console RM
- Visualisation of data
- Physical hardware visualisation of attacks
- Pen-testing
- Research Project development
- Development of custom electronics and software
- Teaching/Training
## The Vault
- USVs
- Radar quipment
- Custom Power Distribution
- VDRs and NAVTEX
- AIS receivers
- Custom Cyber-Ship 24V Logic Interface and monitor
- MFDs
- Serial-IP Converters
- NMEA 2000/0183
- Data recovery from ECDIS
- SatCom
- AIS
- Navtex
## 기본 아키텍처
![[Screenshot From 2026-08-03 13-35-34.png]]
### 세부 구성
![[Screenshot From 2026-08-03 13-38-03 1.png]]
#### 각각 요소
- Orchestrator
![[Screenshot From 2026-08-03 13-38-34.png]]
- Diateam CyberRange
![[Screenshot From 2026-08-03 13-39-03.png]]
- VTT tools
![[Screenshot From 2026-08-03 13-39-23.png]]
- Recommendation engine
![[Screenshot From 2026-08-03 13-39-50.png]]
- Econometric Model
![[Screenshot From 2026-08-03 13-40-09.png]]
- SIEN/ADS
![[Screenshot From 2026-08-03 13-40-38.png]]
- MISP
![[Screenshot From 2026-08-03 13-40-57.png]]
- MaCRA
![[Screenshot From 2026-08-03 13-41-17.png]]
# 4. 독일 - eMIR(e-Maritime Integrated Reference Platform)
- 가상(HAGGIS) + 물리(LABSKAUS) 테스트 베드로 구성
- S-100 해양 데이터 표준 기반의 메시지 브로커(RabbitMQ)를 통해 시뮬레이션과 실제 장비를 연동
## 구성 요소
- 가상 테스트베드 HAGGIS : HLA(High Level Architecture) 기반 공동 시뮬레이션
- 물리 테스트베드 LABSKAUS: VTS, 이동형 브리지 시스템, 연구용 자동화 보트, 센서 퓨전 시스템등
	-> 중앙 Exchange Bus를 통해 모든 데이터 공유, 서비스 지향 아키텍처(SOA) 및 Testbed-as-a Service 패러다임 지원