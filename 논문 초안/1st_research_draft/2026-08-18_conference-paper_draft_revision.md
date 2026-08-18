# [학술대회 원고 초안] IACS UR E26 CBS 제외 기준의 한계 분석: 사고 전이 관점에서

투고처: 한국정보통신학회(KIICE) 종합학술대회 / 분량: 3쪽
작성 시작: 2026-08-13

## 조판 양식 (확인됨 — 일반적인 국내 논문 제출 템플릿과 동일)

| 요소 | 크기 | 단 구성 |
|---|---|---|
| 요약 (국문) | **9 pt** | 1단 |
| ABSTRACT (영문) | **8 pt** | 1단 |
| 키워드 / Key words | **8 pt** | 1단 |
| 본문 (I. 서론 이후 전체) | **10 pt** | **2단** |

→ 제목·저자·요약·초록·키워드까지는 1단, **I. 서론부터 2단 편집**.
→ 표·그림은 2단 폭에 맞추되, 표 2(제정 과정 대조)는 항목이 길어 **단 전체 폭(1단 걸침)** 배치를 검토할 것.

⚠️ 마감일 미확인.

---

## 제목

**국문**
IACS UR E26 CBS 제외 기준의 한계 분석: 사고 전이 관점에서

**영문**
An Analysis of Limitations in the CBS Exclusion Criteria of IACS UR E26:
From the Perspective of Cyber Incident Propagation

---

## 요약

IACS UR E26은 선박의 사이버 복원력에 관한 통일규칙으로, 기존의 비강제 가이드라인과 달리 설계부터 운항까지 전 생애주기에 걸친 강제 요구사항을 제시한다. 그러나 동 규칙 6.4는 특정 컴퓨터기반시스템(CBS)을 적용 범위에서 제외할 수 있는 경로를 함께 규정하고 있다. 본 논문은 UR E26 Rev.1의 제외 기준을 2022년판 및 UR E22와 대조 분석하여 세 가지 한계를 제시한다. 첫째, 2022년판에 존재하던 사고 전이(propagation) 관련 조건과 CBS 간 연결 관계의 조사·문서화 요구가 최종안에서 제외되어, 제외된 CBS가 다른 CBS에 미치는 영향을 검증할 절차가 부재하다. 둘째, 제외 판정에 차용된 UR E22의 시스템 범주는 고장(failure) 결과를 기준으로 정의되어 공격자를 상정하지 않는다. 셋째, 제외에 수반되는 문서 부담의 비대칭이 규칙 구조에 내재한다. 본 논문은 제외 제도의 폐지가 아니라, 전이 검증의 복원과 판정 기준의 구체화를 제언한다.

**핵심어**: 선박 사이버보안, IACS UR E26, 컴퓨터기반시스템, 사고 전이, 사이버 복원력

---

## ABSTRACT

IACS UR E26 is a unified requirement for the cyber resilience of ships. Unlike earlier non-mandatory guidelines, it imposes mandatory requirements across the entire lifecycle from design to operation. However, Section 6.4 of the same requirement also provides a pathway to exclude certain Computer Based Systems (CBS) from its scope of applicability. This paper analyzes the exclusion criteria of UR E26 Rev.1 against the withdrawn 2022 edition and UR E22, and presents three limitations. First, the condition concerning cyber incident propagation and the requirement that connections between CBSs be duly investigated and documented, both present in the 2022 edition, were not carried into the final text, leaving no procedure to verify the effect of an excluded CBS on other systems. Second, the system categories of UR E22, borrowed for the exclusion assessment, are defined on the basis of failure effects and therefore do not presuppose an adversary. Third, an asymmetry in documentation burden is inherent in the structure of the requirement. This paper proposes not the abolition of the exclusion scheme, but the restoration of propagation verification and the specification of verifiable assessment criteria.

**Key words**: Ship Cyber Security, IACS UR E26, Computer Based System, Incident Propagation, Cyber Resilience

---

## I. 서 론

