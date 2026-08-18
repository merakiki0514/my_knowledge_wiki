# [학술대회 원고 초안 rev2] IACS UR E26 CBS 제외 기준의 한계 분석: 사고 전이 관점에서

투고처: 한국정보통신학회(KIICE) 종합학술대회 / 분량: 3쪽
작성: 2026-08-13 → 개정 2026-08-18 (집필 메모 1~12 반영 + 원문 대조 검증)
선행본: `outputs/2026-08-18_conference-paper_draft_revision.md` (사용자 수정 방향 메모본)

## 조판 양식

| 요소 | 크기 | 단 구성 |
|---|---|---|
| 요약 (국문) | 9 pt | 1단 |
| ABSTRACT (영문) | 8 pt | 1단 |
| 키워드 / Key words | 8 pt | 1단 |
| 본문 (I. 서론 이후 전체) | 10 pt | 2단 |

→ 제목·저자·요약·초록·키워드까지는 1단, I. 서론부터 2단 편집.
→ 표 2(제정 과정 대조)는 항목이 길어 단 전체 폭(1단 걸침) 배치를 검토할 것.

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

IACS UR E26은 선박의 사이버 복원력에 관한 통일규칙으로, 기존의 비강제 가이드라인과 달리 설계부터 운항까지 전 생애주기에 걸친 강제 요구사항을 제시한다. 그러나 동 규칙 6.4는 특정 컴퓨터기반시스템(CBS)을 적용 범위에서 제외할 수 있는 경로를 함께 규정하고 있다. 본 논문은 UR E26 Rev.1의 제외 기준을 발효 전 철회된 초판과 대조 분석하여 두 가지 한계를 제시한다. 첫째, 초판에 존재하던 사고 전이(propagation)에 관한 판정 조건과 CBS 간 연결 관계의 조사·문서화 요구가 최종안에 반영되지 않아, 제외된 CBS가 다른 CBS에 미치는 영향을 확인할 절차가 부재하다. 둘째, 필수 기준에 사용된 표현에 판정 기준과 검증 방법이 제시되어 있지 않아 제외 판정이 불확정적이다. 이어 본 논문은 이 두 한계가 시리얼 통신 경로와 시스템 범주를 경유한 전이라는 두 가지 잔여 위협으로 실제로 귀결될 수 있음을 확인한다. 본 논문은 제외 제도 자체의 폐지가 아니라, 전이 검증 조건의 복원과 판정 기준의 구체화가 필요함을 지적한다.

**핵심어**: 선박 사이버보안, IACS UR E26, 컴퓨터기반시스템, 사고 전이, 사이버 복원력

---

## ABSTRACT

IACS UR E26 is a unified requirement for the cyber resilience of ships. Unlike earlier non-mandatory guidelines, it imposes mandatory requirements across the entire lifecycle from design to operation. However, Section 6.4 of the same requirement also provides a pathway to exclude certain Computer Based Systems (CBS) from its scope of applicability. This paper analyzes the exclusion criteria of UR E26 Rev.1 against the withdrawn first edition and presents two limitations. First, the condition concerning cyber incident propagation and the requirement that connections between CBSs be duly investigated and documented, both present in the first edition, were not carried into the final text, leaving no procedure to verify the effect of an excluded CBS on other systems. Second, no assessment threshold or verification method is given for the terms used in the mandatory criteria, which leaves the exclusion assessment indeterminate. This paper then shows that these two limitations can materialize as two residual threats: message injection over serial communication paths, and propagation by way of the system categories. This paper argues not for the abolition of the exclusion scheme, but for the restoration of propagation verification and the specification of verifiable assessment criteria.

**Key words**: Ship Cyber Security, IACS UR E26, Computer Based System, Incident Propagation, Cyber Resilience

---

## I. 서 론

선박은 오랫동안 육상과 분리된 폐쇄 환경으로 간주되어 왔으나, 정보통신기술의 발전과 선내 장비의 네트워크화가 진행되면서 그 전제는 더 이상 성립하지 않는다. 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서, 선박은 IT와 OT가 혼재하는 복합 환경이 되었다. 이러한 변화는 사이버 위협의 유입 경로를 동시에 확대하였으며, 선박을 대상으로 한 위협 분석 연구가 이어져 왔다[3].

제도적 대응은 비강제 가이드라인에서 출발하였다. BIMCO 등이 발간한 지침[4]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였고, 위험도 판정을 정성적 평가에 의존하여 동일한 시스템에 대하여도 평가 주체에 따라 결과가 달라질 여지를 남겼다. 국제선급연합회(IACS)가 제정한 통일규칙 UR E26[1]은 이 지점에서 분명한 진전이다. 동 규칙은 선박을 하나의 집합체로 보아 사이버 복원력 요구사항을 제시하며, 식별(Identify)·보호(Protect)·탐지(Detect)·대응(Respond)·복구(Recover)의 기능 요소별로 요구사항을 구성하고 설계·건조·시운전·운항의 전 생애주기에 걸쳐 이행을 요구한다. IACS의 사이버 복원력 규칙 체계는 세 축으로 이루어지는데, UR E22[2]는 소프트웨어에 의존하는 컴퓨터기반시스템(CBS)의 요구사항과 시스템 범주(Category)를 정의하고, UR E26[1]은 선박 수준의 복원력을, UR E27[6]은 개별 시스템 및 장비의 보안 능력을 다룬다.

