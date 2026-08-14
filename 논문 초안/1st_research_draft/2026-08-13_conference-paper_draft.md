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

이에 대한 제도적 대응은 비강제 가이드라인에서 출발하였다. BIMCO 등이 발간한 지침[4]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였고, 선급별 권고 수준에 머물렀다. 국제선급연합회(IACS)가 제정한 통일규칙 UR E26[1]은 이 지점에서 분명한 진전이다. 동 규칙은 선박을 하나의 집합체로 보아 사이버 복원력 요구사항을 제시하며, 설계·건조·시운전·운항의 전 생애주기에 걸쳐 문서 제출과 실증을 요구한다. 식별(Identify), 보호(Protect), 탐지(Detect), 대응(Respond), 복구(Recover)의 기능 요소별로 요구사항을 구성한 점 역시 기존 가이드라인과 구별된다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 **제외**할 수 있는 경로를 함께 제도화하였다. 동 규칙 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하고 있으며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 UR E26 적용 실무에서 특정 CBS를 대상에서 제외하려는 시도가 반복적으로 관찰된 데에서 출발한다. 다만 본 논문은 그러한 관찰을 주장의 근거로 삼지 않으며, 규칙 조문과 문서 제출 요구사항의 구조만을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. **UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가?** 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 제외 기준을 발효 전 철회된 2022년판[5] 및 시스템 범주를 정의한 UR E22[2]와 대조 분석하였다. 본 논문의 기여는 다음 세 가지이다.

1. UR E26 6.4의 제외 기준을 제정 과정과 대조하여, 사고 전이(propagation)에 관한 조건이 최종안에서 제외되었음을 확인하였다.
2. 제외 판정에 차용된 UR E22의 시스템 범주가 고장(failure) 결과를 기준으로 정의되어 있음을 지적하고, 이를 보안 판정에 적용할 때 발생하는 범주 불일치를 제시하였다.
3. 제외에 수반되는 문서 부담의 비대칭이 규칙 구조 자체에 내재함을 조문 분석으로 제시하였다.

본 논문의 구성은 다음과 같다. II장에서 IACS 사이버 복원력 규칙 체계와 선행연구를 정리하고, III장에서 제외 기준을 분석한다. IV장에서 분석의 귀결로서 잔여 위협의 예시를 제시하고, V장에서 결론과 향후 연구 방향을 기술한다.

---

## II. 관련 연구 및 배경

### 2.1 IACS 사이버 복원력 규칙 체계

IACS의 사이버 복원력 관련 통일규칙은 세 축으로 구성된다. UR E22[2]는 소프트웨어에 의존하여 기능을 수행하는 컴퓨터기반시스템의 설계·건조·시운전·유지보수 요구사항을 규정하며, 시스템 범주(Category)를 정의한다. UR E26[1]은 선박을 하나의 집합체로 보아 선박 수준의 사이버 복원력을 다루고, UR E27[6]은 개별 시스템 및 장비의 보안 능력을 다룬다. 세 규칙은 상호 참조 구조를 이루며, 이와 별도로 IACS Rec.166, 171, 190이 비강제 권고로 제공된다.

UR E26의 적용 대상은 물리 프로세스를 제어·감시하는 OT 시스템으로, 추진, 조타, 양묘 및 계류, 발전 및 배전, 화재탐지 및 소화, 빌지·밸러스트, 수밀 및 침수탐지, 조명, 그리고 비상정지·화물안전·가스탐지 등 안전 관련 시스템이 명시되어 있다. 여기에 법정 요건이 요구하는 항해 시스템과 내·외부 통신 시스템이 추가되며, 적용 대상 CBS로부터 다른 시스템으로 향하는 **IP 기반 통신 인터페이스** 역시 범위에 포함된다.

### 2.2 선행연구와 공백

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

이 기준에는 두 가지 재량 요소가 있다. 첫째, 6.4는 추가 기준을 완전히 충족하지 못하는 CBS라 하더라도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"인 경우 제외를 수용할 수 있도록 규정한다. 둘째, 필수 기준에 사용된 "accessible", "logically disabled", "physical access is controlled", "minimized" 등의 표현에 대하여 판정 기준이나 검증 방법이 규칙에 제시되어 있지 않다. 위험평가의 방법론 역시 지정되어 있지 않으며, UR E22 4.3.4가 ISO/IEC 31010을 참고할 수 있다고 언급하는 수준에 그친다.