선박은 오랫동안 육상과 분리된 폐쇄 환경으로 간주되어 왔으나, 정보통신기술의 발전과 선내 장비의 네트워크화가 진행되면서 그 전제는 더 이상 성립하지 않는다. 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서, 선박은 IT와 OT가 혼재하는 복합 환경이 되었다. 이러한 변화는 사이버 위협의 유입 경로를 동시에 확대하였으며, 선박을 대상으로 한 위협 분석과 대응 요구사항 연구가 이어져 왔다[3].

이에 대한 제도적 대응은 비강제 가이드라인에서 출발하였다. BIMCO 등이 발간한 지침[4]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였고, 선급별 권고 수준에 머물렀다. 국제선급연합회(IACS)가 제정한 통일규칙 UR E26[1]은 이 지점에서 분명한 진전이다. 동 규칙은 선박을 하나의 집합체로 보아 사이버 복원력 요구사항을 제시하며, 설계·건조·시운전·운항의 전 생애주기에 걸쳐 문서 제출과 실증을 요구한다. 이는 식별(Identify), 보호(Protect), 탐지(Detect), 대응(Respond), 복구(Recover)의 기능 요소별로 요구사항을 구성된다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 **제외**할 수 있는 경로를 함께 제도화하였다. 동 규칙 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하고 있으며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 UR E26 적용 실무에서 특정 CBS를 대상에서 제외하려는 시도가 반복적으로 관찰된 데에서 출발한다. 다만 본 논문은 그러한 관찰을 주장의 근거로 삼지 않으며, 규칙 조문을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. **UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가?** 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 제외 기준을 발효 전 철회된 2022년판[5] 및 시스템 범주를 정의한 UR E22[2]와 대조 분석하였다. 본 논문의 기여는 다음 세 가지이다.

1. UR E26 6.4의 제외 기준을 제정 과정과 대조하여, 사고 전이(propagation)에 관한 조건이 최종안에서 제외되었음을 확인하였다.

본 논문의 구성은 다음과 같다. II장에서 선행연구를 정리하고, III장에서 제외 기준을 분석한다. IV장에서 분석의 귀결로서 잔여 위협의 예시를 제시하고, V장에서 결론을 기술한다.

---

## II. 관련 연구 및 배경

### 2.1 IACS 사이버 복원력 규칙 체계 => 서론에 포함

IACS의 사이버 복원력 관련 통일규칙은 세 축으로 구성된다. UR E22[2]는 소프트웨어에 의존하여 기능을 수행하는 컴퓨터기반시스템의 설계·건조·시운전·유지보수 요구사항을 규정하며, 시스템 범주(Category)를 정의한다. UR E26[1]은 선박을 하나의 집합체로 보아 선박 수준의 사이버 복원력을 다루고, UR E27[6]은 개별 시스템 및 장비의 보안 능력을 다룬다. 세 규칙은 상호 참조 구조를 이루며, 이와 별도로 IACS Rec.166, 171, 190이 비강제 권고로 제공된다.

UR E26의 적용 대상은 물리 프로세스를 제어·감시하는 OT 시스템으로, 추진, 조타, 양묘 및 계류, 발전 및 배전, 화재탐지 및 소화, 빌지·밸러스트, 수밀 및 침수탐지, 조명, 그리고 비상정지·화물안전·가스탐지 등 안전 관련 시스템이 명시되어 있다. 여기에 법정 요건이 요구하는 항해 시스템과 내·외부 통신 시스템이 추가되며, 적용 대상 CBS로부터 다른 시스템으로 향하는 **IP 기반 통신 인터페이스** 역시 범위에 포함된다.

### 2.2 선행연구와 공백 => II. 를 관련 연구로 바꿔서 

선박 사이버보안에 대한 위협 분석 연구는 꾸준히 축적되어 왔다. 조용현과 차영균[3]은 선박 시스템에 접근하는 이해관계자를 고려한 데이터 흐름도를 수립하고 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였다. 이후 동 연구진의 일부가 참여한 연구에서는 MITRE ATT&CK 프레임워크를 선박 장비에 적용하여 공격 모델을 제시하였다[7].