UR E26의 적용 대상은 물리 프로세스를 제어·감시하는 OT 시스템으로, 추진·조타·발전 및 배전·화재탐지·빌지 및 밸러스트 등 안전 관련 시스템과 법정 요건이 요구하는 항해·통신 시스템이 명시되어 있으며, 적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스 역시 범위에 포함된다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 **제외**할 수 있는 경로를 함께 제도화하였다. 동 규칙 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하고 있으며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 UR E26 적용 실무에서 특정 CBS를 대상에서 제외하려는 시도가 반복적으로 관찰된 데에서 출발한다. 다만 본 논문은 그러한 관찰을 주장의 근거로 삼지 않으며, 규칙 조문을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. **UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가?** 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 제외 기준을 발효 전 철회된 초판[5]과 대조 분석하였다. 본 논문의 기여는 다음 두 가지이다.

1. UR E26 6.4의 제외 기준을 제정 과정과 대조하여, 사고 전이(propagation)에 관한 판정 조건과 그 전제가 되는 연결 관계 파악 요구가 최종안에 반영되지 않았음을 확인하였다.
2. 이 조건의 부재와 판정 기준의 불확정성이 결합할 때 남는 잔여 위협을 두 가지 예시로 제시하고, 각각을 MITRE ATT&CK for ICS의 공격 기법에 대응시켰다.

본 논문의 구성은 다음과 같다. II장에서 선행연구를 정리하고, III장에서 제외 기준을 분석한다. IV장에서 분석의 귀결로서 잔여 위협의 예시를 제시하고, V장에서 결론을 기술한다.

---

## II. 관련 연구

선박 사이버보안에 대한 위협 분석 연구는 꾸준히 축적되어 왔다. 조용현과 차영균[3]은 선박 시스템에 접근하는 이해관계자를 고려한 데이터 흐름도를 수립하고 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였으며, 대상 기기는 IEC 61162-450/460 기반 기기 목록에서 선정하였다. 이후 동 연구진의 일부가 참여한 연구에서는 MITRE ATT&CK 프레임워크를 선박 장비에 적용하여 공격 모델을 제시하였다[7].

UR E26 자체를 대상으로 한 연구도 축적되고 있다. 사이버 복원력의 정의를 조사하고 UR E26을 NIST의 사이버보안 프레임워크 및 사이버 복원력 체계와 비교한 연구[8], UR E26의 요구사항과 IEC 62443 참조 모델을 함께 고려하여 선박 네트워크 토폴로지를 설계한 연구[9], 동 규칙의 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[10]가 있다. 국외에서는 동 규칙의 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[11]가 발표되었다.

그러나 이들 연구는 공통적으로 **규칙을 어떻게 준수할 것인가**, 또는 **규칙이 다른 프레임워크와 어떻게 다른가**를 다룬다. 제외에 관하여는 제출·유지하여야 하는 위험평가 문서의 하나로 언급되거나[10], 규칙의 구성을 소개하는 과정에서 부속 절차로 언급되는[11] 데 그친다. 규칙이 명시적으로 허용하고 있는 **제외의 판정 기준 자체를 분석 대상으로 삼은 연구는 확인되지 않는다.** 본 논문은 이 지점을 다룬다.

---

## III. UR E26 제외 제도 분석

### 3.1 제외 기준의 구성과 판정의 불확정성

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

이 기준에는 두 가지 재량 요소가 있다. 첫째, 6.4는 추가 기준을 완전히 충족하지 못하는 CBS라 하더라도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"인 경우 제외를 수용할 수 있도록 규정한다. 둘째, 필수 기준에 사용된 "accessible", "logically disabled", "physical access is controlled", "minimized" 등의 표현에 대하여 판정 기준이나 검증 방법이 규칙에 제시되어 있지 않으며, 6.1이 요구하는 위험평가의 방법론 역시 지정되어 있지 않다. 즉 제외 판정의 결과는 평가 주체에 따라 달라질 수 있다.

### 3.2 제외의 실질적 효과