### 3.2 제외의 실질적 효과

제외가 승인된 CBS에는 UR E26 4장의 요구사항이 적용되지 않는다. 4장은 선박 자산 목록(4.1.1), 보안 구역 및 네트워크 분할(4.2.1), 네트워크 보호 대책(4.2.2), 악성코드 대응(4.2.3), 접근 통제(4.2.4), 무선 통신(4.2.5), 원격 접속 통제(4.2.6), 이동식 장치 사용(4.2.7), 네트워크 운영 감시(4.3.1), 검증 및 진단 기능(4.3.2), 사고 대응 계획(4.4.1), 국부·수동 운전(4.4.2), 네트워크 격리(4.4.3)로 구성된다.

여기서 주목할 점은 제외의 효과가 방어 수단의 면제에 그치지 않는다는 것이다. 제외된 CBS는 4.1.1의 자산 목록에서 빠지므로 **선박의 자산 문서에 그 존재가 기재되지 않고**, 4.3.1의 네트워크 운영 감시 대상에서 빠지므로 **침해가 발생하여도 이를 탐지할 수단이 확보되지 않으며**, 4.4.1의 사고 대응 계획에서 빠지므로 **사고 발생 시 처리 절차가 마련되지 않는다.** 즉 제외는 식별·보호·탐지·대응의 전 단계에 걸친 소거로 작용한다.

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

셋째, d)의 승격에는 범위 축소가 수반되었다. 2022년판은 제외 대상이 "essential services 또는 multiple ship services"를 담당하지 않을 것을 요구하였으나, Rev.1의 C-d는 "multiple ship functions을 담당하는 통합제어시스템"이 아닐 것만을 요구한다. 필수 서비스를 담당하는 단일기능 CBS는 더 이상 이 항목에 걸리지 않으며, 이를 보완할 수 있는 A-a는 "should"에 해당하여 충족이 강제되지 않는다.

동일한 대조에서 두 가지 변경이 추가로 확인된다. 하나는 6.4의 수용 문턱에 사용된 표현으로, 2022년판이 "only if **evidence** is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk"로 규정한 것이 Rev.1에서 "only if **assurance** is given ..."으로 변경되었다. 다만 Rev.1의 6.1과 6.2는 여전히 "evidence"를 사용하고 있어, 동일한 장 안에서 입증 수준을 지시하는 표현이 일치하지 않는다. 다른 하나는 2022년판이 6.1과 6.3 및 부속서에 걸쳐 요구하던 "A concise list of excluded applications of relevant requirements is to be generated and maintained with the CBS documents **onboard the ship**"이 Rev.1에는 나타나지 않는다는 점이다. 위험평가 문서 자체는 Rev.1에서도 제출 및 유지 대상이므로 제외에 관한 기록이 전혀 남지 않는 것은 아니나, 제외된 항목만을 추린 별도 목록을 선내에 비치하도록 하는 요구는 사라졌다.

다만 2022년판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 **제정 과정에서 최종안에 반영되지 않은 것**으로 이해하여야 한다. IACS는 각 항목의 변경 사유를 공개한 바 없으므로, 본 논문은 변경의 의도를 추정하지 않으며 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.

### 3.4 시스템 범주 차용의 문제

추가 기준 A-a는 제외 대상 CBS가 Category III 선박 기능을 담당하지 않을 것을 요구한다. 이 범주는 UR E22[2]에 정의되어 있다.

**표 3. UR E22 Table 3의 시스템 범주 (원문)**

| Category | Failure effects | Typical System functionality |
|---|---|---|
| I | Those systems, failure of which **will not** lead to dangerous situations for human safety, safety of the vessel and/or threat to the environment | Monitoring, informational and administrative functions |
| II | Those systems, failure of which could **eventually** lead to dangerous situations ... | Vessel alarm, monitoring and control functions which are necessary to maintain the vessel in its normal operational and habitable conditions |
| III | Those systems, failure of which could **immediately** lead to dangerous or catastrophic situations ... | Control functions for maintaining the vessel's propulsion and steering; Vessel safety functions |