UR E26 자체를 대상으로 한 연구도 축적되고 있다. 사이버 복원력의 정의를 조사하고 UR E26을 NIST의 사이버보안 프레임워크 및 사이버 복원력 체계와 비교한 연구[8], UR E26의 요구사항과 IEC 62443 참조 모델을 함께 고려하여 선박 네트워크 토폴로지를 설계한 연구[9], 동 규칙의 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[10]가 있다. 국외에서는 동 규칙의 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[11]가 발표되었다.

그러나 이들 연구는 공통적으로 **규칙을 어떻게 준수할 것인가**, 또는 **규칙이 다른 프레임워크와 어떻게 다른가**를 다룬다. 제외에 관하여는 제출·유지하여야 하는 위험평가 문서의 하나로 언급되거나[10], 규칙의 구성을 소개하는 과정에서 부속 절차로 언급되는[11] 데 그친다. 규칙이 명시적으로 허용하고 있는 **제외의 판정 기준 자체를 분석 대상으로 삼은 연구는 확인되지 않는다.** 본 논문은 이 지점을 다룬다.

---

## III. UR E26 제외 제도 분석

### 3.1 제외 기준의 구성

UR E26 6.1은 적용 대상 CBS를 요구사항 적용에서 제외하는 경우 위험평가를 수행하고, 제외된 CBS에 관련된 위험수준이 수용 가능함을 입증하는 자료를 제시하도록 규정한다. 구체적인 수용 기준은 6.4에 제시되어 있으며, 반드시 충족하여야 하는 기준(shall be met) 4개와 위험수준 평가 시 고려되어야 하는 추가 기준(should be considered) 3개로 구성된다. 본 논문에서는 전자를 필수 기준, 후자를 추가 기준이라 한다.

**표 1. UR E26 6.4의 제외 기준 (원문)**

| 구분 | Criteria |
|---|---|
| 필수 C-a | The CBS shall be isolated (i.e, have no IP-network connections to other systems or networks) |
| 필수 C-b | The CBS shall have no accessible physical interface ports. Unused interfaces shall be logically disabled. It shall not be possible to connect unauthorised devices to the CBS |
| 필수 C-c | The CBS must be located in areas to which physical access is controlled |
| 필수 C-d | The CBS shall not be an integrated control system serving multiple ship functions as specified in the scope of applicability of this UR |
| 추가 A-a | The CBS should not serve ship functions of category III |
| 추가 A-b | Known vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment |
| 추가 A-c | The attack surface for the CBS is minimized, having considered its complexity, connectivity, physical and logical access points, including wireless access points |

※ 필수 기준은 "The following criteria **shall be met** to exclude a system from the scope of applicability of this UR", 추가 기준은 "The following additional criteria **should be considered** for the evaluation of risk level acceptability"에 해당한다.

이 기준에는 두 가지 재량 요소가 있다. 첫째, 6.4는 추가 기준을 완전히 충족하지 못하는 CBS라 하더라도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"인 경우 제외를 수용할 수 있도록 규정한다. 둘째, 필수 기준에 사용된 "accessible", "logically disabled", "physical access is controlled", "minimized" 등의 표현에 대하여 판정 기준이나 검증 방법이 규칙에 제시되어 있지 않다. 위험평가의 방법론 역시 지정되어 있지 않았다.

### 3.2 제외의 실질적 효과

제외가 승인된 CBS에는 UR E26 4장의 요구사항이 적용되지 않는다. 4장은 선박 자산 목록(4.1.1), 보안 구역 및 네트워크 분할(4.2.1), 네트워크 보호 대책(4.2.2), 악성코드 대응(4.2.3), 접근 통제(4.2.4), 무선 통신(4.2.5), 원격 접속 통제(4.2.6), 이동식 장치 사용(4.2.7), 네트워크 운영 감시(4.3.1), 검증 및 진단 기능(4.3.2), 사고 대응 계획(4.4.1), 국부·수동 운전(4.4.2), 네트워크 격리(4.4.3)로 구성된다.

