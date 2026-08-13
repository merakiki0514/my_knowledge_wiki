# UR E26 제외 기준(6.4) × 잔여 위협 매핑

작성일: 2026-08-13
목적: "E26 6.4의 제외 기준을 **모두 충족**하면서도 남는 위협"을 조항 단위로 도출한다. 본 논문의 핵심 기여표.
표기 규칙: `[규정]` = 규정 원문에 직접 적힌 내용 / `[추론]` = 해석 / `[확인필요]` = 출처 미확보

---

## 0. 근거 문서

| 문서 | 파일 | 확인 상태 |
|---|---|---|
| IACS UR E26 Rev.1 (Nov 2023) | `rules/UR-E26-Rev.1-Nov-2023-CR.pdf` | 원문 확인 |
| IACS UR E26 (Apr 2022, 철회) | 외부(maritimecyprus 사본) | 원문 확인, **로컬 미보관** |
| IACS UR E22 Rev.3 Corr.1 (Sep 2025) | `rules/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` | 원문 확인 |
| IACS UR E27 Rev.1 (Sep 2023) | `rules/UR-E27-Rev.1-Sep-2023-CLN.pdf` | 원문 확인 |
| IEC 61162-460 Ed.3.0 (2024) | `rules/info_iec61162-460{ed3.0}en.pdf` | **미리보기본** — 3장(용어)까지만 수록, 요구사항 조항 없음 |

⚠️ `rules/IEC-61163-2-2020.pdf`는 **IEC 61163-2 "Reliability stress screening – Components"** 로, 본 연구와 무관한 표준입니다(61162 → 61163 오타로 보임). 재확보 필요.

---

## 1. E26 6.4 제외 기준 원문 [규정]

### 1.1 필수 충족 기준 (shall be met) — 본 연구의 "Critical Criteria"

> "The following criteria **shall be met** to exclude a system from the scope of applicability of this UR"

| ID | 원문 요지 |
|---|---|
| **C-a** | CBS는 격리될 것 (i.e., 다른 시스템·네트워크와 **IP-network 연결이 없을 것**) |
| **C-b** | 접근 가능한 물리 인터페이스 포트가 없을 것. 미사용 인터페이스는 논리적으로 비활성화. 비인가 장치 연결이 불가할 것 |
| **C-c** | 물리적 접근이 통제되는 구역에 위치할 것 |
| **C-d** | 1.3절 범위의 다중 선박 기능을 담당하는 통합제어시스템이 아닐 것 |

### 1.2 추가 고려 기준 (should be considered) — "Additional Criteria"

> "The following **additional criteria should be considered** for the evaluation of risk level acceptability"

| ID | 원문 요지 |
|---|---|
| **A-a** | Category III 선박 기능을 담당하지 않을 것 |
| **A-b** | 알려진(Known) 취약점·위협·영향이 risk assessment에 반영되었을 것 |
| **A-c** | 복잡도·연결성·물리/논리 접근점(무선 포함)을 고려해 공격면이 최소화되었을 것 |

### 1.3 제외 시 면제되는 요구사항 [규정]

제외되면 E26 4장 전체가 적용되지 않습니다. 즉 다음이 **모두** 사라집니다.

| 절 | 요구사항 | 제외 시 상실되는 것 |
|---|---|---|
| 4.1.1 | Vessel asset inventory | 해당 CBS가 **자산 목록에서 사라짐** |
| 4.2.1 | Security zones & network segmentation | zone/conduit 다이어그램에서 누락 |
| 4.2.2 | Network protection safeguards | 경계 방어 미적용 |
| 4.2.3 | Antivirus/antimalware | 악성코드 대책 미적용 |
| 4.2.4 | Access control | 계정·권한 통제 미적용 |
| 4.2.5 | Wireless communication | 무선 보안 요구 미적용 |
| 4.2.6 | Remote access control | 원격접속 통제 미적용 |
| 4.2.7 | Mobile & portable devices | 휴대장치 통제 미적용 |
| 4.3.1 | Network operation monitoring | **탐지 대상에서 제외** |
| 4.3.2 | Verification & diagnostic functions | 무결성 점검 미적용 |
| 4.4.1 | Incident response plan | **IR 계획에 미포함** |
| 4.4.2 | Local/independent/manual operation | 수동 대체수단 미보장 |
| 4.4.3 | Network isolation | 격리 절차 미포함 |