제외가 승인된 CBS에는 UR E26 4장의 요구사항이 적용되지 않는다. 4장은 선박 자산 목록(4.1.1), 보안 구역 및 네트워크 분할(4.2.1), 네트워크 보호 대책(4.2.2), 악성코드 대응(4.2.3), 접근 통제(4.2.4), 무선 통신(4.2.5), 원격 접속 통제(4.2.6), 이동식 장치 사용(4.2.7), 네트워크 운영 감시(4.3.1), 검증 및 진단 기능(4.3.2), 사고 대응 계획(4.4.1), 국부·수동 운전(4.4.2), 네트워크 격리(4.4.3), 최소위험상태로의 축퇴(4.4.4), 복구 계획(4.5.1), 백업 및 복원 능력(4.5.2), 통제된 정지·재시작(4.5.3)으로 구성된다.

여기서 주목할 점은, 4.1.1의 자산 목록에서 빠지므로 **해당 CBS는 선박 자산으로 관리되지 않으며**, 4.3.1의 네트워크 운영 감시 대상에서 빠지므로 **침해가 발생하여도 이를 탐지할 수단이 확보되지 않고**, 4.4.1의 사고 대응 계획과 4.5.1의 복구 계획에서 빠지므로 **사고 발생 시 처리·복구 절차가 마련되지 않는다.** 즉 제외는 식별·보호·탐지·대응·복구의 전 기능 요소에 걸친 소거로 작용한다. 자산 목록에 관한 IACS 권고 Rec.190[16]은 제외된 CBS를 목록에 표기할 것을 권장하나, 해당 항목은 권고 내에서도 "(recommended)"로 표시되어 있다.

### 3.3 전이 검증 조건의 부재

UR E26의 초판[5]은 6.4의 기준을 a)부터 l)까지 12개 항목으로 규정하고, 이를 모두 "The following criteria shall be considered for the evaluation of risk level acceptability"로 두었다. Rev.1에서는 이것이 필수 기준 4개와 추가 기준 3개로 재편되었다. 두 판본의 대조 결과는 표 2와 같다.

**표 2. 제외 기준의 제정 과정 대조 (초판 원문 기준)**

| 초판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
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

첫째, **강화된 부분이 있다.** 초판의 d)~g)에 해당하는 항목은 고려 사항에서 필수 충족 사항으로 승격되었고, g)는 "unused interfaces shall be logically disabled" 등 판정 문구가 구체화되었다. 또한 기준을 완전히 충족하지 못하는 경우에도 합리적 설명으로 제외를 수용할 수 있도록 한 재량 조항의 적용 범위가, 초판의 a)~l) 전체에서 Rev.1의 추가 기준 3개로 **축소**되었다.

둘째, **전이와 관련된 두 조건이 최종안에 반영되지 않았다.** 하나는 c) 항목으로, 제외 대상 CBS가 다른 시스템으로부터 사고의 영향을 받거나("cannot be affected by cyber incidents vectored by other CBSs or network devices") 다른 시스템으로 영향을 전파하지("nor it can propagate the effect of a cyber incident to other CBSs or network devices") 않을 것을 요구한 유일한 조항이었다. 다른 하나는 f) 항목의 앞 문장으로, CBS와 다른 CBS 사이의 연결이 "duly investigated, understood and documented"될 것을 요구하였다. Rev.1의 C-a는 f)의 뒷 문장인 IP 연결 부재만을 승계하였다. 즉 **전이의 결과를 판정하는 조건과 그 판정의 전제가 되는 연결 관계 파악 요구가 함께 사라졌다.** 연결 관계의 식별은 Rev.1 이후 발간된 Rec.190[16]에서 자산 목록의 한 항목("to determine that all connections have been identified")으로 다시 나타나지만, 이 역시 비강제 권고의 권장 항목이며 제외 판정의 조건은 아니다.

셋째, C-d의 금지 대상이 좁아졌다. 초판 d)는 "essential services 또는 multiple ship services"를 담당하는 CBS를 대상으로 하였으나 Rev.1 C-d는 통합제어시스템으로 한정되므로, 필수 서비스를 담당하는 단일 기능 CBS는 더 이상 이 항목에 걸리지 않는다. Category III 담당 여부를 다루는 A-a는 필수가 아닌 고려 사항이다.

다만 초판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 **제정 과정에서 최종안에 반영되지 않은 것**으로 이해하여야 한다. IACS는 각 항목의 변경 사유를 공개한 바 없으므로, 본 논문은 변경의 의도를 추정하지 않으며 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.

---

## IV. 잔여 위협의 예시

본 장에서는 III장에서 확인한 한계가 어떤 위협으로 남는지를 두 가지 예시로 제시한다. 본 논문은 체계적인 위협 도출을 목적으로 하지 않으며, 각 예시는 앞선 분석의 귀결을 보이는 범위에 한정한다. 각 위협에 대응하는 공격 기법은 MITRE ATT&CK for ICS[12]의 기법 식별자로 표기한다.

### 4.1 시리얼 통신 경로