동 규칙 3.3은 범주별 예시를 제시하고 있으며, Category I의 예시로 "Fuel monitoring system, maintenance support system, diagnostics and troubleshooting system, **closed circuit television**, cabin security, entertainment system, fish detection system"이, Category III의 예시로 "Propulsion control system, steering gear control system, electric power system (including power management system), dynamic positioning system"이 열거되어 있다.

주목할 점은 이 범주의 정의 근거이다. UR E22 3.1은 범주 구분이 "the potential severity of the consequences **if the system serving the function fails**"에 기초한다고 규정하며, 4.3.3은 범주 결정이 "based on the **failure effects** of the system"으로 이루어져야 한다고 규정한다. 즉 이 범주는 우발적 고장의 안전 결과를 재는 척도이며, 의도를 가진 공격자를 상정하지 않는다.

고장과 공격은 성질이 다르다. 고장은 무작위로 발생하고 그 영향은 해당 시스템의 기능적 중요도에 비례하는 경향이 있으나, 공격은 목표를 가지고 수행되며 공격자는 최종 목표가 아닌 시스템을 경유 지점으로 선택할 수 있다. 안전공학의 관점에서 저심각도로 분류되는 자산이 보안의 관점에서 저가치인 것은 아니다.

이 문제는 UR E22 자체에서도 부분적으로 인식되고 있다. 동 규칙 3.2는 Category I 시스템이 통상 선급의 검증 대상이 아니라고 하면서도, 해당 시스템에 관한 정보가 "to determine the correct category or **ensure that they do not influence the operation of systems in category II and category III**"를 위하여 요구될 수 있다고 규정한다. 즉 저범주 시스템이 고범주 시스템에 영향을 미칠 가능성 자체는 규칙이 인지하고 있으나, 이를 검증하는 절차는 제시되어 있지 않다. 그 절차를 담당할 수 있었던 조항이 3.3에서 확인한 2022년판 c) 항목이다.

### 3.5 제외 유인의 구조적 비대칭

제외 여부는 해당 CBS에 적용되는 요구사항의 범위뿐 아니라, 이해관계자가 이행하여야 할 문서화 부담의 크기를 결정한다.

UR E26의 부속서 I은 이해관계자별·단계별로 제출(Submit), 유지(Maintain), 실증(Demonstrate)하여야 하는 문서를 정리하고 있다. 제외되지 않은 CBS는 보안 구역 및 도관 도면, 사이버 보안 설계 기술서, 선박 자산 목록, 사이버 복원력 시험 절차서 등의 문서 체계에 포함된다. 반면 제외를 위하여 요구되는 것은 5.1.4에 규정된 제외 위험평가 문서이다.

주목할 점은 두 문서군이 검사 단계에서 받는 취급이 다르다는 것이다. 부속서 I에서 사이버 복원력 시험 절차서(5.2.1)는 시운전 단계와 특별검사에서 실증(Demonstrate) 대상으로, 사이버 보안 및 복원력 프로그램(5.3.1)은 최초 연차검사에서 제출, 이후 연차검사에서 실증 대상으로 지정되어 있다. 이에 비해 제외 위험평가 문서(5.1.4)는 설계 단계의 제출과 이후 단계의 유지만이 지정되어 있으며, **최초 연차검사·연차검사·특별검사의 어느 열에도 요구가 표시되어 있지 않다.** 즉 제외 판정의 근거 문서는 제출된 후 갱신될 뿐, 검사 단계에서 그 타당성이 실증되는 절차를 갖지 않는다.

따라서 제외에 수반되는 이행 부담과 제외되지 않는 경우의 이행 부담 사이에는 비대칭이 존재하며, 이 비대칭은 특정 이해관계자의 태도가 아니라 **규칙의 문서 요구 구조 자체에서 발생한다.** 3.1에서 확인한 판정 기준의 불확정성이 이 구조와 결합할 경우, 제외를 시도할 유인과 그 시도가 수용될 여지가 동시에 증가한다.