**[추론] 이 표가 논문의 위험도 논증의 핵심입니다.** 제외는 "요구사항 몇 개 면제"가 아니라 **Identify–Protect–Detect–Respond 전 단계에서의 소거**입니다. 특히 4.1.1(자산목록)과 4.3.1(모니터링)에서 빠진다는 것은, 해당 CBS가 침해되어도 **가시성 자체가 없다**는 뜻입니다.

---

## 2. 핵심 발견 1 — 개정 과정에서 "전이(propagation) 조건"이 삭제됨

E26 2022년판(Apr 2022) 6.4는 기준을 **a)~l) 12개**로 두고 전부 "shall be considered"로 규정했습니다. Rev.1(Nov 2023)에서 **4개 shall + 3개 should = 7개**로 재편되었습니다. [규정]

| 2022년판 | Rev.1 (2023)에서의 처리 |
|---|---|
| f) IP 기반 네트워크로 다른 CBS에 연결되지 않을 것 | **C-a로 승격** (고려 → 필수) |
| g) 비통제 이동식 장치가 쓸 수 있는 물리 인터페이스 없을 것 | **C-b로 승격** |
| e) 통제된 접근 구역에 위치 | **C-c로 승격** |
| d) 필수 서비스 또는 다중 선박 서비스를 담당하지 않을 것 | **C-d로 변경** ("통합제어시스템"으로 **범위 축소**) |
| a) 예견 가능한(Foreseeable) 취약점·위협·영향 고려 | A-b로 잔류, **"Known"으로 문구 약화** |
| b) 공격면 최소화 | A-c로 잔류 |
| **c) 다른 CBS·네트워크 장치로부터 사이버 사고가 전이되어 영향받지 않을 것, 그리고 다른 CBS·네트워크 장치로 사고 영향을 전파하지 않을 것** | **🔴 삭제됨** |
| h) 설치 소프트웨어 식별(목적·이름·버전·공급자·유지보수자) | **🔴 삭제됨** |
| i) 유지보수 정책이 비신뢰 네트워크 연결이나 비통제 이동식 장치 사용을 수반하지 않을 것 | **🔴 삭제됨** |
| j) 하드웨어·소프트웨어 무결성 포함, 상시 기능 무결성 확인 수단 제공 | **🔴 삭제됨** |
| k) 운영자의 로컬 수동 제어 인터페이스 제공(공격면 확대 없이) | **🔴 삭제됨** |
| l) IR/복구 계획에 해당 CBS 처리 방법 명시 | **🔴 삭제됨** |
| — | A-a "Category III 기능 미담당" **신설** |

**[추론] 이것이 본 연구의 가장 강한 규정적 논거입니다.** 삭제된 c)항은 정확히 **전이·피벗 위협**을 다루던 유일한 조항이었고, 이 연구가 제기하는 문제("제외된 CBS가 다른 CBS로 가는 발판이 된다")를 규정이 **한때 인지했다가 놓아버렸다**는 것을 보여줍니다. 삭제된 h)·j)·l)도 각각 SBOM·무결성 검증·IR 포함이라는, 현재 보안 실무의 기본 통제입니다.

### 2.1 함께 확인된 6장 전반의 변경 [규정]

기준 목록 외에도 6장에서 세 가지가 바뀌었습니다. 모두 원문 대조로 확인했습니다.