필수 기준 C-a는 격리를 "have no IP-network connections to other systems or networks"로 정의한다. 즉 IP 네트워크 연결의 부재만을 요구하며, 시리얼 통신에 의한 연결은 제한하지 않는다.

주목할 점은 UR E26이 시리얼 통신의 존재를 인지하고 있다는 것이다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, **simplex serial links**, TCP/IP diodes, dry contacts"를 들고 있으며, 4.2.1.4.1은 비신뢰 네트워크와의 통신에 관한 기술서가 "discrete signals, **serial communication**, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"을 포함하여야 한다고 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도, 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

**[그림 1] 삽입 위치 — 시리얼 경로를 경유한 전이 (도면 명세는 문서 말미 '그림 1 작도 명세' 참조)**

시리얼 통신이 안전하다는 인식은 이 분야에 국한된 것이 아니며, 이미 실험적으로 반박된 바 있다. 장지웅과 김휘강[13]은 전력 제어시스템에서 사용되는 시리얼 기반 DNP3.0 통신이 아날로그 구간에서의 공격 불가, "시리얼 방식의 내재적 보안성", Master만이 통신을 개시하는 프로토콜 특성을 이유로 안전하다고 알려져 왔음을 지적하고, 상용 시뮬레이터로 구성한 환경에서 **시리얼 구간을 탭핑(tapping)하여 기밀성·무결성·가용성 세 측면 모두에서 취약점을 확인**하였다. 패킷 내용이 평문으로 노출되었고, 명령·응답의 변조와 Slave 스푸핑이 가능하였으며, 유효성 검사가 없는 패킷 주입으로 버퍼 오버플로가 발생하였다.

선박 환경의 시리얼 프로토콜에서도 동일한 전제가 성립한다고 볼 근거가 있다. 선내 항해 장비의 데이터 교환 규격인 IEC 61162 계열에서, 보안 요구사항은 기본 규격이 아니라 별도의 add-on 표준인 IEC 61162-460[15]에 규정되어 있으며, 동 표준은 스스로를 "an add-on to IEC 61162-450 where higher safety and security standards are needed"로 정의한다. UR E26 1.3.2 역시 항해 및 무선통신 시스템에 대하여 IEC 61162-460 또는 동등 표준의 적용을 UR E27 4장의 보안 능력 요구를 대신하여 수용할 수 있다고 규정한다. 즉 보안 기능은 기본 규격에 내재된 것이 아니라 선택적으로 추가되는 계층이며, 이를 적용하지 않은 선내 시리얼 구간은 인증·무결성 검증 수단을 갖지 않는다고 보는 것이 타당하다.

선박 환경에서 시리얼 구간은 IP 영역과 완전히 분리되어 있지도 않다. 최근 기술보고서[14]는 시리얼-IP 변환장치에 대한 분석에서 신규 취약점 20건을 식별하고, 변환장치가 침해될 경우 시리얼 통신이 양방향으로 변조될 수 있음을 실험으로 제시하였으며, 그 배경으로 시리얼 프로토콜이 인증이나 암호화를 갖추지 않은 경우가 많다는 점을 지적한다. 동 보고서는 이러한 변환장치의 적용 사례로 추진 및 조타 계통과 전자해도표시정보시스템(ECDIS)을 포함한 선박 시스템을 명시하고 있다.

이를 선박의 알람 감시 구조에 적용하면 다음과 같은 경로를 상정할 수 있다. 선박에는 각 기기로부터 시리얼 통신으로 알람 신호를 수집하는 경보감시시스템(AMS)이 탑재된다. AMS에 신호를 공급하는 말단 기기가 C-a를 충족하여 제외될 경우, 해당 시리얼 구간에 대한 스푸핑을 통해 AMS에 허위 알람 또는 알람 누락을 발생시킬 수 있다. 나아가 AMS가 통합제어감시시스템(ICMS)으로 통합되고 그 사이에 시리얼-IP 변환장치가 놓이는 구성에서는, 오염된 입력이 상위 제어 계통의 표시와 운용자 판단을 왜곡하는 경로가 형성된다. 이는 제외된 말단 기기가 자신은 제어 기능을 갖지 않으면서도 상위 시스템의 무결성 원천이 되는 경우에 해당한다.

따라서 IP 연결이 없다는 사실만으로 해당 CBS가 외부 조작으로부터 분리되어 있다고 보기는 어렵다.

### 4.2 시스템 범주를 경유한 전이

추가 기준 A-a는 제외 대상 CBS가 Category III 기능을 담당하지 않을 것을 요구한다. 따라서 Category I 또는 II로 분류된 시스템은 이 기준을 충족한다.