여기서 주목할 점은, 4.3.1의 네트워크 운영 감시 대상에서 빠지므로 **침해가 발생하여도 이를 탐지할 수단이 확보되지 않으며**, 4.4.1의 사고 대응 계획에서 빠지므로 **사고 발생 시 처리 절차가 마련되지 않는다.** 즉 제외는 식별·보호·탐지·대응의 전 단계에 걸친 소거로 작용한다.

### 3.3 전이 검증 조건의 부재

UR E26의 2022년판[5]은 6.4의 기준을 a)부터 l)까지 12개 항목으로 규정하고, 이를 모두 "The following criteria shall be considered for the evaluation of risk level acceptability"로 두었다. Rev.1에서는 이것이 필수 기준 4개와 추가 기준 3개로 재편되었다. 두 판본의 대조 결과는 표 2와 같다.

**표 2. 제외 기준의 제정 과정 대조 (2022년판 원문 기준)**

| 2022년판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
|---|---|
| f) **The connections of CBS to other CBSs have been duly investigated, understood and documented.** In particular, the CBS shall not be connected to other CBSs or devices by IP-based networks | 뒷문장만 필수 C-a로 승격. **앞문장 미반영** |
| g) The CBS shall not have available physical interfaces that can be used by uncontrolled/unsecure removable devices | 필수 C-b로 승격 (문구 구체화) |
| e) The CBS must be located in areas using controlled access | 필수 C-c로 승격 |
| d) The CBS must not serve **essential services** or multiple ship services | 필수 C-d로 승격. 단 금지 대상이 **통합제어시스템으로 한정** |
| a) **Foreseeable** vulnerabilities, threats, potential impacts ... duly considered in the risk assessment | 추가 A-b로 유지 (Foreseeable → **Known**) |
| b) The attack surface for the CBS is minimized ... | 추가 A-c로 유지 (자구 동일) |
| **c) The CBS, considered in its function and role in the integrated system it is part of, cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices** | **미반영** |
| h)~l) 소프트웨어 식별, 유지보수 정책, 기능 무결성 확인 수단, 국부 수동 조작 인터페이스, 사고 대응·복구 계획상의 취급 지침 | 미반영 |
| — | 추가 A-a (should not serve ship functions of category III) 신설 |

이 대조에서 확인되는 것은 **일방적 완화가 아니다.** 세 방향의 변경이 함께 나타난다.

첫째, **강화된 부분이 있다.** 2022년판의 d)~g)에 해당하는 항목은 고려 사항에서 필수 충족 사항으로 승격되었고, g)는 "unused interfaces shall be logically disabled" 등 판정 문구가 구체화되었다. 또한 기준을 완전히 충족하지 못하는 경우에도 합리적 설명으로 제외를 수용할 수 있도록 한 재량 조항의 적용 범위가, 2022년판의 a)~l) 전체에서 Rev.1의 추가 기준 3개로 **축소**되었다.

둘째, **전이와 관련된 두 조건이 최종안에 반영되지 않았다.** 하나는 c) 항목으로, 제외 대상 CBS가 다른 시스템으로부터 사고의 영향을 받거나("cannot be affected by cyber incidents vectored by other CBSs or network devices") 다른 시스템으로 영향을 전파하지("nor it can propagate the effect of a cyber incident to other CBSs or network devices") 않을 것을 요구한 유일한 조항이었다. 다른 하나는 f) 항목의 앞 문장으로, CBS와 다른 CBS 사이의 연결이 "duly investigated, understood and documented"될 것을 요구하였다. Rev.1의 C-a는 f)의 뒷 문장인 IP 연결 부재만을 승계하였다. 즉 **전이의 결과를 판정하는 조건과 그 판정의 전제가 되는 연결 관계 파악 요구가 함께 사라졌다.**