| 항목 | 2022년판 | Rev.1 (2023) | 평가 |
|---|---|---|---|
| **6.4 수용 문턱의 입증 기준** | "only if **evidence** is given that the operation of the CBS has no impact on the safety of operations" | "only if **assurance** is given that ..." | 🔴 **입증 기준 약화.** evidence(입증 자료)는 제시 의무를, assurance(보증·확언)는 진술로 갈음될 여지를 남김 |
| **제외 항목 목록의 선내 유지** | "A concise list of excluded applications of relevant requirements is to be generated and maintained with the CBS documents onboard the ship" (6.1·6.3에 2회 기술) | **문구 자체가 없음** | 🔴 별도 요약 목록의 선내 생성·유지 의무 소멸 |
| **선급의 거부권 명시** | "The Class Society may accept or reject the exclusion of the CBS" | **문구 없음** | 판단 재량은 남으나 명문 규정이 사라짐 |
| **위험평가 주체** | "by the **Shipyard**" (6.3) | "by the **System integrator**" (6.3) | 책임 주체 이동 |

⚠️ 정확한 서술을 위한 단서:
- 위험평가 문서 자체는 Rev.1에서도 **5.1.4 "Risk assessment for the exclusion of CBSs"** 로 제출·유지 대상입니다(Appendix I: Submit → Maintain). 따라서 "제외 기록이 전혀 남지 않는다"는 과장입니다. 정확히는 **"제외 항목만 추린 간결한 목록을 선내에 유지할 의무가 사라졌다"** 입니다. 검사관이나 사고 대응자가 실제로 펼쳐 볼 형태의 문서가 사라진 것.
- **6.2 Rationale은 Rev.1에서도 여전히 "only if evidence is given"** 이라고 씁니다. 즉 **같은 6장 안에서 6.2는 evidence를, 6.4는 assurance를 요구**합니다. 규정 내부의 용어 불일치이며, 실무에서 어느 쪽을 적용할지에 대한 해석 여지를 만듭니다. → §8의 심사 편차 논거와 직결

⚠️ 서술상 주의: 2022년판은 **발효 전에 철회**되고 Rev.1로 대체되었습니다. 따라서 "요구사항이 시행 중에 완화되었다"고 쓰면 부정확합니다. **"제정 과정에서 전이 조건이 최종안에서 제외되었다"** 로 서술해야 합니다. [확인필요] IACS가 이 변경 사유를 공개한 문서가 있는지 — 있다면 논거가 결정적으로 강해집니다.

---

## 3. 핵심 발견 2 — Category 체계는 "고장(failure)" 기준이지 "공격(attack)" 기준이 아님

UR E22 3.1 Table 3 [규정]:

> "The categorization of a system in the context of this UR is based on the potential severity of the consequences **if the system serving the function fails**."

| Cat | 고장 영향 | 예시 시스템 |
|---|---|---|
| I | 위험 상황으로 이어지지 않음 | 연료 모니터링, 정비지원, 진단, **CCTV**, 선실 보안, 엔터테인먼트, 어군탐지 |
| II | 결국(eventually) 위험 상황 초래 가능 | 연료유 처리, 추진·보조기계 경보/안전, 불활성가스, 화물창 제어·안전 |
| III | 즉시(immediately) 위험·재난 상황 초래 가능 | 추진제어, 조타기제어, 전력시스템(PMS 포함), DP(class 2·3) |

E22 4.3.3 [규정]: "it shall be decided which category the system falls under **based on the failure effects** of the system"

E22 3.2 [규정]: Cat I은 통상 선급 검증 대상이 아니나, "정보는 요청 시 제출되어야 하며 — **Cat II·III 시스템의 운영에 영향을 주지 않음을 보장하기 위함**"

**[추론] 여기에 범주 오류(category error)가 있습니다.**
- Category는 **우발적 고장의 안전 결과**를 재는 척도입니다. 공격자를 상정하지 않습니다.
- 안전공학에서 저심각도 자산은 저우선순위지만, 보안에서 저심각도 자산은 **고가치 교두보**가 될 수 있습니다. 침해 시 직접 피해가 작다는 것과, 침해 경로로서의 가치가 낮다는 것은 전혀 다른 명제입니다.
- E22 3.2가 "Cat I이 Cat II·III에 영향을 주지 않아야 한다"고 **명시**했는데도, E26 6.4에는 이를 검증하는 절차가 없습니다. 그 검증을 담당했을 조항이 바로 §2에서 삭제된 2022년판 c)항입니다.
- Cat I 예시에 **CCTV**가 명시되어 있고, 사용자가 실무에서 관찰한 Smart ship solution(S-Vessel·HS4·Navbox)은 "monitoring, informational and administrative functions"에 해당해 Cat I로 분류되기 쉽습니다.