그러나 이 범주는 보안을 기준으로 정의된 것이 아니다. UR E26 1.3.3은 "System categories are defined in IACS UR E22 on the basis of the consequences of a **system failure** to human safety, safety of the vessel and/or threat to the environment"라고 규정한다. 즉 범주는 우발적 고장의 안전 결과를 재는 척도이며, 의도를 가진 공격자를 상정하지 않는다. 고장의 영향은 해당 시스템의 기능적 중요도에 비례하는 경향이 있으나, 공격자는 최종 목표가 아닌 시스템을 경유 지점으로 선택한다. 감시·정보 기능을 담당하여 Category I로 분류된 시스템이라도 상위 범주 시스템에 데이터를 공급하거나 물리적·논리적 경로를 공유하면 경유 지점이 될 수 있다.

이 가능성은 규칙 자체에서도 부분적으로 인식되고 있다. UR E22[2] 3.2는 Category I 시스템이 통상 선급의 검증 대상이 아니라고 하면서도, 해당 시스템에 관한 정보가 "ensure that they do not influence the operation of systems in category II and category III"를 위하여 요구될 수 있다고 규정한다. 그러나 이를 확인하는 절차는 UR E22와 UR E26 어느 쪽에도 제시되어 있지 않다. 3.3에서 확인한 두 조건, 즉 전이 여부의 판정과 연결 관계의 파악이 최종안에 반영되었다면 제외 판정 단계에서 이 확인이 이루어질 수 있었을 것이다.

**표 3. 잔여 위협 예시와 대응 공격 기법**

| 관련 조항 | 잔여 위협 | ATT&CK for ICS |
|---|---|---|
| 6.4 C-a | IP 연결이 없어도 시리얼 경로를 통한 메시지 주입·변조 및 통신 차단이 가능 | T1692 Unauthorized Message (.001 Command, .002 Reporting), T1695.001 Block Communications: Serial COM, T0830 Adversary-in-the-Middle |
| 6.4 A-a | 저범주로 분류되어 제외된 CBS가 상위 범주 CBS로 향하는 경유 지점이 됨 | T0867 Lateral Tool Transfer, T0859 Valid Accounts, T0832 Manipulation of View |

두 예시에 공통되는 것은, 해당 CBS가 제외됨으로써 4.1.1의 자산 목록과 4.3.1의 네트워크 운영 감시 대상에서도 함께 빠진다는 점이다. 즉 위 경로를 통한 침해가 발생하더라도 이를 인지할 수단이 확보되어 있지 않다.

---

## V. 결론

본 논문은 "UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가"라는 질문에 대하여, 규칙 조문의 대조 분석을 통해 두 가지 한계를 제시하였다.

첫째, 초판에 존재하던 전이 관련 두 조건 — 사고의 전이·전파 여부에 관한 판정 조건과 CBS 간 연결 관계의 조사·문서화 요구 — 이 최종안에 반영되지 않아, 제외된 CBS가 다른 시스템에 미치는 영향을 판정 단계에서 확인하는 절차가 존재하지 않는다. 둘째, 필수 기준에 사용된 표현에 대한 판정 기준과 검증 방법, 그리고 위험평가의 방법론이 규칙에 제시되어 있지 않아 제외 판정이 불확정적이다.

이어 본 논문은 이 두 한계가 시리얼 통신 경로를 통한 메시지 주입·변조와 저범주 시스템을 경유한 전이라는 두 가지 잔여 위협으로 실제로 귀결될 수 있음을 확인하였다. 두 경우 모두 제외에 의하여 자산 목록과 감시 대상에서 함께 배제되므로 침해의 인지 수단이 남지 않는다.

본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, **문제는 판정 기준의 불확정성과 전이 검증의 부재에 있다.** 따라서 전이 검증 조건의 복원과 판정 표현의 구체화가 필요하다.

본 논문은 규칙 문헌의 분석에 기초하며, 실선 환경에서의 실증을 포함하지 않는다. 또한 선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다.

---

## 참고문헌

- [1] IACS, *UR E26 Cyber resilience of ships*, Rev.1, Nov. 2023.
- [2] IACS, *UR E22 Computer based systems*, Rev.3 Corr.1, Sep. 2025.
- [3] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019. DOI: 10.13089/JKIISC.2019.29.3.657
- [4] BIMCO, ICS, INTERCARGO, INTERTANKO, OCIMF *et al.*, *The Guidelines on Cyber Security Onboard Ships*, Version 5, 2024.
- [5] IACS, *UR E26 Cyber resilience of ships*, Apr. 2022 (withdrawn before entry into force on 1 Jan. 2024, see [1] Note 1).
- [6] IACS, *UR E27 Cyber resilience of on-board systems and equipment*, Rev.1, Sep. 2023.
- [7] Y. Jo, O. Choi, J. You, Y. Cha, and D. H. Lee, "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," *Sensors*, vol. 22, no. 5, art. no. 1860, 2022. DOI: 10.3390/s22051860
- [8] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024. DOI: 10.13089/JKIISC.2024.34.5.1149
- [9] 손금준, 최상훈, 강남선, 김성록, "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회논문집, 제61권, 제6호, pp. 427-436, 2024. DOI: 10.3744/SNAK.2024.61.6.427
- [10] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024. DOI: 10.12673/jant.2024.28.1.27
- [11] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," *Turkish Journal of Maritime and Marine Sciences*, vol. 10, Special Issue 1, pp. 31-50, 2024. DOI: 10.52998/trjmms.1531150
- [12] MITRE, *ATT&CK for ICS*, v19.2. [Online]. Available: https://attack.mitre.org/matrices/ics/ (accessed Aug. 14, 2026).
- [13] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013. DOI: 10.13089/JKIISC.2013.23.6.1143
- [14] Forescout Technologies, *BRIDGE BREAK: New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters*, 2026.
- [15] IEC, *IEC 61162-460: Maritime navigation and radiocommunication equipment and systems – Digital interfaces – Part 460: Multiple talkers and multiple listeners – Ethernet interconnection – Safety and security*, Edition 3.0, Apr. 2024.
- [16] IACS, *Rec.190 Recommendation for Vessel Asset Inventory for Computer-based Systems*, Jun. 2025.