### 3.6 논의의 범위

한편 6.4의 명시적 제외와 별개로, UR E26의 적용 범위가 물리 프로세스를 제어·감시하는 OT 시스템을 중심으로 정의됨에 따라 통상 IT로 분류되는 구성요소가 판단에서 벗어나는 경로가 존재한다. 이는 개별 CBS를 요구사항 적용에서 배제하는 6.4와 층위를 달리하는 문제이므로 본 논문에서는 다루지 않으며, 별고에서 논한다.

---

## IV. 잔여 위협의 예시

본 장에서는 III장에서 확인한 한계가 어떤 위협으로 남는지를 두 가지 예시로 제시한다. 본 논문은 체계적인 위협 도출을 목적으로 하지 않으며, 각 예시는 앞선 분석의 귀결을 보이는 범위에 한정한다. 각 위협에 대응하는 공격 기법은 MITRE ATT&CK for ICS[12]의 기법 식별자로 표기한다.

### 4.1 시리얼 통신 경로

필수 기준 C-a는 격리를 "have no IP-network connections to other systems or networks"로 정의한다. 즉 IP 네트워크 연결의 부재만을 요구하며, 시리얼 통신에 의한 연결은 제한하지 않는다.

주목할 점은 UR E26이 시리얼 통신의 존재를 인지하고 있다는 것이다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, **simplex serial links**, TCP/IP diodes, dry contacts"를 들고 있으며, 4.2.1.4.1은 비신뢰 네트워크와의 통신에 관한 기술서가 "discrete signals, **serial communication**, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"을 포함하여야 한다고 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도, 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

시리얼 통신이 안전하다는 인식은 이 분야에 국한된 것이 아니며, 이미 실험적으로 반박된 바 있다. 장지웅과 김휘강[13]은 전력 제어시스템에서 사용되는 시리얼 기반 DNP3.0 통신이 아날로그 구간에서의 공격 불가, **"시리얼 방식의 내재적 보안성"**, Master만이 통신을 개시하는 프로토콜 특성을 이유로 안전하다고 알려져 왔음을 지적하고, 상용 시뮬레이터로 구성한 환경에서 **시리얼 구간을 탭핑(tapping)하여 기밀성·무결성·가용성 세 측면 모두에서 취약점을 확인**하였다. 구체적으로 암호화 부재로 인해 별도의 복호화 없이 패킷 내용이 노출되었고, 명령과 응답의 변조 및 Slave 스푸핑이 가능하였으며, 유효성 검사가 없는 패킷 주입으로 버퍼 오버플로가 발생하였다.

주목할 점은 이 취약점이 기술적으로 해소 불가능한 것이 아니라는 데 있다. 장지웅과 김휘강[13]은 같은 연구에서 시리얼 구간에도 적절한 인증 및 암호화를 도입하여야 함을 결론으로 제시하였다. 그럼에도 동 연구는 DNP 인증·암호화에 관한 논의가 7~8년간 진행되었음에도 실제 전력계통망에 도입한 사례가 확인되지 않는다고 보고하면서, 그 이유로 전체 시스템 재설계의 부담과 실시간 제어주기 내 처리라는 운영상 제약을 들었다. 문제는 수단의 부재가 아니라 도입 유인의 부재이며, 이는 3.5에서 확인한 구조와 같은 성격이다.

선박 환경에서도 시리얼 구간은 IP 영역과 완전히 분리되어 있지 않다. 최근 보고[14]는 시리얼-IP 변환장치에 대한 분석에서 신규 취약점 20건을 식별하고, 변환장치가 침해될 경우 시리얼 통신이 양방향으로 변조될 수 있음을 실험으로 제시하였으며, 그 배경으로 시리얼 프로토콜이 인증이나 암호화를 갖추지 않은 경우가 많다는 점을 지적한다. 동 보고는 이러한 변환장치의 적용 사례로 추진 및 조타 계통과 전자해도표시정보시스템(ECDIS)을 포함한 선박 시스템을 명시하고 있다.

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

## V. 결론 및 향후 연구