이 절이 논문에서 A-a(Category III 미담당) 기준을 반박하는 근거가 됩니다.

---

## 4. 매핑표 — 기준을 통과하면서도 남는 위협 (본 논문 핵심표)

각 행: **"기준을 충족했다"는 사실이 배제하지 못하는 위협**.
ATT&CK for ICS 기법 ID는 MITRE ATT&CK ICS 매트릭스 현행판 기준으로 확인함.

| # | 기준 | 기준이 보장하는 것 | 보장하지 못하는 것 (잔여 위협) | ATT&CK for ICS | 근거 문헌(papers/) |
|---|---|---|---|---|---|
| **R1** | **C-a** IP 네트워크 연결 없음 | IP 기반 원격 침투 차단 | **시리얼 연결은 제한하지 않음.** NMEA 0183/RS-485/Modbus RTU 등은 인증·암호화·무결성이 없어 물리 접속만으로 메시지 주입·변조 가능. E26 4.2.1.1은 zone 연결 수단으로 *simplex serial links*를 명시 허용하고, 4.2.1.4.1은 비신뢰 네트워크와의 통신 기술서에 *discrete signals, serial communication* 포함을 요구 → **규정은 시리얼의 존재를 알면서 제외 판정에서는 IP만 본다** | T1692.001/.002 Unauthorized Message (Command/Reporting), T1695.001 Block Communications: Serial COM, T0830 AiTM, T0842 Network Sniffing | RS-485 통신보안 실증연구; 전력 제어시스템 시리얼 DNP 취약점; 제어네트워크 프로토콜 위협연구 |
| **R2** | **C-a** | 논리적 격리 | **비IP 경로 전체가 사각지대**: USB, 정비용 노트북, 무선(Wi-Fi/BLE), 위성단말 백채널. 격리의 정의가 IP로 한정되어 air-gap과 동일시됨 | T0847 Replication Through Removable Media, T0864 Transient Cyber Asset, T0860 Wireless Compromise, T0887 Wireless Sniffing | TRITON; Vulnerability analysis of S7 PLCs |
| **R3** | **C-b** 접근 가능 물리 포트 없음 | 정상 상태의 외부 포트 부재 | **"접근 가능(accessible)"·"논리적 비활성화"의 판정 기준이 규정에 없음.** 디버그 UART·JTAG·내부 헤더·서비스 커넥터는 케이스 개방 시 노출. 논리적 비활성화는 펌웨어 수준에서 복구 가능 | T1693 Modify Firmware, T0862 Supply Chain Compromise | ICSREF; Reverse Engineering of Private Protocols; PropFuzz / FieldFuzz |
| **R4** | **C-c** 물리적 접근 통제 구역 | 구역 지정 사실 | **구역 지정의 근거·수준·검증 방법이 규정에 없음.** 브릿지·기관실은 정박 중 검사관·기술자·항만 인력·벤더가 상시 출입 → 실효적 통제 곤란. E26에 출입 로깅·이중 통제·감사 요구 없음 | T0864 Transient Cyber Asset, T0847 | [확인필요] 항만 정박 중 승선 인원 통계 |
| **R5** | **C-d** 통합제어시스템 아님 | 다기능 통합 제어의 배제 | **단일기능 CBS도 통합 시스템에 데이터를 공급하면 무결성 원천이 됨.** Smart ship solution은 스스로 제어하지 않지만 ICMS·육상으로 데이터를 중계 → 오염된 입력이 정상 제어 판단을 왜곡. 2022년판 c)항이 다루던 지점이나 현재 미검증 | T0832 Manipulation of View, T0829 Loss of View, T0882 Theft of Operational Information | Forescout BRIDGE BREAK; 선박 사이버보안 위협모델링 VSAT |
| **R6** | **A-a** Cat III 미담당 | 고심각도 기능 배제 | **Category는 고장 기준이지 공격 기준이 아님(§3).** Cat I 자산이 Cat III 자산으로 가는 피벗이 될 수 있으나 E26 6.4에 전이 검증 절차 없음. E22 3.2는 "Cat I이 Cat II·III에 영향 없어야 한다"고 하면서 검증 방법을 제시하지 않음 | T0867 Lateral Tool Transfer, T0859 Valid Accounts, T0866 Exploitation of Remote Services | ATT&CK for ICS Philosophy; TRITON; Bypassing NAC |
| **R7** | **A-b** 알려진 취약점 반영 | 기지 취약점 고려 | **"Known"으로 한정** → 미공개·독자 프로토콜 취약점은 원천적으로 대상 밖. 선박 장비는 폐쇄형 독자 프로토콜 비중이 높아 CVE가 존재하지 않는 경우가 다수. 2022년판의 "Foreseeable"보다 후퇴한 문구 | T0862 Supply Chain Compromise | Reverse Engineering of Private Protocols; WireWatch; Protocol Fuzzing surveys |
| **R8** | **A-c** 공격면 최소화 | 공격면 고려 | **정량 기준·측정 방법 부재.** 주 평가도구인 BIMCO/IACS Rec.171 방식은 정성 평가여서 평가자 간 재현성이 낮음 | — | IACS Rec 171 + BIMCO Risk Assessment (미분석) |
| **R9** | 전체 | — | **제외 자체가 만드는 2차 위협**: 4.1.1 자산목록·4.3.1 모니터링·4.4.1 IR에서 빠짐 → 침해 시 **탐지·대응 불가**. 공격자에게 "감시받지 않는 노드"가 명세상 보장됨 | T0872 Indicator Removal on Host, T0878 Alarm Suppression | Detection Engineering in ICS |
| **R10** | 전체 | — | **누적 효과 미평가**: 6.4는 CBS를 **개별로** 심사. 제외된 CBS가 다수 누적될 때의 결합 공격면을 평가하는 절차가 없음 | — | [추론] 기존 문헌 미확인 |
| **R11** | **1.3.2** (제외가 아닌 **범위 정의**) | 적용 대상을 OT로 한정 | **IT 시스템 자체는 적용 대상이 아님.** 1.3.2 b)는 IT를 범위에 넣는 것이 아니라 "적용 대상 CBS로부터 다른 시스템으로 향하는 **IP 기반 통신 인터페이스**"만 범위로 함. 예시로 여객용 네트워크, **관리 네트워크**, 승무원 복지 시스템, "OT에 연결되는 그 밖의 모든 시스템(정비 중 일시 연결 포함)" 열거. → 선내 업무망·CCTV·무선·스마트십 솔루션이 IT로 분류되어 판단에서 경시될 여지. 이 범위 설정은 **경계 방어가 유효하다는 전제**에 의존하나, 4.2.2.4는 **설계·건조 단계 "No requirements"**, 시운전은 DoS 2건 + 포트 스캔뿐 → **경계 우회 가능성 자체를 검증하는 시험이 요구되지 않음** | T0819 Exploit Public-Facing Application, T0822 External Remote Services, T0866 Exploitation of Remote Services, T0867 Lateral Tool Transfer, T0859 Valid Accounts | TRITON (IT 침투 → 양쪽 접근 가능 시스템 경유 → OT 이동); Forescout BRIDGE BREAK (인터넷 노출 엣지 장비·VPN 집중장치·침해된 IT 워크스테이션을 통한 초기 접근); Bypassing NAC (2006, 다소 오래됨) |