---

## 그림 1 작도 명세 (집필 메모 7 대응)

**제목**: 그림 1. 제외된 CBS를 경유한 시리얼 전이 경로
**형식**: 흑백 선도, 2단 중 1단 폭. 상자·화살표만 사용(음영 최소).

**계층(위 → 아래)**

1. **육상**: RCC/원격지원 — 점선으로 위성링크(VSAT) 연결
2. **선내 IT 영역**: 업무망, 승무원 복지망 — E26 1.3.2 b)에 따라 *IP 인터페이스만* 범위임을 각주 라벨로 표시
3. **경계**: 방화벽/게이트웨이 상자
4. **선내 OT 영역 (E26 4장 적용)**: ICMS / AMS(경보감시) / ECDIS / 추진·조타 제어(Cat III)
5. **시리얼 영역**: 굵은 점선 박스. 내부에 말단 기기 3~4개(센서, 보조기기, 감시 전용 기기 — Cat I). RS-485 / NMEA 0183 라벨
6. **연결부**: 시리얼 영역과 OT IP망 사이에 **시리얼-IP 변환장치** 상자

**강조 요소**

- 말단 기기 중 1개를 **회색 점선 상자**로 표시하고 라벨: "6.4 C-a 충족 → 제외 / 4.1.1 자산목록·4.3.1 감시 대상 아님"
- 공격 경로 ①: 물리 접근 → 시리얼 구간 탭핑 → AMS 허위 알람 (라벨: T1692.002)
- 공격 경로 ②: IT 영역 침해 → 변환장치 장악 → 양방향 변조 → ICMS 표시 왜곡 (라벨: T0830, T0832)
- ①②가 모두 **회색 점선 상자를 통과**하도록 배치하여 "제외된 지점이 경로상에 있다"는 것이 그림만으로 읽히게 할 것

**캡션 초안**: "그림 1. IP 연결이 없어 제외 기준 C-a를 충족하는 말단 기기가 시리얼 구간과 변환장치를 경유하여 상위 시스템에 영향을 미치는 경로. 점선 상자는 UR E26 4장의 적용을 받지 않는 CBS."

---

## 검증 메모 (2026-08-18 원문 대조)

### 원문 대조로 확인한 사항 [규정]

| 본문 위치 | 대조 원문 | 결과 |
|---|---|---|
| 표 1 전체 | `rules/UR-E26-Rev.1-Nov-2023-CR.pdf` 6.4 (p.46-47 of 56) | 자구까지 일치 |
| 표 2 전체 | `rules/ur-e26-new-apr-2022.pdf` 6.4 (p.27 of 32) | a)~l) 전건 자구 일치 |
| 3.1 재량 조항 | Rev.1 "does not fully meet the **additional criteria**" ↔ 초판 "criteria as per **a) to l)**" | 축소 확인 |
| 3.2 4장 구성 | Rev.1 4.1~4.5 절 제목 | 4.4.4·4.5.1~4.5.3 **추가 반영함** |
| 4.1 시리얼 인용 | Rev.1 4.2.1.1(p.10), 4.2.1.4.1 | 자구 일치 |
| 4.1 IEC 인용 | Rev.1 1.3.2 "application of IEC 61162-460 ... may be accepted"; `rules/info_iec61162-460{ed3.0}en.pdf` Scope | 일치 |
| 4.2 범주 정의 | Rev.1 **1.3.3** System Category | 일치 (기존 노트의 "1.3.1"은 오기) |
| 4.2 E22 인용 | `rules/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` 3.2 | 자구 일치 |
| 3.2·3.3 Rec.190 | `rules/Rec-190-New-Jun-2025.pdf` Column O·U (p.4-5 of 11) | 두 항목 모두 "(recommended)" 표기 확인 |

