# 분석 노트 — BRIDGE BREAK: New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters

- 서지: Forescout Research (Vedere Labs), 2026. 벤더 기술보고서 (**동료심사 논문 아님**)
- 원문: `papers/Forescout BRIDGE BREAK Report FINAL.pdf`
- 표기: `[보고서]` = 원문에 직접 적힌 내용 / `[추론]` = 내 해석

> ⭐ **본 연구에서 가장 중요한 문헌.** E26 6.4 C-a("IP 네트워크 연결 없음")가 왜 격리를 보장하지 못하는지를 실물 장비 취약점으로 실증한다.

## 요약 (6행)

| 항목 | 내용 |
|---|---|
| 문제 | Serial-to-IP 컨버터는 레거시 시리얼 장비를 IP망에 연결하는 '지루한' 장비로 취급되나, 실제로는 중요 인프라에서 과도한 영향력을 갖는 경계 장치 |
| 방법 | 주요 제조사 제품 펌웨어 수집·언팩 → 소프트웨어 구성 분석(SBOM) → 수동 취약점 분석 → PoC 공격 시나리오 2건 실험 |
| 데이터 | Lantronix EDS3000PS(fw 2.1.0.0R3), EDS5000(fw 3.1.0.0R2), Silex SD330-AC(fw 1.42) 등. Shodan 관측 약 20,000대, 전 세계 추정 1,000만 대 이상 |
| 결과 | **신규 취약점 20건** (Lantronix 8 + Silex 12) + n-day 2건. RCE, 인증 우회, 하드코딩 서명키를 통한 펌웨어 변조, DoS. 실험실에서 시리얼 온도계 값을 24°C → -40~+40°C 진동으로 조작 성공 |
| 한계 | 벤더 보고서(동료심사 없음). 3개 제품에 한정. 선박 환경에서의 직접 실증은 없음(용례 언급만) |
| 관련성 | **확장 + 핵심 근거.** R1·R2·R5의 직접 실증. 선박 적용은 내가 채워야 할 공백 |

---

## 1. 연구 목적
[보고서] 지난 10년간 중요 인프라 대상 공격이 증가한 상황에서 **serial-to-IP 컨버터의 보안 상태를 재점검**하는 것.