다만 2022년판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 **제정 과정에서 최종안에 반영되지 않은 것**으로 이해하여야 한다. IACS는 각 항목의 변경 사유를 공개한 바 없으므로, 본 논문은 변경의 의도를 추정하지 않으며 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.
### 3.4 논의의 범위 => 필요없으면 삭제

한편 6.4의 명시적 제외와 별개로, UR E26의 적용 범위가 물리 프로세스를 제어·감시하는 OT 시스템을 중심으로 정의됨에 따라 통상 IT로 분류되는 구성요소가 판단에서 벗어나는 경로가 존재한다. 이는 개별 CBS를 요구사항 적용에서 배제하는 6.4와 층위를 달리하는 문제이므로 본 논문에서는 다루지 않으며, 별고에서 논한다.

---

## IV. 잔여 위협의 예시

본 장에서는 III장에서 확인한 한계가 어떤 위협으로 남는지를 두 가지 예시로 제시한다. 본 논문은 체계적인 위협 도출을 목적으로 하지 않으며, 각 예시는 앞선 분석의 귀결을 보이는 범위에 한정한다. 각 위협에 대응하는 공격 기법은 MITRE ATT&CK for ICS[12]의 기법 식별자로 표기한다.

### 4.1 시리얼 통신 경로

필수 기준 C-a는 격리를 "have no IP-network connections to other systems or networks"로 정의한다. 즉 IP 네트워크 연결의 부재만을 요구하며, 시리얼 통신에 의한 연결은 제한하지 않는다.

주목할 점은 UR E26이 시리얼 통신의 존재를 인지하고 있다는 것이다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, **simplex serial links**, TCP/IP diodes, dry contacts"를 들고 있으며, 4.2.1.4.1은 비신뢰 네트워크와의 통신에 관한 기술서가 "discrete signals, **serial communication**, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"을 포함하여야 한다고 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도, 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

시리얼 통신이 안전하다는 인식은 이 분야에 국한된 것이 아니며, 이미 실험적으로 반박된 바 있다. 장지웅과 김휘강[13]은 전력 제어시스템에서 사용되는 시리얼 기반 DNP3.0 통신이 아날로그 구간에서의 공격 불가, **"시리얼 방식의 내재적 보안성"**, Master만이 통신을 개시하는 프로토콜 특성을 이유로 안전하다고 알려져 왔음을 지적하고, 상용 시뮬레이터로 구성한 환경에서 **시리얼 구간을 탭핑(tapping)하여 기밀성·무결성·가용성 세 측면 모두에서 취약점을 확인**하였다. 구체적으로 암호화 부재로 인해 별도의 복호화 없이 패킷 내용이 노출되었고, 명령과 응답의 변조 및 Slave 스푸핑이 가능하였으며, 유효성 검사가 없는 패킷 주입으로 버퍼 오버플로가 발생하였다.

선박 환경에서도 시리얼 구간은 IP 영역과 완전히 분리되어 있지 않다. 최근 보고[14]는 시리얼-IP 변환장치에 대한 분석에서 신규 취약점 20건을 식별하고, 변환장치가 침해될 경우 시리얼 통신이 양방향으로 변조될 수 있음을 실험으로 제시하였으며, 그 배경으로 시리얼 프로토콜이 인증이나 암호화를 갖추지 않은 경우가 많다는 점을 지적한다. 동 보고는 이러한 변환장치의 적용 사례로 추진 및 조타 계통과 전자해도표시정보시스템(ECDIS)을 포함한 선박 시스템을 명시하고 있다.

또한 선박은 알람을 감시하기 위해 AMS(Serial 통신을 통해 연결된 System으로부터 알람을 받아 모으는 장치)가 탑재되어 있으며, 이는 시리얼 구간에서 스푸핑이 발생할 수 있으며, ICMS로 발전될 시 변환 장치를 통해 오정보를 통해 연결된 핵심 시스템이 영향(오작동)을 받을 수 있다
-> 추가 했으면 좋겠다 생각한 내용
=> 위을 내용을 그림(간단한 토폴로지로 표현하면 좋을 듯, 필요한 조합을 말하면 거기에 맞춰 그려보겠음)