### 선행본에서 수정한 오류

1. **[사실 오류]** 3.2의 4장 구성 목록이 4.4.3에서 끝나 **4.4.4와 4.5 Recover 전체(4.5.1~4.5.3)가 누락**되어 있었다. 이에 따라 "식별·보호·탐지·대응의 전 단계"라는 서술도 복구를 빠뜨렸다. 원문대로 보완했고, 결과적으로 논거가 강해진다.
2. **[정합성]** 요약·ABSTRACT·V장이 "세 가지 한계"의 셋째로 문서 부담 비대칭을 들고 있으나, 본문 3.5절이 삭제되어 근거 없는 주장이 되어 있었다. 집필 메모 3에 따라 전 문서에서 제거하고 "두 가지 한계"로 통일했다.
3. **[정합성]** 서론의 기여 목록이 1번만 남아 있었다. 두 항목으로 재작성했다.
4. **[정합성]** 4.2의 "3.4에서 확인하였듯"이 삭제된 절을 가리키고 있었다. 범주의 고장 기준 근거를 E26 1.3.3 원문 인용으로 대체하여 UR E22 절 없이 성립하도록 했다(집필 메모 4).
5. **[표 번호]** 표 3이 없는데 "표 4"로 되어 있었다 → 표 3.
6. **[문장]** 서론 "기능 요소별로 요구사항을 구성된다" 비문, 3.1 "지정되어 있지 않았다" 시제 → 수정.
7. **[용어]** "2022년판" → **"초판"**으로 통일(집필 메모 9). "초안"은 부정확하다. 2022년 4월판은 초안이 아니라 정식 제정된 UR이며 발효 전에 철회되었다. "초판(Apr 2022, 발효 전 철회)"이 짧으면서 정확하다.
8. **[톤]** "제언한다" → "필요함을 지적한다"(집필 메모 10). 결론 구조를 메모 12의 방향(한계 → 잔여 위협으로 귀결됨을 확인)으로 재편했다.

### 여전히 확인이 필요한 사항 [확인 필요]

- **ATT&CK ID 체계**: 표 3에 T1692/T1695 계열과 T0830/T0832/T0859/T0867이 혼재한다. ICS 매트릭스의 재번호 부여 결과로 보이나 **투고 직전 v19.2 현행 페이지에서 재확인**할 것. 특히 T1692의 하위기법 번호(.001/.002)와 T1695.001의 명칭.
- **NMEA 0183(시리얼) 규격 원문 미보유**: 4.1의 IEC 논거는 61162-460(이더넷 계열 add-on) 원문으로만 뒷받침된다. `experiment/선박 및 해양 프로토콜과 통신 하드웨어 매칭 가이드 V2.docx`로 NMEA 0183 ↔ RS-422 ↔ IEC 61162-1/-2, AMS ↔ RS-485의 대응 관계는 정리되었으나 이는 자체 정리 자료이므로 인용원이 되지 못한다. IEC 61162-1/-2 원문을 확보해야 4.1이 추정에서 직접 인용으로 바뀐다. 그 전까지는 현재 강도("타당하다", "상정할 수 있다") 이상으로 쓰지 말 것.
- **`rules/IEC-61163-2-2020.pdf`는 무관 문서**: 파일명이 61162로 오인되기 쉬우나 실제 내용은 IEC **61163**-2 *Reliability stress screening – Part 2: Components*이다. NMEA와 무관하므로 인용하지 말 것.
- **AMS/ICMS 경로(4.1 마지막 문단)**: 문헌 근거가 아닌 **구성상 추론**이다. `experiment/각 system_최종완료.xlsx - Sheet1.csv`(110행)의 AMS 항목이 "수천 개 센서 신호를 통합 취합"으로 기술되어 구성 자체는 확인되나, 자체 정리 자료이므로 인용원이 아니다. 그림 1의 작도 근거로만 사용할 것.
- **Forescout[14]는 동료심사 문헌이 아니다.** 본문에서 "기술보고서"로 명시했다. 심사에서 지적될 수 있으므로 [13]과 병렬 배치를 유지할 것.
- **분량**: 현재 본문은 3쪽을 초과한다. 압축 우선순위는 ① 3.3의 셋째 문단(C-d 범위 축소) ② 4.2의 고장·공격 대비 설명 ③ 표 2의 h)~l) 행 순으로 줄일 것. 표 1과 표 2는 논문의 핵심이므로 유지.

### 집필 메모 대응 현황

