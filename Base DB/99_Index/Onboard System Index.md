---
type: index
tags:
  - index
  - onboard-system
---

# Onboard System Index

`Database/선내 시스템 목록 110종.csv`에 수록된 **선내 시스템 110종**의 탐색용 인덱스.

- **원본**: `Database/선내 시스템 목록 110종.csv` (컬럼: 시스템 / 기능 / 주요 data)
- **성격**: 실제 선박의 시스템 목록. [SOURCE]
- **그룹 분류**: 검색 편의를 위해 이 문서에서 부여한 것으로, **원본 CSV에는 그룹 컬럼이 없다.** [INFERENCE]
- **`#` 번호**: CSV의 데이터 행 순번(헤더 제외). 원본 대조용.
- UR E22 시스템 카테고리(Cat I/II/III)는 선박별로 달라지므로(UR E22 §3.3) 이 인덱스에서는 부여하지 않는다.

## 빠른 찾기

| 찾는 것 | 그룹 |
| --- | --- |
| 주기관, 보일러, 조타, 연료유 계통 | [[#A. 추진·기관 (Propulsion & Machinery)]] |
| 발전기, 비상발전기, 육상전원, ESS | [[#B. 전력 (Electrical Power)]] |
| SCR, Scrubber, EGR, ODME, 소각기, 방오 | [[#C. 배기·환경 (Emission & Environmental)]] |
| 카고펌프, 탱크 레벨, IGG, 적하계산기 | [[#D. 화물·탱크 (Cargo & Tank)]] |
| 밸러스트 처리 | [[#E. 밸러스트 (Ballast)]] |
| LNG 벙커링, BOG, 기화기, 질소 | [[#F. LNG·연료가스 (LNG / Fuel Gas)]] |
| 화재탐지, 가스탐지, CO2, PAGA | [[#G. 안전 (Safety Systems)]] |
| Radar, ECDIS, AIS, VDR, Gyro, Autopilot | [[#H. 항해 (Navigation / Bridge)]] |
| Inmarsat, MF/HF, VHF, Navtex, Weather Fax | [[#I. 무선통신 (Radio Communication)]] |
| 선내전화, Master Clock, 공청 | [[#J. 선내통신·기타 (Internal Comm & Misc)]] |
| AMS, IAS | [[#K. 자동화 (Automation)]] |
| HS4, K-IMS, ISS, HiNAS, NAVBOX, 성능 모니터링 | [[#L. 스마트십·성능 (Smart Ship & Performance)]] |

## 규정과의 접점

- 이 목록은 UR E26 §4.1.1 **Vessel Asset Inventory**의 기초 자료로 쓸 수 있다. 템플릿 컬럼은 IACS Rec.190 §6.1 참조 → [[Regulation Locator#4. 자산 목록 (Asset Inventory)]]
- IACS Rec.171 §4 Table 1 "Systems reference table"에 유사한 시스템 분류(Machinery / Ballast·Bilge / Cargo Management / Radio Communication / Bridge / Safety)가 있다. 본 인덱스의 그룹과 **직접 대응하지는 않는다.** [확인 필요]
- CSV에는 제조사, 모델, 프로토콜, 네트워크 존, IP 정보가 **없다.** Rec.190 §6.1 기준 컬럼 F/G/M/Q/R/S에 해당하는 정보 부재.

---

## 시스템 목록

### A. 추진·기관 (Propulsion & Machinery)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 1 | **BMS** | 선교(Bridge)에서 주기관(Main Engine)을 직접 원격 제어하고 상태를 모니터링하는 시스템입니다. | 주기관 RPM 명령값/현재값, Engine Telegraph 상태 신호, 제어권(Bridge/ECR/Local) 전환 신호, Shut-down/Slow-down 경보 상태. |
| 5 | **F.O Supply Control System** | 주기관 및 발전기 엔진에 연료유(Fuel Oil)를 중단 없이 안정적인 압력과 온도로 공급하는 장치입니다. | 연료유 공급 압력/온도, 연료유 필터 차압(Differential Pressure), 공급 펌프 운전/정지 상태, 점도(Viscosity) 계측 데이터. |
| 6 | **Aux. Boiler** | 선내 가열용, 화물창 가습용 및 펌프 구동용 스팀(Steam)을 생산하기 위해 연료를 연소시키는 보일러입니다. | 보일러 드럼 수위(Water Level), 스팀 압력/온도, 버너(Burner) 화염 감지 신호, 연료 소비량. |
| 7 | **Composite Boiler** | 항해 중에는 주기관 배기가스의 폐열을 이용하고, 정박 중에는 버너를 태워 스팀을 생산하는 다목적 보일러입니다. | 배기가스 입출구 온도, 댐퍼(Damper) 개도율, 스팀 압력, 덤프 밸브(Dump Valve) 제어 신호. |
| 8 | **E/R TEMP. Control Valve System** | 기관실(Engine Room) 내부 주요 구역 및 구동 장비들의 국부 온도를 집중 모니터링합니다. | 구역별 대기 온도, 교정용 센서(Pt100/K-Type) 측정값, 고온 경보(High Temp Alarm) 디지털 신호. |
| 20 | **Steering Control System** | 선교의 조타륜(Wheel) 조종 명령에 따라 조타기(Steering Gear)의 유압 펌프를 구동하여 타(Rudder)의 각도를 제어합니다. | 타각 명령값(Order Angle), 실제 타각 피드백(Actual Rudder Angle), 유압 펌프 운전 상태 및 유온/유압 경보. |
| 61 | **Viscosity Control & Flowmeter** | 디젤 엔진 연소실 진입 전 연료유의 온도를 조절해 적정 점도를 유지시키고, 유량계로 소모량을 계측합니다. | 연료유 점도(Viscosity, cSt) 계측값, 연료유 제어 밸브 PID 신호, 유량계 누적 펄스 수(연료 소비량 데이터). |
| 63 | **Temp. & Press Contorl Valve System** | 청수 냉각 계통, 윤활유 계통 등에 설치되어 유체의 온도와 압력을 설정치로 자동 조절하는 밸브 제어 계통입니다. | 계통 실제 온도/압력 측정값, 목표 설정값(Set-point), 컨트롤러 출력 신호(MV, 4-20mA). |
| 86 | **ME TOP Bracing Control System** | 주기관의 피스톤 왕복 운동으로 발생하는 선체 상부의 횡진동을 감쇠시키기 위해 장착된 유압 구조물의 압력을 제어합니다. | 브레이싱 유압 실린더 압력 값, 주기관 RPM 연동 비례 제어 신호. |
| 88 | **Exhaust Gas Econimizer Control System** | 주기관 배기가스 덕트 내에 설치된 이코노마이저 패널의 스팀 생산량 및 급수 유량을 제어합니다. | 급수 제어 밸브 개도율, 스팀 압력 설정 제어값, 순환 펌프 기동 상태. |
| 89 | **HFO/LO Purifier Control System** | 연료유(HFO) 및 윤활유(LO) 청정기(Purifier)의 원심분리 운전 회전수를 제어하고, 주기적인 찌꺼기 배출(Sludge Discharge)을 제어합니다. | 청정기 고속 회전수, 오일 공급 온도, 슬러지 배출 타이머 주기 설정값, 수분 감지(Water Detection) 알람. |
| 93 | **Fuel oil change-over system** | 배출규제해역(ECA) 진입 시 엔진 연료를 고유황유(HFO)에서 저유황유(LSMGO)로 온도 충격 없이 완만하게 자동 전환 제어합니다. | 연료 라인 점진적 온도 변화율(°C/min), 3-Way 전환 밸브 제어 신호, 연료유 혼합 탱크 레벨. |
| 99 | **M/E Bearing Wear Monitoring System** | 주기관 내부 주요 크랭크핀 베어링, 크로스헤드 베어링 등의 미세 마모 상태를 거리 센서로 실시간 감지하여 대형 사고를 예방합니다. | 베어링별 크레디트 마모량(mm단위 미세 변위), 센서 근접도 신호, 베어링 비정상 마모 경보. |
| 100 | **Control Air Dryer** | 선내 정밀 기기 및 자동 제어 공압 밸브에 공급되는 압축공기의 수분을 응축·제거하여 고장을 예방하는 장치입니다. | 출구 공기 노점 온도(Dew Point, °C), 드라이어 냉매 압력, 배수(Drain) 밸브 자동 주기 작동 신호. |
| 108 | **Heat Tracing System** | 극지방 운항 시 결빙으로 인한 파이프 및 센서 파손을 막기 위해 선외 노출 배관에 감긴 전기 열선의 전원 및 온도를 자동 제어합니다. | 배관 표면 온도 측정값, 열선 그룹별 소모 전류량, 누전(Earth Fault) 감지 경보. |
| 109 | **G/E Aiar Waste Gate Valve Control System** | 발전기 엔진의 고부하/저부하 조건에 맞춰 터보차저 과급 공기의 일부를 바이패스하여 엔진 연소 효율을 최적화하는 밸브 제어 장치입니다. | 웨이스트 게이트 밸브 제어 개도율, 소기(Scavenge Air) 압력/온도 피드백 신호. |

### B. 전력 (Electrical Power)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 3 | **Generator Engine** | 선내 필요한 전력을 생산하기 위해 발전기(Generator)를 구동하는 디젤 또는 가스 엔진입니다. | 엔진 RPM, 윤활유(LO)/냉각수(JW) 온도 및 압력, 실린더별 배기가스 온도, 시동/정지 상태 신호. |
| 19 | **Emergency Generator Engine** | 주전원 상실(Blackout) 시 선박의 안전에 필수적인 장비들에 전력을 즉시 공급하는 비상 발전기용 엔진입니다. | 비상 발전기 전압/주파수, 버스바(Bus-bar) 연결 상태 신호, 시동 배터리 전압, 자동 시동(Auto-start) 준비 상태. |
| 103 | **AMP Reel Control Panel** | 선박 정박 중 선내 전력 공급을 위해 부두의 고압 육상 전원(Alternative Maritime Power) 케이블 릴 모터를 구동 및 제어합니다. | 고압 케이블 릴 모터 토크 상태, 드럼 리미트 스위치 접점, AMP 차단기 인터록 제어 신호. |
| 105 | **ESS Control panel** | 선내 부하 변동에 대응하고 연료를 절감하기 위해 대용량 배터리 시스템(Energy Storage System)의 충방전 및 전력 품질을 제어합니다. | 배터리 충전 상태(SOC, %), 배터리 건강 상태(SOH), 충방전 전류/전압(kW), ESS 셀 최고 온도 및 BMS 알람. |

### C. 배기·환경 (Emission & Environmental)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 2 | **M/E HP SCR Control System** | 주기관(Main Engine)의 고압 질소산화물 저감장치(SCR)를 제어하여 배기가스 속 유해 물질을 줄입니다. | SCR 입출구 배기가스 온도 및 압력, NOx(질소산화물) 농도 계측값, 요소수(Urea) 분사량, 바이패스 밸브 개도율. |
| 4 | **G/E SCR Control System** | 발전기 엔진(Generator Engine)에서 배출되는 배기가스의 질소산화물을 저감하는 SCR 장치를 제어합니다. | 발전기 배기가스 온도, Urea 유량 및 공급 압력, SCR 촉매 전후단 차압, 시스템 운전 모드 상태. |
| 16 | **Vapour emission control system** | 화물 적재 시 탱크 상부로 배출되는 유해 유증기(Vapour)의 압력과 산소 농도를 제어하며 육상으로 안전하게 회수합니다. | Vapour 라인 압력, Vapour 산소(O2) 농도 계측값, 탈착 밸브 상태, 선박-육상 간 인터록 상태 신호. |
| 17 | **Oil Discharge Monitoring Equipment(ODME)** | 선외로 배출되는 화물창 세정수 및 빌지의 유분 농도를 감시하여 법적 기준(15ppm 또는 30L/nm) 초과 시 배출을 차단합니다. | 배출수 내 유분 농도(ppm), 배출 유량, 선박의 현재 항해 속력, 선외 배출 밸브(Overboard Valve) 개폐 상태 및 인터록 기록. |
| 62 | **ICCP System** | 외부 전원 공급식 선체 부식 방지 장치(Impressed Current Cathodic Protection)로 선체 외판에 최적 전류를 흘려 부식을 차단합니다. | 기준 전극(Reference Electrode) 전위차(mV), 출력 전류(Ampere) 및 전압(Volt) 데이터. |
| 65 | **SOX SCRUBBER system** | 엔진 배기가스에 해수 또는 알칼리 화학액을 분사하여 황산화물(SOx) 유해 물질을 제거하는 탈황 시스템입니다. | 배기가스 pH 지수, 세정수 흡입/배출 유량, 배 배출 가스 내 SO2/CO2 비율, 워시워터(Washwater) 탁도(Turbidity). |
| 69 | **INCINERATOR** | 선내 운항 중 발생하는 폐유(Sludge), 쓰레기 등을 국제 해양오염방지협약(MARPOL) 기준에 맞게 고온 소각합니다. | 소각로 연소실 내부 온도, 슬러지 버너 오일 공급 유량, 배기가스 온도 및 팬(Fan) 가동 상태. |
| 85 | **ME Exhaust Gas Recirculation System** | 주기관 배기가스 일부를 처리 후 다시 실린더 흡기로 공급해 연소 온도를 낮춤으로써 티어3(Tier III) NOx 규제를 만족시키는 시스템입니다. | EGR 수조 수질(pH/탁도), 가스 재순환 송풍기(Blower) 속도, EGR 밸브 위치 제어 신호. |
| 87 | **GE Selective Catalytic Reduction System** | 발전기 엔진(G/E) 배기가스 라인에 설치되어 촉매 환원 반응을 통해 질소산화물을 친환경적으로 분해 제어합니다. | 발전기 SCR 셀 촉매 온도, 요소수 도징(Dosing) 펌프 제어값, 차압 알람 신호. |
| 102 | **MGPS** | 해수 흡입구(Sea Chest) 내부에 구리/알루미늄 이온을 방출하여 해수 배관 내부에 조개, 해초류가 흡착·성장하는 것을 예방합니다. | MGPS 전원 공급 장치 양극(Anode) 인가 전류/전압 값, 양극 소모량(Life-time) 추정 데이터. |
| 104 | **Olly Bilge Separator** | 선저 유수분리기로 기관실 바닥에 고인 기름 섞인 물(Bilge)을 필터링하여 해양 규정인 15ppm 이하로만 선외 배출하도록 제어합니다. | 배출 전 최종 유분 농도(ppm값 지시), 선외 배출 전환 밸브 제어 접점, 유수분리기 펌프 압력. |

### D. 화물·탱크 (Cargo & Tank)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 9 | **Cargo Pump control system** | 액체 화물(원유, LNG, 화학제품 등)을 하역하기 위해 화물 펌프의 회전수와 출력을 원격 제어합니다. | 펌프 RPM 명령 및 피드백, 펌프 흡입/토출 압력, 베어링 및 케이싱 온도, 펌프 Trip 경보 신호. |
| 10 | **Valve Remote Control System** | 화물 배관 및 평형수 배관 상에 위치한 수많은 밸브들을 원격(제어실)에서 유압 또는 공압으로 개폐합니다. | 각 밸브의 Open/Close 상태 피드백 신호, 솔레노이드 밸브 구동 제어 신호, 유압 유니트(Hydraulic Unit) 압력. |
| 11 | **Cargo Tank level monitoring system** | 화물창(Cargo Tank) 내부의 화물 높이(Level)를 레이더나 압력 센서로 정밀 계측합니다. | 탱크별 화물 레벨(Ullage/Innago), 화물 온도(상/중/하층), 탱크 내부 불활성 가스 압력(Vapor Pressure). |
| 12 | **Tank High & Overfill Alarm** | 화물 선적 중 탱크 수위가 95%(High) 및 98%(Overfill)에 도달하면 독립된 센서로 감지하여 강한 경보를 울립니다. | 95% High Alarm 접점 신호, 98% Overfill Alarm 접점 신호, 알람 루프 자가진단(Fail-safe) 상태. |
| 13 | **Tank Level & Draft Gauge System** | 선내 평형수 탱크, 연료유 탱크 등의 수위와 선박 전체의 흘수(Draft, 배가 물에 잠기는 깊이)를 측정합니다. | 각 탱크의 잔량(Volume/Weight), 선수/선미/좌현/우현 흘수 센서 계측값, 선박의 트림(Trim) 및 힐(Heel) 계산 데이터. |
| 22 | **Inert Gas Generator System** | 연료 연소를 통해 산소 농도 5% 이하의 불활성 가스(Inert Gas)를 대량 생산하여 유조선 화물창에 주입합니다. | 생산 가스의 산소(O2) 농도, 이너트 가스 공급 압력 및 온도, 스크러버 냉각수 유량 상태. |
| 24 | **Ship shore Link ESDS** | LNG/LPG선 등에서 비상상황 발생 시 선박과 육상 터미널의 화물 이송 펌프 및 밸브를 동시에 차단(Emergency Shut Down)합니다. | ESD 활성화 신호(Trip 신호), 링크 통신 상태(광케이블/전기/공압 핀 방식 링크), 비상 정지 원인(Cause) 데이터. |
| 26 | **Loading Computer** | 화물 및 평형수 배치에 따른 선체의 굽힘 모멘트(Bending Moment), 전단력(Shearing Force), 복원성(Stability)을 계산합니다. | 선체 응력(Stress) 계산 결과값, GM(복원성 지표) 값, 탱크별 실시간 수위 데이터 수신, 복원성 만족/만족 불가 알림. |
| 60 | **RCMS(Reefeer Container Monitoring System)** | 선박에 적재된 다수의 냉동 컨테이너(Reefer Container) 전원 소켓과 연동하여 개별 온도를 원격 집중 모니터링합니다. | 컨테이너별 현재 공급 온도(Supply Temp), 리턴 온도(Return Temp), 압축기 경보 상태 코드. |
| 91 | **COPT Remote Control System** | 카고 오일 펌프 구동용 스팀 터빈(Cargo Oil Pump Turbine)의 회전수와 스팀 공급 가버너 밸브를 원격 제어실에서 조종합니다. | 터빈 가버너 밸브 제어 신호, 터빈 베어링 진동 및 온도 데이터, 비상 트립(Emergency Trip) 접점 신호. |
| 92 | **COPT Vacuum condenser Monitoring System** | COPT 스팀 터빈 구동 후 배출되는 배기 스팀을 효율적으로 응축시키기 위한 진공 응축기의 진공도와 냉각 계통을 감시합니다. | 응축기 내부 진공도(mmHg / bar), 냉각 해수 입출구 온도, 응축수 배출 펌프 레벨 제어 신호. |
| 98 | **CASCADE TK Level control System** | 보일러 응축수 및 각종 가열 라인 리턴수가 모이는 캐스케이드 탱크의 수위를 일정하게 유지하기 위해 급수 밸브를 제어합니다. | 캐스케이드 탱크 수위, 리턴수 유분 오염 감지 경보 신호, 메이크업 보충수 밸브 통제 신호. |

### E. 밸러스트 (Ballast)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 15 | **BWTS** | 선박 평형수 처리장치(Ballast Water Treatment System)로, 평형수 내 해양 미생물을 필터나 UV, 전기분해로 살균합니다. | 평형수 유량(Flow Rate), UV 강도(Intensity) 또는 TRO(잔류산화물) 농도, 필터 전후단 차압, 전력 소비량. |

### F. LNG·연료가스 (LNG / Fuel Gas)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 59 | **LFFS** | 저인화점 연료 공급 시스템(Low Flashpoint Fuel Supply system)으로, 친환경 LNG나 메탄올 연료를 엔진 요구 조건에 맞게 공급합니다. | 연료 가스 공급 압력 및 온도, 마스터 가스 밸브(GVU) 상태, 이중 배관 불활성 가스 퍼지 압력. |
| 71 | **LNG Bunkering System** | LNG 연료 추진선이 벙커링선이나 육상 기지로부터 LNG 연료를 안전하게 수급받는 제어 시스템입니다. | 벙커링 라인 매니폴드 압력 및 온도, 긴급 분리 장치(ERS) 작동 상태 신호, 가스 누출 센서 상태. |
| 72 | **Vaporizer System** | 액체 상태의 LNG를 강제 기화시켜 엔진이나 보일러에서 연료 가스로 사용할 수 있도록 가열·기화시키는 장치입니다. | LNG 출구 가스 온도, 열매체(Glycol Water) 입출구 온도 및 유량, 기화기 전후단 가압 상태. |
| 73 | **Fuel Gas System** | 기화되거나 압축된 LNG 연료 가스를 엔진(Main/Aux Engine)이 요구하는 압력, 온도, 유량에 맞춰 가스밸브 유닛으로 공급합니다. | 엔진 진입 연료 가스 압력 제어값, 연료 가스 공급 온도 제어값, 환기 팬 가동 상태. |
| 74 | **Bog Compressor system** | LNG 탱크 내부에서 자연 발생하는 증발가스(BOG, Boil-Off Gas)를 엔진 연료로 사용하거나 재액화하기 위해 고압으로 압축합니다. | 컴프레서 흡입/토출 압력, 다단 압축기(Multi-stage) 단별 온도, 윤활유 압력, 모터 전류량. |
| 75 | **Glycol Water System** | LNG 기화기 등의 열원으로 사용되는 글라이콜-물 혼합액을 순환시키고 가열 및 냉각을 제어하는 루프 시스템입니다. | 글라이콜 펌프 운전 상태, 혼합액 온도/압력, 가열 스팀 밸브 제어 개도율. |
| 76 | **Nitrogen System** | 고순도 질소(N2)를 생산하여 가스관 퍼지(Purge), 화물창 단열 구역(Interbarrier Space) 채움 등 방폭 환경을 조성합니다. | 생산 질소 가스의 순도(Purity, %), 질소 저장 탱크 압력, 공급 라인 유량. |
| 77 | **custody transfer System** | LNG 화물의 하역 및 선적 시, 화물의 정밀 레벨, 온도, 압력을 다중 정밀 센서로 측정해 상거래용 물량을 최종 산출하는 시스템입니다. | 고정밀 탱크 레벨 측정치(밀리미터 단위), 화물의 액체 밀도 및 기체 상 계산값, 최종 보정 물량 리포트. |
| 78 | **Gas flow metering system** | 선내에서 소비되거나 이송되는 천연가스의 유량을 질량 유량계(Coriolis Meter) 등을 통해 오차 없이 정밀하게 계측합니다. | 가스 질량 유량(Mass Flow Rate, kg/h), 가스 밀도, 가스 누적 소비량(Totalizer). |
| 79 | **LNG Transfer System** | 선내에 위치한 여러 개의 LNG 화물 탱크 간에 또는 화물 탱크에서 연료 탱크로 액체 LNG를 이송하는 시스템입니다. | 이송 펌프 운전 전류, 이송 라인 예냉(Pre-cooling) 온도 상태, 라인 밸브 연동 상태. |
| 80 | **N2 Generator Control System** | 공기 압축기와 멤브레인 필터를 활용해 질소를 추출하는 질소 생성 장치의 운전 루틴을 자동 제어합니다. | 공기 압축기 구동 상태, 산소 배출 밸브 제어 신호, 생성 질소 압력 값. |
| 81 | **Bog Compressor Control System** | BOG 압축기의 서지(Surge) 현상을 방지하고 화물창 압력 변동에 맞춰 컴프레서의 용량(Capacity)을 자동 제어합니다. | 안티 서지 밸브(Anti-surge Valve) 개도 제어값, 컴프레서 바이패스 루프 상태 데이터. |
| 110 | **High Duty Nitrongen generator** | LNG선 화물 하역 전후, 화물창 내부를 대량으로 급속 퍼지(Purge) 및 치환하기 위해 설계된 대용량 고압 질소 공급 제어 시스템입니다. | 대용량 질소 가스 라인 유량 및 압력, 압축기 단별 토출 온도, 질소 순도 알람 접점. |

### G. 안전 (Safety Systems)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 14 | **Gas Detection System** | 화물 구역 주변 및 선내 위험 구역의 가스 농도를 상시 흡입·분석하여 누출 여부를 감지합니다. | 구역별 가스 농도(LEL % 또는 ppm), 가스 검지기 교정(Calibration) 상태, 가스 감지 경보 신호. |
| 21 | **Gas leakage alarm system** | 이중관(Double Wall Pipe) 내부나 가스 엔진 주변의 미세 가스 누출을 신속하게 감지하여 경보를 울립니다. | 센서별 가스 누출 경보 접점, 엔진 연료 차단 밸브(Master Gas Fuel Valve) 인터록 트리거 신호. |
| 23 | **Oil mist detection system** | 크랭크케이스 내부 등의 유증기(Oil Mist) 농도를 광학식으로 측정하여 디젤 엔진의 내부 폭발을 사전 예방합니다. | 기통(Cylinder)별 유증기 농도 레벨(mg/L), 고농도 오일 미스트 경보, 센서 오염도 상태 데이터. |
| 25 | **CO2 Alarm System** | 기관실 등 대형 화재 구역에 이산화탄소 소화가스를 방출하기 전, 구역 내 작업자의 대피를 유도하는 시청각 경보장치입니다. | CO2 캐비닛 도어 오픈 신호, 소화가스 방출 카운트다운 시간, 시청각 경보등/사이렌 출력 신호. |
| 56 | **FDS** | 화재 감지 시스템(Fire Detection System)으로 선내 구역별 연기, 불꽃, 열 센서 신호를 수집하여 화재 위치를 즉시 경보합니다. | 화재 감지기 루프 주소(Address), 루프 단선/단락 감지 신호, 화재 발생 구역 ID 디지털 접점. |
| 57 | **PAGA** | 선내 비상 방송 및 일반 확성 장치(Public Address & General Alarm)로 비상 유연 경보 및 대피 방송을 선내 전역에 송출합니다. | General Alarm 톤 발생 신호, 선교/ECR 방송 우선권(Priority) 제어 신호, 앰프 결함(Fault) 신호. |
| 58 | **Signal Light column** | 기관실 등 소음이 심해 방송이 안 들리는 구역에 알람 종류(화재, 주기관 이상, 기기 고장 등)에 맞는 색상등을 점멸하여 시각적으로 경보합니다. | 알람 종류별 온/오프 접점 입력, 경보등 점멸 사이클 제어 신호. |
| 67 | **C/H Smoke Detection System** | 화물창(Cargo Hold) 내부에서 발생하는 미세 연기를 흡입 파이프를 통해 감지하여 화재 징후를 조기에 알립니다. | 화물창 채널별 공기 흡입 유량, 연기 밀도 스캔 지표(%), 화재 알람 접점 신호. |
| 68 | **C/H Water level detection System** | 화물창 내부 바닥에 해수나 누수가 차오르는 것을 감지하여 침수 사고를 방지하는 안전장치입니다. | 화물창 하부 빌지 웰(Bilge Well) 침수 수위(mm), High/Sinking Level 경보 접점. |

### H. 항해 (Navigation / Bridge)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 29 | **X-Band Radar** | 9GHz 대역 주파수를 사용하여 근거리의 타선 및 장애물을 높은 해상도로 탐지하는 항해용 레이더입니다. | 타깃 위치(거리/방위), TT(Target Tracking) 데이터(CPA/TCPA), 레이더 영상 신호 raw 데이터. |
| 30 | **S-Band Radar** | 3GHz 대역 주파수를 사용하여 우천, 폭풍우 등 악천후 상황에서도 먼 거리의 타깃을 탐지하는 항해용 레이더입니다. | 원거리 타깃 추적 데이터, AIS 연동 타깃 정보, 기상 에코(Clutter) 제거 상태 값. |
| 31 | **DGPS** | 위성 GPS 신호에 지상 기준국의 보정 신호를 더해 오차 범위 수 미터 이내의 정밀한 위성 위치 정보를 제공합니다. | 위도/경도 좌표(NMEA 0183 규격 포맷), 고도, HDOP(수평정밀도 저하율), 위성 수신 상태 데이터. |
| 32 | **AIS** | 선박 자동 식별 장치로, 자선의 정보(선명, 위치, 침로, 속력, 화물 등)를 VHF 무선 전파로 타선 및 육상국과 자동 송수신합니다. | MMSI 번호, 자선/타선의 위도·경도, 침로(COG), 대지속력(SOG), 목적지 및 ETA. |
| 33 | **Rudder Angle Indicator** | 현재 타(Rudder)의 실제 회전 각도를 선교 및 조타실의 인디게이터 화면에 실시간으로 표시합니다. | 실제 타각 포지션 신호(Analog 전압/전류 또는 디지털 통신 신호). |
| 34 | **Echo sounder** | 선저에서 해저면을 향해 초음파를 발사하고 되돌아오는 시간을 측정하여 현재 수심을 파악합니다. | 선저 하부 수심(Depth below keel, 미터 단위), 변환기(Transducer) 선택 상태, 디지털 수심 출력 문장(NMEA). |
| 35 | **Doppler Speed Log** | 도플러 효과를 이용하여 선박이 물에 대해 움직이는 속도(대수속력) 및 땅에 대해 움직이는 속도(대지속력)를 측정합니다. | 전후방 속력(Fore/Aft Speed), 좌우방 속력(Port/Stbd Speed), 수심 한계 상태 신호. |
| 36 | **VDR** | 항해용 블랙박스(Voyage Data Recorder)로, 선교 내 음성, 무선 통신, 레이더 화면, 해도 화면, 주요 항해 장비 데이터를 실시간 저장합니다. | VHF 음성 녹음 데이터, 선교 마이크 오디오, 레이더 스크린 캡처 이미지, 항해 센서 데이터 캡처 타임스탬프. |
| 37 | **ECDIS** | 전자해도 정보시스템(Electronic Chart Display and Information System)으로 디지털 해도를 화면에 표출하고 타 항해 장비와 연동합니다. | 전자해도(ENC) 레이어 데이터, 침로 계획(Route Plan) 좌표 리스트, 안전 수심 경보(Safety Contour) 알림 신호. |
| 38 | **Route Planning System** | 목적지까지 안전하고 경제적으로 운항할 수 있도록 경유점(Waypoints), 제한 수심, 기상 정보를 고려하여 항로를 설계하는 시스템입니다. | 경유점 위경도 좌표 세트, 구간별 계획 속력 및 침로, 예상 도달 시간(ETA) 계산값. |
| 39 | **Conning Display System** | 항해 당직자가 한눈에 파악할 수 있도록 조타, 항해 센서, 엔진 상태 등 핵심 정보들을 선교 중앙 화면에 통합 표출합니다. | 자이로 방위, 속력, 타각, 풍향/풍속, 스태프 지시 상태 정보의 통합 디스플레이 데이터 세트. |
| 41 | **Anemometer** | 선박의 마스트 상부에 설치되어 바람의 상대적인 방향(풍향) 및 속도(풍속)를 계측합니다. | 상대 풍향/풍속, (항해 데이터와 연산된) 진 풍향/진 풍속 데이터. |
| 42 | **BNWAS** | 선교 항해당직 경보시스템으로, 설정 시간 동안 항해사의 움직임(스위치 조작 등)이 없으면 단계별로 선내에 강한 경보를 울립니다. | 카운트다운 타이머 잔여 시간, 1차/2차/3차 알람 트리거 신호, 당직자 리셋 버튼 입력 신호. |
| 43 | **Fixed Piloting unit** | 도선사(Pilot)가 지참하는 휴대용 장비(PPU)와 인터페이스하여, 선박 고유의 정밀 항해 GPS 및 AIS 데이터를 유선 고정 포트로 제공합니다. | 파일럿 전용 NMEA 데이터 스트림(정밀 위경도, 헤딩, ROT 데이터). |
| 49 | **Mag' Comp'** | 마그네틱 컴패스(자기나침반)로 전원이 차단된 상태에서도 지구 자기장을 이용해 선박의 절대적인 자침방위를 제공합니다. | 현재 자침 방위 값, 센서 연동용 플럭스게이트(Fluxgate) 출력 신호. |
| 50 | **Auto pilot** | 항해사가 설정한 목표 침로(Heading)와 현재 자이로 컴패스 값을 비교하여 타(Rudder)를 자동으로 제어해 침로를 유지합니다. | 목표 침로(Set Course), 침로 오차(Heading Error), 자동 조타 게인(Gain) 설정치, 비상 수동(Manual) 전환 신호. |
| 51 | **Gyro Comp'** | 고속 회전하는 자이로스코프 원리를 이용해 선박의 자북이 아닌 진북(True North) 기준의 정확한 방위를 항해 장비들에 제공합니다. | 현재 진북 방위(Heading,도 단위), 선박 회전율(ROT, Rate of Turn). |
| 82 | **Satellite Log** | 인공위성 GNSS 신호의 반사 오차 등을 보정하여, 해류의 영향을 배제한 선박의 실제 땅에 대한 속도(대지속력)를 정밀 측정합니다. | 위성 기반 3축(전후, 좌우) 대지 속력 데이터, 위성 신호 품질 지표. |
| 84 | **Sound Reception System** | 가시거리가 짧거나 밀폐된 선교 내부의 항해사를 위해 선외 기적 및 음향 신호를 전방향 마이크로 수신해 방향을 시각화하고 들려줍니다. | 외부 수신 음향의 주파수 및 방향(각도) 데이터, 경보 작동 상태 신호. |
| 90 | **MGC Heading Reference System** | 소형 자이로 컴패스 메커니즘을 기반으로 선박의 방위와 운동 자세(Heading, Roll, Pitch) 기준 정보를 정밀하게 제공합니다. | 자세 제어 보정용 디지털 방위각, 롤링/피칭 각도 가속도 데이터. |
| 97 | **SBAS/GNSS(GPS+GLONASS) Navigator** | 미국 GPS와 러시아 GLONASS 위성 신호를 동시 수신하고 위성 기반 보정시스템(SBAS)을 적용해 최고의 항해 위치 정밀도를 출력합니다. | 멀티 GNSS 위성 좌표 데이터, SBAS 보정 신호 활성화 유무, 위치 오차 타임스탬프 문장. |

### I. 무선통신 (Radio Communication)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 40 | **Weather Fax.** | 무선 단파 방송을 통해 송출되는 기상 일기예보도, 태풍 정보, 파고 예상도 등을 수신하여 이미지 형태로 출력합니다. | 수신 주파수 채널 정보, 기상 팩시밀리 라인 스캔 이미지 데이터. |
| 44 | **Navtex** | 518kHz 등 지정된 주파수로 방송되는 국제 해사 안전 정보(NAVAREA 경보, 기상 경보, 구조 정보)를 수신해 자동 인쇄/표시합니다. | 수신된 안전 메시지 텍스트, 메시지 ID 및 카테고리 분류 코드. |
| 45 | **Immarsat FBB** | 인말새트 위성을 이용한 선박용 초고속 광대역 통신 장비로, 선내 인터넷 통신 및 이메일, 음성 통화를 지원합니다. | 데이터 업로드/다운로드 패킷, 위성 신호 강도(RSSI), IP 할당 및 대역폭 제어 데이터. |
| 46 | **Immarsat C** | 국제해사기구(IMO) GMDSS 규정에 필수적인 저속 위성 통신 장비로, GMDSS 비상 알람(Distress Alert) 및 짧은 데이터 텍스트를 송수신합니다. | Distress 전송 신호, 안전 확인(Inmarsat-C 로그온) 상태, EGC(해상안전정보 방송) 수신 문자열. |
| 47 | **MF/HF** | 중단파 및 단파대 무선 설비로, 원거리(수백~수천 마일) 통신 및 DSC(디지털 선택 호출) 기능을 이용한 비상 경보 통신을 수행합니다. | 수신/송신 주파수(kHz), DSC Distress 호출 데이터, 무선 음성 신호. |
| 48 | **VHF** | 초단파 무선 설비로, 인근 선박 또는 항만 관제소(VTS)와의 근거리 무선 통신 및 DSC 채널 70을 통한 비상 통신을 담당합니다. | 채널 번호(예: Ch.16), DSC 수신 신호, 송신 출력 상태(High/Low). |

### J. 선내통신·기타 (Internal Comm & Misc)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 52 | **Common Battery Telephone** | 선내 정전 시에도 자체 수동 발전기 또는 축전지 전원을 이용해 조타실-기관실 등 필수 구역 간 직통 통화를 확보하는 비상 전화입니다. | 링어(Bell) 트리거 접점 신호, 음성 아날로그 신호. |
| 53 | **Auto Telephon system** | 선내 장착된 전자식 교환기를 통해 선교, 거주구, 기관실 각 구역 간 일상적인 내부 통화를 가능하게 하는 자동 다이얼 전화입니다. | 내선 번호 다이얼 신호, 통화 라인 점유/해제 상태 신호. |
| 54 | **Communal Aerial System** | 선박 마스트의 전방향 안테나로 수신된 지상파 TV, 라디오 및 위성 TV 신호를 선내 수많은 객실(Cabin)로 손실 없이 증폭·분배합니다. | RF 무선 주파수 신호 레벨, 분배기 감쇄율 상태. |
| 55 | **Master Clock** | 선박 내 각 구역에 분산 설치된 자시계(Slave Clock)들의 시간을 GPS 위성 시간과 연동하여 일제히 표준시로 동기화합니다. | 시간 동기화 펄스 신호(1분/1초 단위 펄스), UTC 시간 문자열 데이터. |
| 66 | **Miscellaneous System** | 선박 내 특정 카테고리에 포함되지 않는 기타 보조 잡종 장비들의 동작 유무를 감시합니다. | 개별 온/오프 상태 신호, 공통 알람(Common Alarm) 접점. |

### K. 자동화 (Automation)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 18 | **Alarm Monitoring System(AMS)** | 선박 내 기관실 및 주요 장비의 수천 개 센서 신호를 통합 취합하여 경보를 발생시키고 모니터링합니다. | 선내 모든 아날로그 센서값(온도/압력/레벨 등), 디지털 알람 상태 접점, 알람 알림(Acknowledge) 신호, 이벤트 로그 데이터. |
| 70 | **IAS(Integrated Automation System)** | 선박 전체의 제어 계통(알람 감시, 화물 제어, 전력 제어 등)을 대형 워크스테이션 HMI 및 분산 제어기(DPU)로 통합 관리합니다. | 선내 분산 제어 필드 네트워크 패킷, 시스템 이중화 상태 신호, 전 선박 통합 센서 및 밸브 데이터베이스 마스터 정보. |

### L. 스마트십·성능 (Smart Ship & Performance)

| # | 시스템 | 기능 요약 | 주요 data |
| --- | --- | --- | --- |
| 27 | **Ship's Performance System** | 선박의 속도, 출력, 연료 소비량을 종합 분석하여 에너지 효율 지표 파악 및 운항 효율성을 평가합니다. | 축 출력(Shaft Power), 실시간 연료 소모율(FOC), 선속(Speed Log/GPS), 선박 성능 저하(Fouling) 지수. |
| 28 | **Kyma Ship Performance Monitoring System** | Kyma 사의 토크미터 및 데이터를 기반으로 선박 주추진 장치의 효율과 마력을 정밀 모니터링하는 전문 시스템입니다. | 주기관 제동마력(BHP), 축 토크(Torque), 회전수(RPM), 실시간 슬립률(Slip Ratio). |
| 64 | **Shaft Power Meter** | 선박 추진축에 센서를 부착하여 회전 시 발생하는 뒤틀림(토크)과 회전수를 계측해 마력과 효율을 계산합니다. | 축 토크(kN·m), 축 회전수(RPM), 계산된 추진축 마력(kW 또는 HP). |
| 83 | **HS4(HANWHA Smart ship Solution)** | 한화조선해양의 스마트십 솔루션으로, 전 선박의 OT 데이터를 수집·분석하여 경제 운항 가이드 및 육상 원격 관제를 지원합니다. | 전 선박 통합 IoT 데이터 스트림, 선측-육상 간 위성 데이터 전송 주기/용량, 기관 및 항해 통합 모니터링 분석 로그. |
| 94 | **K-IMS** | 선박의 운항 및 기관 데이터를 통합 관리하고 육상 스마트플랫폼과 동기화하는 친환경/스마트십 데이터 플랫폼입니다. | 표준화된 선박 OT 시계열 데이터 세트, 통신 게이트웨이 상태, 육상 데이터 전송 동기화 플래그. |
| 95 | **GLOBAL 4G** | 연안 및 항만 정박 중 고가의 위성 통신 대신 모바일 4G/LTE 가입자망을 활용해 대용량 데이터를 고속 통신하는 시스템입니다. | LTE 라우터 신호 감도(RSRP/RSRQ), 데이터 트래픽 소모량, 위성-4G 통신 자동 전환(Failover) 신호. |
| 96 | **KMSM Network System** | 선내 설치된 스마트 제어 및 감시 자산들을 상호 연결하고 보안을 유지하는 선내 백본 네트워크 인프라입니다. | 네트워크 스위치 포트 링크 상태, VLAN 트래픽 로드, 네트워크 토폴로지 이상 경보. |
| 101 | **ISS(Integrated Smart Ship Solution) - 현대** | HD현대 기반의 통합 스마트십 솔루션으로 연료 절감 운항 최적화, 최적 항로 생성 및 시스템 원격 진단을 담당합니다. | 통합 수집 인프라 로그 데이터, AI 기반 기상 라우팅 추정 항로 좌표, 에너지 효율 모니터링 데이터 세트. |
| 106 | **HiNAS(Hyundai Intelligent Navigation System)** | AI 기반 지능형 항해 시스템으로 항해 카메라 및 레이더 센서 융합을 통해 주변 선박을 자동 식별하고 충돌 회피 항로를 제안합니다. | 증강현실(AR) 기반 타선 타깃 박스 좌표, 충돌 위험도 지표(CPA 위험 경보), 자율운항 제어 명령 셋. |
| 107 | **NAVBOX** | 선측 항해 및 기관 장비의 원시 NMEA/Modbus 데이터를 표준 규격으로 패킹하여 육상 클라우드로 전송하는 스마트십 게이트웨이 보안 장비입니다. | 항해 세션 데이터 백업 로그, 육상 통신 VPN 터널링 상태, 보안 인증서 유효성 신호. |