본 논문은 "UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가"라는 질문에 대하여, 규칙 조문의 대조 분석을 통해 세 가지 한계를 제시하였다.

첫째, 2022년판에 존재하던 전이 관련 두 조건 — 사고의 전이·전파 여부에 관한 판정 조건과 CBS 간 연결 관계의 조사·문서화 요구 — 이 최종안에 반영되지 않아, 제외된 CBS가 다른 시스템에 미치는 영향을 판정 단계에서 확인하는 절차가 존재하지 않는다. 둘째, 제외 판정에 차용된 UR E22의 시스템 범주는 고장 결과를 기준으로 정의되어 있어, 의도를 가진 공격자를 상정하는 보안 판정의 기준으로는 정합하지 않는다. 셋째, 제외에 수반되는 문서 부담과 제외되지 않는 경우의 문서 부담 사이에 비대칭이 존재하며, 이는 규칙의 문서 요구 구조에서 발생한다.

이에 따라 본 논문은 다음을 제언한다. 첫째, 2022년판 c) 항목과 f) 항목 앞 문장에 해당하는 **전이 검증 조건의 복원**이다. 이는 본 논문이 지적한 한계 가운데 가장 직접적으로 해소 가능한 부분이다. 둘째, "accessible", "logically disabled", "physical access is controlled", "minimized" 등 판정에 사용되는 표현을 **검증 가능한 형태로 구체화**하는 것이다. 셋째, 6장 안에서 상이하게 사용되고 있는 입증 수준 표현의 통일이다. 본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 문제는 제외의 존재가 아니라 판정 기준의 불확정성과 전이 검증의 부재에 있다.

본 논문은 규칙 문헌의 분석에 기초하며, 실선 환경에서의 실증을 포함하지 않는다. 또한 선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다.

후속 연구는 두 방향으로 진행할 계획이다. 첫째, 본 논문에서 예시로 제시한 잔여 위협을 위협 모델링 기법을 적용하여 체계화하고, 3.6에서 언급한 적용 범위 정의의 문제를 함께 다루는 것이다. 둘째, 시험 환경(testbed)을 구축하여 도출된 위협 가운데 실증 가능한 항목을 검증하고 이에 대한 방어 방안을 연구하는 것이다.

---

## 참고문헌

*(2026-08-14 검증 완료. **전 14건 원문 대조 확인.** 2022년판 원문이 `rules/ur-e26-new-apr-2022.pdf`로 확보되어 표 2는 전량 원문 검증됨 → `llm_wiki/2026-08-14_e26-2022-vs-rev1_verification.md`)*

⚠️ **번호 전면 재편 (2026-08-14)**: 17건 → **14건**. 논리에 기여하지 않는 3건을 삭제하고(아래 "삭제한 참고문헌" 표), 2.2절 보강 2건을 신설한 뒤 전체를 다시 매겼다. 본문 인용 번호와 목록이 [1]~[14] 빠짐없이 일치함을 확인.

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

### 검증 메모

**[3]** 원고가 인용한 "STRIDE와 Attack Tree, 206건 위협 식별"은 원문 초록·본문 확인 완료.

**[5]** 원문 `rules/ur-e26-new-apr-2022.pdf` 보관. 표 2의 모든 셀을 원문과 1:1 대조 완료 → `llm_wiki/2026-08-14_e26-2022-vs-rev1_verification.md`. [9]의 초록이 "IACS issued UR E26 in April 2022"로 발행 사실을 기술하고 있어 2차 문헌 근거도 있다.

**[7]** 제1저자 Y. Jo와 제4저자 Y. Cha는 [3]의 조용현·차영균과 동일 인물(고려대 정보보호대학원). 2.2절에서 "동 연구진의 일부가 참여한 연구"로 서술한 근거다.

**[8]** 국문 제목은 발행본 표기 그대로임. "통일규칙"이 아니라 **"통합 요구사항"**으로 표기되어 있으므로 임의 수정 금지. 연세대 김진·이삼열, AHP로 생애주기 단계별 요소 우선순위를 도출하고 NIST CSF 및 NIST 사이버 복원력 체계와 대조한 연구. **NIST CSF와의 일치율 8.5%, 사이버 복원력 체계와 53.8%**로 보고. 제외 조항은 다루지 않음.