## 2. 연구 문제
[보고서]
- Serial-to-IP 컨버터는 RS-232/RS-422/**RS-485**를 TCP/IP로 변환하는 장치로, 병원 의료기기, 공장 PLC·센서·액추에이터, 변전소 RTU·IED·릴레이의 연결을 담당
- "Legacy serial equipment is not going away any time soon"
- **위협 행위자는 이 장비를 지루하게 여기지 않는다.** 2015년 우크라이나 공격에서 여러 serial-to-IP 컨버터의 펌웨어가 의도적으로 손상되어 변전소가 원격 운용 불능 상태가 됨. 2025년 폴란드 전력망에서 재차 공격 대상이 됨
- 2016년 이후 이 제품군에 대한 체계적 연구가 거의 없었음

## 3. 연구 대상
[보고서] 주요 제조사: Moxa, Digi, Advantech, Lantronix, Perle, Silex 등. 상세 분석 대상 3종:
- Lantronix EDS3000PS Series (8~16 시리얼 포트), fw 2.1.0.0R3
- Lantronix EDS5000 Series (8/16/32 포트, 랙마운트), fw 3.1.0.0R2
- Silex SD330-AC (RS-232C를 **무선 또는 이더넷**으로 연결), fw 1.42

**선박 용례 [보고서]**: "Critical shipboard systems for maintenance, monitoring, and control, including **propulsion and steering** systems; and the **Electronic Chart Display and Information System (ECDIS)** used for navigation."

**선행 연구 [보고서]**: "2018: Ken Munro demonstrated how serial-to-IP converters could be used to **compromise shipboard networks**." → [확인필요] Munro의 원자료(Pen Test Partners) 확보 필요. 내 논문에 직접 인용 가치 큼

## 4. 연구 방법
[보고서]
1. 펌웨어 수집 및 언팩 가능한 제품 선정
2. 소프트웨어 구성 분석 — Linux 커널 버전, 빌드 도구, 서드파티 컴포넌트
3. 수동 취약점 분석 (시간 제약으로 3개 제품에 집중)
4. 조율된 취약점 공개(coordinated disclosure)
5. 실험실 PoC — 공격 시나리오 2건 (OT 데이터 변조 / 헬스케어 DoS)

## 5. 핵심 결과

### 5.1 취약점
[보고서] **신규 20건** — Lantronix 8건, Silex 12건. 추가로 Silex에서 n-day 2건 확인(CVE-2015-5621, CVE-2024-24487).

영향 범주:
- OS 명령 주입·메모리 손상(버퍼 오버플로)을 통한 **원격 코드 실행(RCE)**
- 인증 취약점을 통한 **장치 완전 장악**
- **하드코딩된 서명키**로 인한 펌웨어 변조
- DoS
- 임의 파일 업로드, 인증 우회, 약한 암호화로 인한 정보 노출(패스워드·키 포함)

주요 CVE: CVE-2026-32955~32965 (Silex), CVE-2025-67034~67041 (Lantronix)

### 5.2 노출 규모
[보고서] Shodan 단순 질의로 약 **20,000대** 관측 (Lantronix 8,292 / Moxa 3,859 등). 전 세계 실제 배치는 **1,000만 대 이상**으로 추정 (Moxa "8,200만 대 연결" 진술 기준, 컨버터당 평균 8대 가정).

### 5.3 공격 영향 3유형
[보고서]
1. **Denial of service** — 시리얼 통신 두절. 2015년(펌웨어 손상)과 2025년(도달 불가 IP 주소 설정)의 서로 다른 방식
2. **Lateral movement** — 비라우팅(non-routable) OT 네트워크의 경계를 넘음. 2023년 선행연구에서 시리얼 링크를 악용해 Purdue Level 1 자산 간 이동 실증
3. **센서·액추에이터 데이터 변조** — 시리얼→IP 방향의 센서값 변조, IP→시리얼 방향의 명령 변조. "changing the speed or direction of a servo motor"

[보고서] 컨버터가 침해되면:
- 시리얼 통신을 **양방향으로** 변조 가능
- **"Serial protocols often lack authentication or encryption"**
- 결과적으로 그 시리얼 링크에 의존하는 장치·프로세스에 영향 가능

[보고서] MITRE ATT&CK for ICS **T0832 – Manipulation of View**에 대응한다고 명시. Stuxnet의 운영자 기만과 동일한 결과를 컨버터 악용으로 달성 가능.

### 5.4 실증 (Scenario 1)
[보고서] 실험실에서 시리얼 온도계를 SCADA 애플리케이션에 연결. 공격 전 약 24°C 안정. **공격 후 그래프가 -40°C ~ +40°C로 진동.** 역으로 **진동하는 실제 값을 안정된 값처럼 보이게 하는 것도 가능**.

초기 접근 경로: 인터넷 노출 엣지 장비(산업용 라우터·방화벽·**VPN 집중장치**), 침해된 IT 워크스테이션, OT 네트워크 내 deep lateral movement, (병원의 경우) 물리 접근 + 평면 네트워크.

## 6. 기존 연구와 차이
[보고서] 2015~2020년 사이 개별 연구(Maldonado DEF CON 2015, Wightman S4 2016, Anubhav 2017, **Munro 2018 선박**, Larsen S4 2020)는 있었으나, 그 이후 "limited new research beyond additional single vulnerability disclosures". 이 보고서는 **현행 제품군 전반의 보안 태세를 교차 벤더로 평가**한 것이 차별점.

## 7. 한계 (저자 인정 + 관찰)
[보고서 — 저자 인정]
- "Due to time constraints" 3개 제품·펌웨어에 한정
- Shodan 결과는 오탐 포함 가능하며 전체를 과소추정
- 실제 배치 규모는 "difficult to know"

[추론 — 내 관찰]
- **벤더 보고서**로 동료심사를 거치지 않음. 학술 인용 시 성격을 명시해야 함
- 선박 환경에서의 실증이 없음. 선박은 "Other Use Cases"에서 한 줄 언급될 뿐
- NMEA 0183/2000 등 **선박 고유 시리얼 프로토콜**은 다루지 않음 → **이 공백이 곧 내 연구의 자리**

## 8. 내가 가져갈 것
1. **R1의 결정적 근거**: "Serial protocols often lack authentication or encryption" + 온도계 값 변조 PoC. 2026-08-11 메모의 "시리얼이라고 안전하다는 근거는 어디에도 없다"를 실증으로 뒷받침
2. **R2의 결정적 근거**: 컨버터는 시리얼 세계와 IP 세계의 **경계**다. E26 6.4 C-a가 "IP 네트워크 연결 없음"을 격리로 정의하지만, 시리얼로만 연결된 CBS라도 어딘가에서 컨버터를 만나면 IP 세계와 이어진다. **격리의 정의 자체가 성립하지 않는 지점**
3. **R5·R9의 근거**: T0832 Manipulation of View — 운영자가 보는 값을 조작. 정박 중 화물·항해 정보가 왜곡되어도 안전 사고로 즉시 드러나지 않음 → E26 6.4의 "no impact on the safety of operations" 판정을 통과
4. **실제 공격 이력**: 우크라이나 2015(펌웨어 손상 → 변전소 원격 운용 불능), 폴란드 2025(GCP 공격). 시리얼 경계 장치가 **가설이 아니라 실제 표적**임을 보이는 사례
5. **Purdue Level 1 lateral movement**(2023 선행연구) — R6(제외 CBS → Cat III CBS 피벗)의 유비
6. **[확인필요] Ken Munro (2018) 원자료** — 선박 네트워크를 serial-to-IP 컨버터로 침해한 시연. 확보되면 내 논문의 선박 특화 근거로 최상급

## 9. 내 연구와의 관계
**확장 (핵심 근거 문헌).**
- 이 보고서는 "시리얼 경계 장치는 취약하다"를 **일반 ICS 환경에서** 입증했다
- 내 연구는 이를 **선박 규정 맥락으로 확장**한다: "그런데 UR E26 6.4는 바로 그 시리얼 연결을 격리로 인정하고 CBS를 감시 대상에서 제외한다"
- **공백이 명확하다**: 이 보고서는 선박 용례를 한 줄 언급하고 NMEA를 다루지 않음. 선박 환경 + 규정 축은 비어 있음
- ⚠️ 벤더 보고서이므로, 학술 논문(RS-485 실증연구, DNP3 시리얼 취약점)과 **함께** 인용해 근거를 분산시킬 것

## 다음 확인
- [ ] Ken Munro / Pen Test Partners의 2018 선박 시연 원자료 확보
- [ ] Forescout 2023 "deep lateral movement" 보고서 확보 (Purdue Level 1 이동)
- [ ] 선박에 실제로 serial-to-IP 컨버터가 쓰이는지 — 어떤 장비가, 어디에? (실무 지식으로 확인 가능한 영역)
- [ ] NMEA 0183/2000 게이트웨이가 기능상 serial-to-IP 컨버터와 동일한지

## 연결
- [[2026-08-13_e26-exclusion-residual-threat_mapping]] — R1, R2, R5, R6, R9의 근거
- [[2018_kang_onboard-ship-cybersecurity_note]] — 그 논문에 빠진 시리얼 관점을 이 보고서가 채움