| 메모 | 내용 | 처리 |
|---|---|---|
| 1 | BIMCO 지침의 정성적 평가 문제를 문제 제기에 포함 | 서론 2문단에 반영 |
| 2 | 연구배경(2.1)을 서론으로 이동 | 서론 2~3문단으로 흡수, 2.1 삭제 |
| 3 | 문서 제출 논점 제외 | 3.5 및 요약·결론의 셋째 한계 삭제 |
| 4 | UR E22 상세 삭제 | 3.4(범주 절) 삭제, 4.2에서 최소 인용만 유지 |
| 5 | 서론 전면 수정 | 재작성 |
| 6 | 향후 연구 방향 삭제 | 삭제 상태 유지 |
| 7 | 그림 1 삽입 | 삽입 위치 표시 + 작도 명세 별도 제공 |
| 8 | NMEA 시리얼 취약점 근거 | IEC 61162-460 add-on 구조 + E26 1.3.2로 논거 구성, 추론임을 명시 |
| 9 | "2022년판" 용어 정리 | "초판"으로 통일 |
| 10 | "제언한다" 재검토 | "필요함을 지적한다"로 변경 |
| 11 | 판정 기준 불확정성 문장 유지 | 결론에 굵게 유지 |
| 12 | 결론 방향 전환 | 한계 → 잔여 위협 귀결 확인 구조로 재편 |
| 13 | 추가 자료 | 아래 '추가 검토 자료' 참조 |

---

## 추가 검토 자료 (집필 메모 13 대응)

### 즉시 쓸 수 있는 것 — 로컬 보관 원문으로 확인 완료

**① IACS Rec.166 (Apr 2020, Corr.2 Apr 2022) 6.5 Respond R1** — `rules/IACS Rec.166.pdf` p.10

> R1) Impact of cyber incidents should be **contained to the network zone of origin**.
> R2) Minimize by isolating the extension of possible disruption to OT system which affects the availability of safety critical functions.

E26의 전신인 비강제 권고가 이미 2020년에 사고의 봉쇄(containment)를 기능 요구사항으로 두고 있었다. 이를 쓰면 3.3의 논증이 판본 두 개의 대조에서 **공개 문헌 세 건(Rec.166 → 초판 → Rev.1)을 관통하는 흐름에서의 이탈**로 올라간다. 삽입은 3.3 둘째 문단 앞 한 문장 또는 각주. **분량 초과 상태이므로 각주 권장.**

⚠️ 단, Rec.166 R1은 **제외 판정 기준이 아니라 일반 기능 요구사항**이다. "제외 기준에서 사라졌다"와 층위가 다르므로 "동일 요구가 삭제되었다"고 쓰면 안 된다. "전이 봉쇄라는 문제의식 자체는 IACS 문헌에 계속 있었으나, 제외 판정 단계에서만 사라졌다"가 정확한 서술이다.

### 확보하면 좋은 것 — 현재 미보유

**② Ken Munro / Pen Test Partners (2018), 시리얼-IP 변환장치를 통한 선박 네트워크 침해 실증**
Forescout 보고서[14]가 선행연구로 인용하고 있다("2018: Ken Munro demonstrated how serial-to-IP converters could be used to compromise shipboard networks"). 원자료를 확보하면 4.1의 논거가 **선박 환경에서의 직접 실증**으로 바뀐다. 현재는 [14]의 재인용에 의존하고 있어 심사에서 지적될 수 있다.

**③ IEC 61162-1 / 61162-2 원문** — NMEA 0183 시리얼 규격
확보하면 4.1의 IEC 논거를 추정에서 직접 인용으로 바꿀 수 있다. 우선순위 높음.

**④ 선급별 이행 지침(KR GC-44-K 등)의 제외 관련 서술**
"판정이 선급마다 달라질 수 있다"를 공개 지침 문헌 대조만으로 보일 수 있는 유일한 경로다. 다만 학술대회 3쪽에는 들어가지 않는다. **정식 논문용으로 남길 것.**

### 이번 논문에서는 쓰지 말 것

- **업체 해설본과 IACS 원문을 혼동하지 말 것** — `rules/IACS Rec 171 + BIMCO Risk Assessment.pdf`와 `rules/IACS Rec.190 Guideline_Rev.01.pdf`는 특정 업체가 작성한 해설 자료이므로 인용 불가(1차 자료가 아니고 업체가 식별된다). 2026-08-18 추가된 `rec166corr2.pdf`·`rec171-1.pdf`·`Rec-190-New-Jun-2025.pdf`가 IACS 원문이며, 인용은 이쪽으로만 할 것.
- **Rec.171(May 2022, ISM Code 연계)** — 사이버 위험관리를 안전관리체제(SMS)에 편입하는 권고로, 본 논문의 제외 판정 논지와 층위가 다르다. 제외 대상 CBS가 SMS 관리 대상에서도 빠지는지를 다루려면 별도 절이 필요하므로 **정식 논문용으로 남길 것.**
- **TRITON 백서, Bypassing NAC** — 저범주·IT 경유 전이의 실증 사례로 가치가 있으나 4.2가 이미 규정 논거로 완결되어 있고 분량이 없다. 정식 논문 IV장에서 사용.