**[9]** 저자 소속이 **한국선급(손금준·최상훈), 이글루코퍼레이션(강남선), 현대LNG해운(김성록)**. IEC 62443 참조 모델을 기반으로 E26 대응 네트워크 토폴로지를 제안하며, **6.4 제외 조항은 다루지 않음** → 2.2절의 "공백" 주장을 뒷받침한다. 원문 PDF를 `papers/IACS UR E26을 고려한 선박 네트워크 토폴로지 설계.pdf`에 보관함.

**[10]** 저자 소속이 이글루코퍼레이션·한국선급·중소조선연구원. 강남선은 [9]의 공저자와 동일 인물이다. **제외를 "제출·유지 문서(CBS 제외에 대한 위험 평가 결과서)"로만 두 차례 언급하고 판정 기준은 다루지 않는다** → 2.2절 공백 주장의 직접 근거. 또한 이 논문의 표 1이 E26 Appendix I를 재현하면서 제외 위험평가 문서의 **검사 열이 비어 있는 것까지 그대로 싣고 있어**, 3.5절 논거가 제3자 문헌에서 독립적으로 확인된다. 분석 노트: `llm_wiki/2024_kang_e26-technical-analysis_note.md`

**[11]** 국외 연구를 하나 포함시켜 "해외 문헌 미조사" 지적을 차단하는 역할. E26 6장은 논문 전체에서 **한 문장**("Its supplementary part is related to risk assessment for exclusion of CBS from the application of requirements")으로만 언급되고 수용 기준은 다루지 않는다.
⚠️ **인용 주의**: 이 논문은 참고문헌을 "IACS UR E26 (2022)"로 표기하면서 본문은 Rev.1 자구를 인용하고 있다(2022년판 4.4.3의 "manually or automatically"가 인용문에 없음). **판본 관련 서술을 이 논문에서 그대로 옮기지 말 것.** 분석 노트: `llm_wiki/2024_kayisoglu_e26-checklist_note.md`

**[12]** 접속 시점 최신판은 **v19.2 (2026-08-06 released)**. 본 원고가 사용한 T1692(.001/.002), T1695.001, T0859는 v19.2 기준 모두 유효한 활성 기법으로 확인함. 단 T1692·T1695는 구 ID(T0855/T0856 등)를 대체한 신규 ID이므로 **버전 표기를 반드시 유지**할 것.

**[14]** 발행 주체는 **Forescout Technologies**(보고서 판권 표기 기준). 신규 취약점은 Lantronix 8건 + Silex 12건 = **20건**으로 본문 수치와 일치. 선박 적용 사례(추진·조타 계통, ECDIS)는 보고서 p.4 기재 확인.

---

### 삭제한 참고문헌 — 정식 논문에서 되살릴 것

논리에 기여하지 않거나 다른 인용으로 대체 가능한 3건을 덜어냈다. **서지는 모두 검증 완료 상태이므로 정식 논문에서 그대로 쓸 수 있다.**

| 구 번호 | 서지 | 삭제 사유 |
|---|---|---|
| 구 [3] | 강남선, "선박 사이버 보안에 대한 기술적 분석," 한국마린엔지니어링학회지, 42(6), pp. 463-471, 2018. DOI: 10.5916/jkosme.2018.42.6.463 | 서론 첫 문단의 일반 배경("IT·OT 혼재") 인용. 해당 서술은 인용 없이도 성립하며 곧바로 이어지는 [3](구 [4])이 같은 역할을 한다 |
| 구 [9] | A. Yousaf and J. Zhou, "From sinking to saving: MITRE ATT&CK and D3FEND frameworks for maritime cybersecurity," *IJIS*, 23(3), pp. 1603-1618, 2024. DOI: 10.1007/s10207-024-00812-4 | 2.2절에서 [7]과 동일한 역할(ATT&CK의 해양 적용). 선박 장비를 직접 다루는 [7]이 표 4와 더 가까움. 국외 문헌 커버리지는 [11]이 담당 |
| 구 [13] | A. Di Pinto, Y. Dragoni, A. Carcano, *TRITON: The First ICS Cyber Attack on Safety Instrument Systems*, Black Hat USA 2018 Research Paper, Nozomi Networks, 2018. | 3.6·4.3절 이월로 본문 인용이 사라짐. 원문 2.3절에 "The attackers moved to the OT network through systems that were accessible to both environments" 확인 완료 |
| 구 [16] | 홍봉조, 김춘경, 최은희, 이남용, "RS-485 통신보안에 관한 실증적 연구," 한국IT정책경영학회 논문지, 10(4), pp. 917-922, 2018. | 4.1절의 "암호화는 가능하나 도입되지 않는다" 논증에서 보조 역할. 해당 논증은 [13]의 결론과 "7~8년간 미도입" 보고만으로 성립한다. 원 논문 결론이 "AES는 비싸지만 ARIA는 거의 무료"여서 한쪽만 인용하면 부정확해지는 문제도 함께 해소됨 |