따라서 IP 연결이 없다는 사실만으로 해당 CBS가 외부 조작으로부터 분리되어 있다고 보기는 어렵다.

### 4.2 시스템 범주를 경유한 전이

추가 기준 A-a는 제외 대상 CBS가 Category III 기능을 담당하지 않을 것을 요구한다. 따라서 Category I 또는 II로 분류된 시스템은 이 기준을 충족한다.

그러나 3.4에서 확인하였듯 이 범주는 고장 결과를 기준으로 정의된 것이다. 감시·정보·관리 기능을 담당하여 Category I로 분류된 시스템이라 하더라도, 상위 범주 시스템에 데이터를 공급하거나 동일한 물리적·논리적 경로를 공유하는 경우 공격의 경유 지점이 될 수 있다. UR E22 3.2가 저범주 시스템이 상위 범주 시스템의 운영에 영향을 주지 않을 것을 언급하고 있음에도, 이를 확인하는 절차는 UR E22와 UR E26 어느 쪽에도 제시되어 있지 않다. 3.3에서 확인한 두 조건, 즉 전이 여부의 판정과 연결 관계의 파악이 최종안에 반영되었다면 제외 판정 단계에서 이 확인이 이루어질 수 있었을 것이다.

**표 4. 잔여 위협 예시와 대응 공격 기법**

| 관련 조항 | 잔여 위협 | ATT&CK for ICS |
|---|---|---|
| 6.4 C-a | IP 연결이 없어도 시리얼 경로를 통한 메시지 주입·변조 및 통신 차단이 가능 | T1692 Unauthorized Message (.001 Command, .002 Reporting), T1695.001 Block Communications: Serial COM, T0830 Adversary-in-the-Middle |
| 6.4 A-a | 저범주로 분류되어 제외된 CBS가 상위 범주 CBS로 향하는 경유 지점이 됨 | T0867 Lateral Tool Transfer, T0859 Valid Accounts, T0832 Manipulation of View |

두 예시에 공통되는 것은, 해당 CBS가 제외됨으로써 4.1.1의 자산 목록과 4.3.1의 네트워크 운영 감시 대상에서도 함께 빠진다는 점이다. 즉 위 경로를 통한 침해가 발생하더라도 이를 인지할 수단이 확보되어 있지 않다.

---

## V. 결론

본 논문은 "UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가"라는 질문에 대하여, 규칙 조문의 대조 분석을 통해 세 가지 한계를 제시하였다.

첫째, 2022년판에 존재하던 전이 관련 두 조건 — 사고의 전이·전파 여부에 관한 판정 조건과 CBS 간 연결 관계의 조사·문서화 요구 — 이 최종안에 반영되지 않아, 제외된 CBS가 다른 시스템에 미치는 영향을 판정 단계에서 확인하는 절차가 존재하지 않는다. 둘째, 제외 판정에 차용된 UR E22의 시스템 범주는 고장 결과를 기준으로 정의되어 있어, 의도를 가진 공격자를 상정하는 보안 판정의 기준으로는 정합하지 않는다. 셋째, 제외에 수반되는 문서 부담과 제외되지 않는 경우의 문서 부담 사이에 비대칭이 존재하며, 이는 규칙의 문서 요구 구조에서 발생한다.

이에 따라 본 논문은 문제는 판정 기준의 불확정성과 전이 검증의 부재에 있음을 확인했다.

본 논문은 규칙 문헌의 분석에 기초하며, 실선 환경에서의 실증을 포함하지 않는다. 또한 선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다.

---
## 참고문헌