**[추론] R11은 R1~R10과 층위가 다릅니다.** R1~R10은 **6.4의 명시적 제외**를 통과한 CBS의 잔여 위협이지만, R11은 **1.3.2의 범위 정의** 때문에 애초에 판단 대상에 들어오지 않는 영역의 문제입니다. 즉 이탈 경로가 두 개입니다.
- 경로 A (6.4): 개별 CBS를 요구사항 적용에서 배제
- 경로 B (1.3.2): 영역 단위로 판단의 시야를 축소

두 경로는 서로 다른 층위에서 **동일한 결과 — 보호·감시 대상에서 벗어난 자산의 존재** 로 귀결됩니다. 논문에서는 이 대비 구조로 III장을 닫는 것이 효과적입니다.

⚠️ 서술 주의: "E26이 IT를 전혀 다루지 않는다"는 부정확합니다. 인터페이스는 범위에 있고, 4.2.6(원격접속)·4.2.5(무선)·4.2.7(휴대장치)도 존재합니다. 정확히는 **"IT 시스템 자체의 보안 수준을 요구하지 않고 경계 방어에 의존한다"** 입니다.

---

## 5. 사용자 실무 관찰과의 연결

2026-08-12 메모의 두 경로를 위 매핑에 대응:

| 메모의 위협 | 대응 행 | 규정 통과 논리 |
|---|---|---|
| 내부: Serial 신호 스푸핑 → 기기 오작동 | **R1, R5** | C-a는 IP만 보므로 시리얼 전용 장비는 격리로 인정됨 |
| 외부: 육상-해상 정보 차이 → 항해·화주 계획 차질 | **R5, R9** | 정보계 시스템은 Cat I·단일기능으로 A-a·C-d 통과. 무결성 훼손은 안전 사고가 아니어서 6.4 "no impact on the safety of operations" 판정을 통과 |