⚠️ 3쪽 분량에서 **14건도 여전히 많을 수 있다.** 추가 삭감 시 [6](E27, 2.1의 배경 서술 전용) → [4](BIMCO) 순으로 검토. 단 **[5]·[10]·[11]은 각각 표 2와 2.2절 공백 주장의 근거이므로 삭감 대상이 아니다.**

**[16]** 종료 페이지 **922** 확인(917-922). 원 논문의 결론은 "암호화는 비싸다"가 아니라 **"AES는 비싸지만 ARIA는 거의 무료(평문 대비 99.2~99.8%)"**이다. 초안이 AES 수치만 인용해 결론을 절반만 옮기고 있었으므로 4.1절을 수정함(2026-08-14). 수정 후 비용 논거는 [15]의 "7~8년간 도입 사례 없음"이 지고, 4.1이 3.5(도입 유인 구조)와 연결된다.

※ 3쪽 분량이므로 참고문헌은 12건 내외로 제한. 삭감 시 [16] → [3] 순 검토.

---

## 집필 메모

**서론에서 지킨 것**
- E26이 진전임을 2문단에서 명시적으로 인정 (톤 관리)
- 실무 관찰을 3문단에 한 문장으로만 두고, 곧바로 "근거로 삼지 않는다"고 선언
- 2022년판을 "발효 전 철회된"으로 표기 (시행 중 완화 ❌)
- "위협 모델링"이라는 표현을 쓰지 않음 (정식 논문용으로 보존)

**남은 판단**
- 기여 3가지의 순서: 현재 전이 → 범주 → 유인. 제목이 전이를 지목하므로 이 순서가 맞음
- IV장을 "잔여 위협의 예시"로 둔 것은 과약속을 피하기 위함. R1·R6·R9 세 개만 제시

**II·III장에서 지킨 것**
- 3.3에서 "일부는 강화되었다"를 먼저 쓰고 삭제를 뒤에 배치. 유리한 사실만 고르지 않았음을 보여야 나머지 주장이 산다
- 3.3 마지막 문단에서 "발효 전 철회" 사실을 명시하고 "완화가 아니라 최종안 미반영"으로 못박음
- 3.5에서 "특정 이해관계자의 태도가 아니라 규칙의 문서 요구 구조 자체에서 발생한다"고 명시. 실무 관찰을 근거로 삼지 않겠다는 서론의 선언과 호응
- 선급·조선소·업체를 특정하는 표현 없음
- 3.4에서 Cat I 예시의 CCTV를 굵게 처리. 정보·감시계 장비의 귀속점을 독자가 스스로 떠올리게 함(직접 주장하지 않음)

**3.6 이월 (2026-08-14 결정)**
- 구 3.6절(적용 범위 정의에 의한 IT 영역 이탈)과 구 4.3절을 **정식 논문으로 이월.** 근거: `notes/2026-08-14_disclosure-strategy_conference-vs-journal.md`
- 이유 두 가지. ① 6.4 제외와 층위가 다른 **독립된 두 번째 논증 축**이므로 학술대회에서 소진하면 정식 논문의 기여가 줄고 중복게재 리스크가 커진다 ② 3쪽 분량에 III장 6개 절 + IV·V장은 물리적으로 불가
- 대신 3.6에 **한 문장 예고**만 남겨 우선권은 확보. "별고에서 논한다"로 명시
- 이월된 내용의 원본 논증(1.3.2 b)의 인터페이스 한정, 4.2.2 실증 요구에 우회 검증 부재, TRITON 경로)은 이 파일 git 이력과 `llm_wiki/2026-08-13_e26-exclusion-residual-threat_mapping.md`에 남아 있음
- 표 4가 3행 → **2행**, IV장이 3절 → **2절**로 축소됨