- [1] IACS, *UR E26 Cyber resilience of ships*, Rev.1, Nov. 2023.
- [2] IACS, *UR E22 Computer based systems*, Rev.3 Corr.1, Sep. 2025.
- [3] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019. DOI: 10.13089/JKIISC.2019.29.3.657
- [4] BIMCO, ICS, INTERCARGO, INTERTANKO, OCIMF *et al.*, *The Guidelines on Cyber Security Onboard Ships*, Version 5, 2024.
- [5] IACS, *UR E26 Cyber resilience of ships*, Apr. 2022 (withdrawn before entry into force on 1 Jan. 2024, see [1] Note 1). — 원문 `rules/ur-e26-new-apr-2022.pdf` 보관. 6장 pp. 25-27 of 32
- [6] IACS, *UR E27 Cyber resilience of on-board systems and equipment*, Rev.1, Sep. 2023.
- [7] Y. Jo, O. Choi, J. You, Y. Cha, and D. H. Lee, "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," *Sensors*, vol. 22, no. 5, art. no. 1860, 2022. DOI: 10.3390/s22051860
- [8] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024. DOI: 10.13089/JKIISC.2024.34.5.1149
- [9] 손금준, 최상훈, 강남선, 김성록, "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회논문집, 제61권, 제6호, pp. 427-436, 2024. DOI: 10.3744/SNAK.2024.61.6.427
- [10] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024. DOI: 10.12673/jant.2024.28.1.27
- [11] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," *Turkish Journal of Maritime and Marine Sciences*, vol. 10, Special Issue 1, pp. 31-50, 2024. DOI: 10.52998/trjmms.1531150
- [12] MITRE, *ATT&CK for ICS*, v19.2. [Online]. Available: https://attack.mitre.org/matrices/ics/ (accessed Aug. 14, 2026).
- [13] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013. DOI: 10.13089/JKIISC.2013.23.6.1143
- [14] Forescout Technologies, *BRIDGE BREAK: New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters*, 2026.
---

## 집필 메모(수정 필요 메모)
=> 학술 대회용이기에 아이디어 수준을 반영(또한 학회의 성격 반영)
1. IACS의 불확정성적인 규정으로 인해 많은 선급에서 참고하는 BIMCO guideline은 정성적인 평가가 대다수로 이게 문제점중 하나로 봄 => 이게 나의 문제 제시 중 하나였음
2. 서론에다 연구배경(2의)이동하여 내용 재작성
3. 문서 제출 생각 X => 정보통신 학회의 사이버보안쪽으로 제출할 예정이므로
4. UR E22의 내용은 여기선 삭제, 원래 필요했던 이유는 OT에 중점되어 있고, IT쪽은 카테고리 I으로 분류되는 경우가 많은데 여기서 취약점으로 확인할려는 사항이 였음
5. 즉, 서론 내용 전적으로 수정 필요
6. 향후 연구 방향은 삭제 => 불완전한 논문으로 보일 수 있음
7. 4.1 시리얼 통신 밑에 그림.1로 통산적인 선박 네트워크 토폴로지 삽입
8. 4.1 내용을 선박의 시리얼 프로토콜(NMEA)의 취약점 역시 같은 취약점이 관찰되는 근거를 통해 취약점을 예상? 할 수 있다. 정도(end user로부터 스푸핑이 핵심 기기로 이어질 수 있음)
9. 2022년판 이라는 말보다는 Rev.1이전 확정되기전 초안? 등 쫌더 깔끔한 단어로 2022년판하니까 어색함
10. 학술대회인데, 제언한다.. 라는 말이 맞는지 생각듬(IACS의 규정은 해외 규정이기에)
11. '문제는 판정 기준의 불확정성과 전이 검증의 부재에 있다' 이 문장은 만족
12. 결론 쪽 방향을 '분석을 통한 한계를 2가지 예시의 잔여 위협으로 실제로 귀결될 수 있음을 확인했다.' 이쪽이 훨씬 목적성에 맞는거 같음
13. 추가할 자료 있으면 더 말해줘