**[추론] 두 번째가 특히 중요합니다.** E26 6.4의 수용 문턱은 "**safety of operations**에 영향 없음"입니다. 즉 **안전(safety)에 영향이 없으면 정보 무결성·기밀성 훼손은 제외를 막지 못합니다.** 이는 E26이 safety 중심 프레임이며 CIA 삼요소 중 I·C를 제외 판정에서 사실상 배제한다는 뜻입니다. 자율운항선박은 육상 원격운용센터(RCC)의 상황인식에 의존하므로, 이 프레임에서 정보 무결성 훼손은 **곧바로 안전 문제로 전환**됩니다 → 정식 논문의 MASS 확장 논거.

---

## 6. 논문에서의 주장 구조 (초안)

1. E26 6.4는 CBS 제외 경로를 제공한다 [규정]
2. 제외는 Identify–Protect–Detect–Respond 전 단계에서의 소거를 의미한다 [규정, §1.3]
3. 그런데 제외 기준은 (i) 격리를 IP로 한정하고, (ii) Category를 고장 기준으로 차용하며, (iii) 전이 조건을 담고 있지 않다 [규정, §1·§3·§2]
4. 따라서 기준을 완전히 충족하면서도 R1~R10의 위협이 잔존한다 [추론, §4]
5. 이 잔여 위협은 문헌상 실증된 공격 기법에 대응된다 [문헌]
6. OT/IT가 융합되는 MASS 환경에서 이 격차는 확대된다 [추론 → 정식 논문]

---

## 7. 다음 단계에서 확인할 것

- [ ] IACS가 2022년판 c)·h)~l)항 삭제 사유를 공개한 문서 존재 여부 → 있으면 §2가 결정적
- [ ] IACS Rec.166 / Rec.190이 6.4 제외 심사에 대한 해석 지침을 제공하는지 (미분석)
- [ ] Rec.171 + BIMCO 방법론의 정성성 — R8 논거 확보용 (미분석)
- [ ] IEC 61162-460 전문 확보 → E26 1.3.2의 "대체 수용" 경로가 제외와 어떻게 상호작용하는지
- [ ] ISM Code 중 사이버 관련 해당 조항 특정 (Company 책임·SMS)
- [ ] R4·R10의 선행연구 존재 여부