**분량 초과 시 삭제 우선순위** (3.6 이월 후 갱신)
1. 2.1의 두 번째 문단(적용 대상 나열) → 한 문장으로 축약
2. 3.1의 마지막 문단(판정 기준 불확정성) → 3.5로 흡수
3. 표 3(E22 범주) → 본문 서술로 전환
4. 3.3의 evidence/assurance 문단 → 각주 처리
5. 표 2의 h)~l) 5행 → 한 행으로 묶어 요약
※ 3.3의 표 2(특히 c)·f) 행)와 3.4의 고장 기준 논증은 논문의 핵심이므로 **끝까지 유지**

**표 2 검증 반영 (2026-08-14 완료)**
`llm_wiki/2026-08-14_e26-2022-vs-rev1_verification.md` §4의 수정 지시 8건 + 연쇄 수정 6건 전부 반영함. 핵심은 세 가지.
- **f) 앞문장 복원** — 원고가 `...`로 가리고 있던 "The connections of CBS to other CBSs have been duly investigated, understood and documented"를 되살림. 미반영된 전이 관련 조건이 **하나(c))가 아니라 둘(c) + f) 앞문장)**임이 드러남. 논문에서 가장 크게 강해진 부분
- **3.3절 구조를 "세 방향의 변경"으로 재편** — 강화 / 전이 조건 미반영 / d)의 범위 축소. **강화를 먼저 쓴다**는 원칙 유지, 재량 조항 축소를 강화 사례로 추가
- **3.5절에 Appendix I 검사 열 대조 추가** — 제외 위험평가 문서(5.1.4)만 1st AS·AS·SS 열이 비어 있다는 사실. 3.5절을 조문만으로 닫는 근거이며 [10]에서 제3자 확인됨

**"IACS는 사유를 공개하지 않았다"를 원고가 먼저 명시** — 3.3절 말미. 심사자가 "초안과 최종안의 차이는 입법재량"이라 반박할 카드를 미리 무력화하고, 동시에 우리가 의도를 추정하지 않는다는 선언이 된다.

**IV·V장에서 지킨 것**
- IV장 첫 문단에서 **"체계적인 위협 도출을 목적으로 하지 않으며 ... 앞선 분석의 귀결을 보이는 범위에 한정한다"**고 선언. 과약속 방지 + 정식 논문 몫 보존
- IV장 4.1/4.2가 각각 III장 3.3(C-a)/3.4(A-a)에 1:1 대응. R9(탐지 불가)는 별도 절로 두지 않고 IV장 마지막 문단에서 **두 예시의 공통점**으로 처리 → 반복을 피하면서 논지는 살림
- V장 향후 연구에서 방법론 조합·전이 경로 구성·실험 설계를 **추상화**(2026-08-14). "STRIDE와 ATT&CK for ICS를 결합한", "전이 경로를 구성하는 것", "시리얼 메시지 주입 실험" 삭제 → 정식 논문과 2단계 연구의 실행 레시피를 넘기지 않기 위함
- 표 4가 논문의 payoff. 관련 조항 → 잔여 위협 → ATT&CK 기법의 3열 구조
- V장 제언에서 **"제외 제도 폐지를 주장하지 않는다"**를 명시하고 그 이유("모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며")까지 씀
- V장 한계에서 **"선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다"**고 명시 → P2를 주장하지 않았음을 스스로 선언. 심사 방어선
- 향후 연구에 STRIDE + ATT&CK for ICS와 testbed를 명시 → 정식 논문과 2단계 연구를 예고하면서, 이 논문이 모델링을 하지 않았음을 분명히 함
