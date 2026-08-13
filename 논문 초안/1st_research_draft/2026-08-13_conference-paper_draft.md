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

IACS UR E26은 선박의 사이버 복원력에 관한 통일규칙으로, 기존의 비강제 가이드라인과 달리 설계부터 운항까지 전 생애주기에 걸친 강제 요구사항을 제시한다. 그러나 동 규칙 6.4는 특정 컴퓨터기반시스템(CBS)을 적용 범위에서 제외할 수 있는 경로를 함께 규정하고 있다. 본 논문은 UR E26 Rev.1의 제외 기준을 2022년판 및 UR E22와 대조 분석하여 세 가지 한계를 제시한다. 첫째, 2022년판에 존재하던 사고 전이(propagation) 관련 조건이 최종안에서 제외되어, 제외된 CBS가 다른 CBS에 미치는 영향을 검증할 절차가 부재하다. 둘째, 제외 판정에 차용된 UR E22의 시스템 범주는 고장(failure) 결과를 기준으로 정의되어 공격자를 상정하지 않는다. 셋째, 제외에 수반되는 문서 부담의 비대칭이 규칙 구조에 내재한다. 아울러 본 논문은 명시적 제외와 별개로, 적용 범위가 OT 시스템을 중심으로 정의됨에 따라 IT 영역이 판단에서 벗어나는 경로가 존재하며, 이때 의존하게 되는 경계 방어의 우회 가능성은 규칙의 실증 요구에 포함되어 있지 않음을 지적한다. 본 논문은 제외 제도의 폐지가 아니라, 전이 검증의 복원과 판정 기준의 구체화를 제언한다.

**핵심어**: 선박 사이버보안, IACS UR E26, 컴퓨터기반시스템, 사고 전이, 사이버 복원력

---

## ABSTRACT

IACS UR E26 is a unified requirement for the cyber resilience of ships. Unlike earlier non-mandatory guidelines, it imposes mandatory requirements across the entire lifecycle from design to operation. However, Section 6.4 of the same requirement also provides a pathway to exclude certain Computer Based Systems (CBS) from its scope of applicability. This paper analyzes the exclusion criteria of UR E26 Rev.1 against the withdrawn 2022 edition and UR E22, and presents three limitations. First, the condition concerning cyber incident propagation, which existed in the 2022 edition, was not carried into the final text, leaving no procedure to verify the effect of an excluded CBS on other systems. Second, the system categories of UR E22, borrowed for the exclusion assessment, are defined on the basis of failure effects and therefore do not presuppose an adversary. Third, an asymmetry in documentation burden is inherent in the structure of the requirement. In addition, apart from explicit exclusion, this paper points out that the scope of applicability is defined around OT systems, which leaves a path for IT domains to fall outside consideration, while the possibility of bypassing the boundary defenses on which such a scope relies is not covered by the compliance demonstrations the requirement calls for. This paper proposes not the abolition of the exclusion scheme, but the restoration of propagation verification and the specification of verifiable assessment criteria.

**Key words**: Ship Cyber Security, IACS UR E26, Computer Based System, Incident Propagation, Cyber Resilience

---

## I. 서 론

선박은 오랫동안 육상과 분리된 폐쇄 환경으로 간주되어 왔으나, 정보통신기술의 발과 선내 장비의 네트워크화가 진행되면서 그 전제는 더 이상 성립하지 않는다. 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서, 선박은 IT와 OT가 혼재하는 복합 환경이 되었다[3]. 이러한 변화는 사이버 위협의 유입 경로를 동시에 확대하였으며, 선박을 대상으로 한 위협 분석과 대응 요구사항 연구가 이어져 왔다[4].

이에 대한 제도적 대응은 비강제 가이드라인에서 출발하였다. BIMCO 등이 발간한 지침[5]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였고, 선급별 권고 수준에 머물렀다. 국제선급연합회(IACS)가 제정한 통일규칙 UR E26[1]은 이 지점에서 분명한 진전이다. 동 규칙은 선박을 하나의 집합체로 보아 사이버 복원력 요구사항을 제시하며, 설계·건조·시운전·운항의 전 생애주기에 걸쳐 문서 제출과 실증을 요구한다. 식별(Identify), 보호(Protect), 탐지(Detect), 대응(Respond), 복구(Recover)의 기능 요소별로 요구사항을 구성한 점 역시 기존 가이드라인과 구별된다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 **제외**할 수 있는 경로를 함께 제도화하였다. 동 규칙 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하고 있으며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 UR E26 적용 실무에서 특정 CBS를 대상에서 제외하려는 시도가 반복적으로 관찰된 데에서 출발한다. 다만 본 논문은 그러한 관찰을 주장의 근거로 삼지 않으며, 규칙 조문과 문서 제출 요구사항의 구조만을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. **UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가?** 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 제외 기준을 발효 전 철회된 2022년판[6] 및 시스템 범주를 정의한 UR E22[2]와 대조 분석하였다. 본 논문의 기여는 다음 세 가지이다.

1. UR E26 6.4의 제외 기준을 제정 과정과 대조하여, 사고 전이(propagation)에 관한 조건이 최종안에서 제외되었음을 확인하였다.
2. 제외 판정에 차용된 UR E22의 시스템 범주가 고장(failure) 결과를 기준으로 정의되어 있음을 지적하고, 이를 보안 판정에 적용할 때 발생하는 범주 불일치를 제시하였다.
3. 제외에 수반되는 문서 부담의 비대칭이 규칙 구조 자체에 내재함을 조문 분석으로 제시하였다.

본 논문의 구성은 다음과 같다. II장에서 IACS 사이버 복원력 규칙 체계와 선행연구를 정리하고, III장에서 제외 기준을 분석한다. III장의 마지막에서는 명시적 제외와 구별되는 또 하나의 이탈 경로로서 적용 범위 정의의 문제를 함께 다룬다. IV장에서 분석의 귀결로서 잔여 위협의 예시를 제시하고, V장에서 결론과 향후 연구 방향을 기술한다.

---

## II. 관련 연구 및 배경

### 2.1 IACS 사이버 복원력 규칙 체계

IACS의 사이버 복원력 관련 통일규칙은 세 축으로 구성된다. UR E22[2]는 소프트웨어에 의존하여 기능을 수행하는 컴퓨터기반시스템의 설계·건조·시운전·유지보수 요구사항을 규정하며, 시스템 범주(Category)를 정의한다. UR E26[1]은 선박을 하나의 집합체로 보아 선박 수준의 사이버 복원력을 다루고, UR E27[7]은 개별 시스템 및 장비의 보안 능력을 다룬다. 세 규칙은 상호 참조 구조를 이루며, 이와 별도로 IACS Rec.166, 171, 190이 비강제 권고로 제공된다.

UR E26의 적용 대상은 물리 프로세스를 제어·감시하는 OT 시스템으로, 추진, 조타, 양묘 및 계류, 발전 및 배전, 화재탐지 및 소화, 빌지·밸러스트, 수밀 및 침수탐지, 조명, 그리고 비상정지·화물안전·가스탐지 등 안전 관련 시스템이 명시되어 있다. 여기에 법정 요건이 요구하는 항해 시스템과 내·외부 통신 시스템이 추가되며, 적용 대상 CBS로부터 다른 시스템으로 향하는 **IP 기반 통신 인터페이스** 역시 범위에 포함된다.

### 2.2 선행연구와 공백

선박 사이버보안에 대한 위협 분석 연구는 꾸준히 축적되어 왔다. 조용현과 차영균[4]은 선박 시스템에 접근하는 이해관계자를 고려한 데이터 흐름도를 수립하고 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였다. 최근에는 MITRE ATT&CK 프레임워크를 선박 환경에 적용한 연구[8], ATT&CK과 D3FEND를 결합하여 대응 방안까지 다룬 연구[9] 등이 발표되었다.

UR E26 자체를 대상으로 한 연구도 등장하였다. 사이버 복원력의 정의를 조사하고 UR E26을 기존 사이버보안 프레임워크와 비교한 연구[10], UR E26의 요구사항을 고려하여 선박 네트워크 토폴로지를 설계한 연구[11]가 그 예이다.

그러나 이들 연구는 공통적으로 **규칙을 어떻게 준수할 것인가**, 또는 **규칙이 다른 프레임워크와 어떻게 다른가**를 다룬다. 규칙이 명시적으로 허용하고 있는 **제외 경로 자체를 분석 대상으로 삼은 연구는 확인되지 않는다.** 본 논문은 이 지점을 다룬다.

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

### 3.3 사고 전이 조건의 부재

UR E26의 2022년판[6]은 6.4의 기준을 a)부터 l)까지 12개 항목으로 규정하고, 이를 모두 "The following criteria shall be considered for the evaluation of risk level acceptability"로 두었다. Rev.1에서는 이것이 필수 기준 4개와 추가 기준 3개로 재편되었다. 두 판본의 대조 결과는 표 2와 같다.

**표 2. 제외 기준의 제정 과정 대조 (2022년판 원문 기준)**

| 2022년판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
|---|---|
| f) ... the CBS shall not be connected to other CBSs or devices by IP-based networks | 필수 C-a로 승격 |
| g) The CBS shall not have available physical interfaces that can be used by uncontrolled/unsecure removable devices | 필수 C-b로 승격 |
| e) The CBS must be located in areas using controlled access | 필수 C-c로 승격 |
| d) The CBS must not serve essential services or multiple ship services | 필수 C-d로 변경 (integrated control system으로 범위 축소) |
| a) **Foreseeable** vulnerabilities, threats, potential impacts ... duly considered in the risk assessment | 추가 A-b로 유지 (Foreseeable → **Known**) |
| b) The attack surface for the CBS is minimized ... | 추가 A-c로 유지 |
| **c) The CBS, considered in its function and role in the integrated system it is part of, cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices** | **삭제** |
| h) The software installed on the CBS has been duly identified and evidence is given of the purpose, name, version, provider and maintainer ... | 삭제 |
| i) The CBS is subject to a maintenance policy and such policy does not imply any permanent or temporary connection to untrusted networks, or use of uncontrolled/unsecure removable devices | 삭제 |
| j) The CBS provides means for checking at any time its functional integrity and the quality of service provided, including checks on hardware and software integrity | 삭제 |
| k) The CBS provides suitable interfaces allowing a human operator to take local manual control ... | 삭제 |
| l) The Incident Response Plan and Recovery Plan contain indications on how to treat the CBS in case of cyber incidents occurring on the ship | 삭제 |
| — | 추가 A-a (should not serve ship functions of category III) 신설 |

이 대조에서 확인되는 사실은 두 가지이다. 첫째, 2022년판의 d)~g)에 해당하는 항목은 고려 사항에서 필수 충족 사항으로 **강화**되었다. 둘째, 2022년판의 c) 항목, 즉 **사고의 전이와 전파에 관한 조건은 최종안에 반영되지 않았다.** c) 항목은 제외 대상 CBS가 다른 시스템으로부터 사고의 영향을 받거나("cannot be affected by cyber incidents vectored by other CBSs or network devices") 다른 시스템으로 영향을 전파하지("nor it can propagate the effect of a cyber incident to other CBSs or network devices") 않을 것을 요구한 유일한 조항이었다.

동일한 대조에서 두 가지 변경이 추가로 확인된다. 하나는 6.4의 수용 문턱에 사용된 표현으로, 2022년판이 "only if **evidence** is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk"로 규정한 것이 Rev.1에서 "only if **assurance** is given ..."으로 변경되었다. 다만 Rev.1의 6.2는 여전히 "only if evidence is given"을 사용하고 있어, 동일한 장 안에서 입증 수준을 지시하는 표현이 일치하지 않는다. 다른 하나는 2022년판이 요구하던 "A concise list of excluded applications of relevant requirements is to be generated and maintained with the CBS documents **onboard the ship**"이 Rev.1에는 나타나지 않는다는 점이다. 위험평가 문서 자체는 Rev.1에서도 제출 및 유지 대상이므로 제외에 관한 기록이 전혀 남지 않는 것은 아니나, 제외된 항목만을 추린 별도 목록을 선내에 비치하도록 하는 요구는 사라졌다.

다만 2022년판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 **제정 과정에서 최종안에 반영되지 않은 것**으로 이해하여야 한다.

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

UR E26의 부속서 I은 이해관계자별·단계별로 제출(Submit), 유지(Maintain), 실증(Demonstrate)하여야 하는 문서를 정리하고 있다. 제외되지 않은 CBS는 보안 구역 및 도관 도면, 사이버 보안 설계 기술서, 선박 자산 목록, 사이버 복원력 시험 절차서 등의 문서 체계에 포함되며, 이들 문서는 설계 단계에서 제출된 후 건조·시운전·운항의 각 단계에서 유지되고 최초 연차검사 이후의 검사에서 실증 대상이 된다. 반면 제외를 위하여 요구되는 것은 5.1.4에 규정된 제외 위험평가 문서이다.

따라서 제외에 수반되는 이행 부담과 제외되지 않는 경우의 이행 부담 사이에는 비대칭이 존재하며, 이 비대칭은 특정 이해관계자의 태도가 아니라 **규칙의 문서 요구 구조 자체에서 발생한다.** 3.1에서 확인한 판정 기준의 불확정성이 이 구조와 결합할 경우, 제외를 시도할 유인과 그 시도가 수용될 여지가 동시에 증가한다.

### 3.6 적용 범위 정의에 의한 이탈: IT 영역의 취급

지금까지는 6.4의 명시적 제외 절차를 다루었다. 그러나 UR E26의 적용 대상에서 벗어나는 경로는 이것만이 아니다. 규칙의 적용 범위 정의 자체가 또 하나의 경로를 형성한다.

UR E26 1.3.2는 적용 대상을 물리 프로세스를 제어·감시하는 OT 시스템으로 규정하고, 이와 별도로 **"적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스"**를 범위에 포함한다. 여기서 말하는 다른 시스템의 예시로는 여객 및 방문객 서비스 시스템, 여객용 네트워크, **관리 네트워크(administrative networks)**, 승무원 복지 시스템, 그리고 영구적이든 일시적이든 OT 시스템에 연결되는 그 밖의 모든 시스템이 열거되어 있다. 즉 이들 시스템은 **그 자체가 요구사항의 적용 대상이 아니며, 적용 대상은 이들과 OT 시스템을 잇는 인터페이스이다.** 선내 업무용 네트워크, CCTV, 무선 접속 설비, 각종 스마트십 솔루션과 같이 통상 IT로 분류되는 구성요소가 판단 과정에서 상대적으로 가볍게 취급되는 여지가 여기에서 발생한다.

이러한 범위 설정은 **경계 방어가 유효하게 작동한다는 전제**에 의존한다. UR E26 4.2.1.1은 보안 구역이 격리되거나 구역 간 데이터 통신을 통제하는 수단으로 연결될 것을 요구하고, 4.2.2.1은 보안 구역이 방화벽 또는 이에 상응하는 수단으로 보호될 것을 요구한다. 문제는 이 전제가 규칙 안에서 검증되지 않는다는 점이다. 4.2.2의 적합성 실증 요구를 보면 **설계 단계와 건조 단계에는 요구사항이 없고(No requirements)**, 시운전 단계의 시험은 구역 경계 보호장치를 대상으로 한 서비스 거부(DoS) 시험, 과도한 데이터 흐름에 대한 DoS 시험, 그리고 불필요한 기능·포트·프로토콜·서비스가 제거되었는지에 대한 포트 스캔 및 분석적 평가로 구성된다. 이들은 각각 가용성과 하드닝을 확인하는 시험이며, **경계가 우회될 수 있는지 자체를 검증하는 시험은 요구되지 않는다.**

경계 방어의 우회는 가설이 아니다. 안전계장시스템(SIS)을 표적으로 한 TRITON 사고에서 공격자는 IT 네트워크를 먼저 침투한 뒤 **양쪽 환경에 모두 접근 가능한 시스템을 경유하여 OT 네트워크로 이동**하였고, 이후 통상 격리된 네트워크 구간에 위치하는 SIS 엔지니어링 워크스테이션을 감염시켰다[13]. 최근 보고에서도 인터넷에 노출된 경계 장비나 침해된 IT 워크스테이션이 OT 영역에 대한 초기 접근 경로로 활용된 사례가 확인된다[12].

따라서 IT로 분류된다는 사실이 해당 구성요소를 사이버 보안 판단에서 제외할 근거가 되기는 어렵다. 6.4의 제외가 개별 CBS를 요구사항 적용에서 배제하는 경로라면, 적용 범위 정의는 **영역 단위로 판단의 시야를 좁히는 경로**로 작용한다. 두 경로는 서로 다른 층위에서 동일한 결과, 즉 보호와 감시의 대상에서 벗어난 자산의 존재로 귀결된다.

## IV. 잔여 위협의 예시

본 장에서는 III장에서 확인한 한계가 어떤 위협으로 남는지를 세 가지 예시로 제시한다. 본 논문은 체계적인 위협 도출을 목적으로 하지 않으며, 각 예시는 앞선 분석의 귀결을 보이는 범위에 한정한다. 각 위협에 대응하는 공격 기법은 MITRE ATT&CK for ICS[14]의 기법 식별자로 표기한다.

### 4.1 시리얼 통신 경로

필수 기준 C-a는 격리를 "have no IP-network connections to other systems or networks"로 정의한다. 즉 IP 네트워크 연결의 부재만을 요구하며, 시리얼 통신에 의한 연결은 제한하지 않는다.

주목할 점은 UR E26이 시리얼 통신의 존재를 인지하고 있다는 것이다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, **simplex serial links**, TCP/IP diodes, dry contacts"를 들고 있으며, 4.2.1.4.1은 비신뢰 네트워크와의 통신에 관한 기술서가 "discrete signals, **serial communication**, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"을 포함하여야 한다고 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도, 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

시리얼 통신이 안전하다는 인식은 이 분야에 국한된 것이 아니며, 이미 실험적으로 반박된 바 있다. 장지웅과 김휘강[15]은 전력 제어시스템에서 사용되는 시리얼 기반 DNP3.0 통신이 아날로그 구간에서의 공격 불가, **"시리얼 방식의 내재적 보안성"**, Master만이 통신을 개시하는 프로토콜 특성을 이유로 안전하다고 알려져 왔음을 지적하고, 상용 시뮬레이터로 구성한 환경에서 **시리얼 구간을 탭핑(tapping)하여 기밀성·무결성·가용성 세 측면 모두에서 취약점을 확인**하였다. 구체적으로 암호화 부재로 인해 별도의 복호화 없이 패킷 내용이 노출되었고, 명령과 응답의 변조 및 Slave 스푸핑이 가능하였으며, 유효성 검사가 없는 패킷 주입으로 버퍼 오버플로가 발생하였다.

시리얼 통신에 보안 수단을 적용하는 것은 기술적으로 가능하나 비용을 수반한다. 홍봉조 등[16]은 RS-485 구간에 암호화를 적용한 실험에서 평문 대비 통신성능이 AES-128 적용 시 45.1%, AES-256 적용 시 35.5% 수준으로 감소함을 측정하였다. 실제로 장지웅과 김휘강[15]은 DNP 인증·암호화에 관한 논의가 7~8년간 진행되었음에도 실제 전력계통망에 도입한 사례가 확인되지 않는다고 보고하면서, 그 이유로 전체 시스템 재설계의 부담과 실시간 제어주기 내 처리라는 운영상 제약을 들었다.

선박 환경에서도 시리얼 구간은 IP 영역과 완전히 분리되어 있지 않다. 최근 보고[12]는 시리얼-IP 변환장치에 대한 분석에서 신규 취약점 20건을 식별하고, 변환장치가 침해될 경우 시리얼 통신이 양방향으로 변조될 수 있음을 실험으로 제시하였으며, 그 배경으로 시리얼 프로토콜이 인증이나 암호화를 갖추지 않은 경우가 많다는 점을 지적한다. 동 보고는 이러한 변환장치의 적용 사례로 추진 및 조타 계통과 전자해도표시정보시스템(ECDIS)을 포함한 선박 시스템을 명시하고 있다.

따라서 IP 연결이 없다는 사실만으로 해당 CBS가 외부 조작으로부터 분리되어 있다고 보기는 어렵다.

### 4.2 시스템 범주를 경유한 전이

추가 기준 A-a는 제외 대상 CBS가 Category III 기능을 담당하지 않을 것을 요구한다. 따라서 Category I 또는 II로 분류된 시스템은 이 기준을 충족한다.

그러나 3.4에서 확인하였듯 이 범주는 고장 결과를 기준으로 정의된 것이다. 감시·정보·관리 기능을 담당하여 Category I로 분류된 시스템이라 하더라도, 상위 범주 시스템에 데이터를 공급하거나 동일한 물리적·논리적 경로를 공유하는 경우 공격의 경유 지점이 될 수 있다. UR E22 3.2가 저범주 시스템이 상위 범주 시스템의 운영에 영향을 주지 않을 것을 언급하고 있음에도, 이를 확인하는 절차는 UR E22와 UR E26 어느 쪽에도 제시되어 있지 않다. 2022년판 c) 항목이 최종안에 반영되었다면 제외 판정 단계에서 이 확인이 이루어질 수 있었을 것이다.

### 4.3 IT 영역을 경유한 접근

3.6에서 확인한 바와 같이, 적용 범위 정의에 따라 선내 업무용 네트워크, CCTV, 무선 접속 설비, 스마트십 솔루션 등은 그 자체가 요구사항의 적용 대상이 아니며, OT 영역과의 분리는 경계 방어에 의존한다. 그러나 경계 방어의 우회 가능성을 확인하는 시험은 4.2.2의 적합성 실증 요구에 포함되어 있지 않다. TRITON 사고[13]에서 확인된 바와 같이 IT 네트워크를 경유한 OT 영역 접근은 실제로 발생한 공격 경로이며, 이 경우 침해의 출발점이 되는 자산은 규칙의 적용 대상 밖에 위치한다.

**표 4. 잔여 위협 예시와 대응 공격 기법**

| 관련 조항 | 잔여 위협 | ATT&CK for ICS |
|---|---|---|
| 6.4 C-a | IP 연결이 없어도 시리얼 경로를 통한 메시지 주입·변조 및 통신 차단이 가능 | T1692 Unauthorized Message (.001 Command, .002 Reporting), T1695.001 Block Communications: Serial COM, T0830 Adversary-in-the-Middle |
| 6.4 A-a | 저범주로 분류되어 제외된 CBS가 상위 범주 CBS로 향하는 경유 지점이 됨 | T0867 Lateral Tool Transfer, T0859 Valid Accounts, T0832 Manipulation of View |
| 1.3.2 | 적용 대상 밖의 IT 자산이 침해 출발점이 되고, 경계 방어의 우회 가능성은 미검증 | T0819 Exploit Public-Facing Application, T0822 External Remote Services, T0866 Exploitation of Remote Services |

세 예시에 공통되는 것은, 해당 CBS가 제외됨으로써 4.1.1의 자산 목록과 4.3.1의 네트워크 운영 감시 대상에서도 함께 빠진다는 점이다. 즉 위 경로를 통한 침해가 발생하더라도 이를 인지할 수단이 확보되어 있지 않다.

---

## V. 결론 및 향후 연구

본 논문은 "UR E26 6.4의 제외 기준을 충족하는 것으로 해당 CBS의 사이버 보안이 확보되었다고 볼 수 있는가"라는 질문에 대하여, 규칙 조문의 대조 분석을 통해 세 가지 한계를 제시하였다.

첫째, 2022년판에 존재하던 사고의 전이와 전파에 관한 조건이 최종안에 반영되지 않아, 제외된 CBS가 다른 시스템에 미치는 영향을 판정 단계에서 확인하는 절차가 존재하지 않는다. 둘째, 제외 판정에 차용된 UR E22의 시스템 범주는 고장 결과를 기준으로 정의되어 있어, 의도를 가진 공격자를 상정하는 보안 판정의 기준으로는 정합하지 않는다. 셋째, 제외에 수반되는 문서 부담과 제외되지 않는 경우의 문서 부담 사이에 비대칭이 존재하며, 이는 규칙의 문서 요구 구조에서 발생한다. 아울러 명시적 제외와 구별되는 이탈 경로로서, 적용 범위가 OT 시스템을 중심으로 정의됨에 따라 IT 영역이 판단에서 벗어나고 그 분리가 의존하는 경계 방어의 우회 가능성은 실증 요구에 포함되어 있지 않음을 확인하였다.

이에 따라 본 논문은 다음을 제언한다. 첫째, 2022년판 c) 항목에 해당하는 **전이 검증 조건의 복원**이다. 이는 본 논문이 지적한 한계 가운데 가장 직접적으로 해소 가능한 부분이다. 둘째, "accessible", "logically disabled", "physical access is controlled", "minimized" 등 판정에 사용되는 표현을 **검증 가능한 형태로 구체화**하는 것이다. 셋째, 6.2와 6.4에서 상이하게 사용되고 있는 입증 수준 표현의 통일이다. 본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 문제는 제외의 존재가 아니라 판정 기준의 불확정성과 전이 검증의 부재에 있다.

본 논문은 규칙 문헌의 분석에 기초하며, 실선 환경에서의 실증을 포함하지 않는다. 또한 선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다.

후속 연구는 두 방향으로 진행할 계획이다. 첫째, 본 논문에서 예시로 제시한 잔여 위협을 STRIDE와 MITRE ATT&CK for ICS를 결합한 방법론으로 체계화하고, 제외된 CBS로부터 상위 범주 CBS에 이르는 전이 경로를 구성하는 것이다. 둘째, 시험 환경(testbed)을 구축하여 도출된 위협 가운데 실증 가능한 항목을 검증하고 이에 대한 방어 방안을 연구하는 것이다. 특히 4.1에서 다룬 시리얼 경로의 경우, 선박용 시리얼 통신 구간에 대한 메시지 주입 실험을 통해 제외 판정과 실제 조작 가능성 사이의 간극을 확인할 수 있을 것으로 본다.

---

## 참고문헌 (작성 중)

- [1] IACS, *UR E26 Cyber resilience of ships*, Rev.1, Nov. 2023.
- [2] IACS, *UR E22 Computer based systems*, Rev.3 Corr.1, Sep. 2025.
- [3] 강남선, "선박 사이버 보안에 대한 기술적 분석," 한국마린엔지니어링학회지, 제42권, 제6호, pp. 463-471, 2018.
- [4] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
- [5] BIMCO et al., *Guidelines on Cyber Security Onboard Ships*, Version 5. **[확인필요: 발행연도·공동발행기관 정확한 표기]**
- [6] IACS, *UR E26 Cyber resilience of ships*, Apr. 2022 (withdrawn). **[확인필요: 철회 사실은 [1]의 Note 1에 기재되어 있으므로 [1] 병기 가능]**
- [7] IACS, *UR E27 Cyber resilience of on-board systems and equipment*, Rev.1, Sep. 2023.
- [8] "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," *Sensors*, vol. 22, no. 5, 1860, 2022. **[확인필요: 저자명]**
- [9] "From sinking to saving: MITRE ATT&CK and D3FEND frameworks for maritime cybersecurity," *International Journal of Information Security*, 2024. DOI 10.1007/s10207-024-00812-4 **[확인필요: 저자명, 권·호·페이지]**
- [10] "선박의 사이버 복원력을 위한 통일규칙(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교 연구," 정보보호학회논문지, 2024. **[확인필요: 저자명, 권·호·페이지, 정확한 국문 제목]**
- [11] "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회 논문집. **[확인필요: 저자명, 연도, 권·호·페이지]**
- [12] Forescout Research, *BRIDGE BREAK: New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters*, 2026.
- [13] A. Di Pinto, Y. Dragoni, and A. Carcano, *TRITON: The First ICS Cyber Attack on Safety Instrument Systems*, Black Hat USA 2018 Research Paper, 2018.
- [14] MITRE, *ATT&CK for ICS*. https://attack.mitre.org/matrices/ics/ **[확인필요: 인용 시점의 매트릭스 버전과 접속일자 표기]**
- [15] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013.
- [16] 홍봉조, 김춘경, 최은희, 이남용, "RS-485 통신보안에 관한 실증적 연구," 한국IT정책경영학회 논문지, 제10권, 제4호, pp. 917-923, 2018. **[확인필요: 종료 페이지]**

⚠️ [8]~[11]은 서지사항 미확보. **투고 전 반드시 원문 확인.** 저자명 없이 인용하면 심사에서 즉시 지적된다.
※ 3쪽 분량이므로 참고문헌은 12건 내외로 제한. IV장 집필 시 확정.

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

**3.6에서 지킨 것**
- 규정 근거를 먼저 세움: 1.3.2 b)가 IT 시스템 자체가 아니라 **인터페이스만** 범위에 넣는다는 점. 이게 "IT는 대상이 아니다"라는 실무 판단의 조문상 출발점
- "실무에서 IT를 간과한다"고 단정하지 않고 **"가볍게 취급되는 여지가 여기에서 발생한다"**로 서술. 관찰을 주장으로 바꾸지 않는다는 원칙 유지
- 방화벽 우회를 일반론으로 말하지 않고 **4.2.2.4의 실증 요구 목록을 근거로** 논증. 설계·건조 단계 "No requirements", 시운전은 DoS 2건 + 포트 스캔뿐 → 우회 검증 시험이 없다는 것이 확인 가능한 사실
- TRITON을 인용하되 "IT 침투 → 양쪽 접근 가능 시스템 경유 → OT 이동"이라는 **경로**만 씀. 선박에 그대로 적용된다고 주장하지 않음
- 마지막 문단에서 6.4 제외와 범위 정의를 **"서로 다른 층위의 두 경로"**로 정리 → 논문 전체가 하나의 구조로 닫힘

**분량 초과 시 삭제 우선순위** ⚠️ 3.6 추가로 III장이 늘어남. 3쪽 맞추려면 아래 순서로 덜어낼 것
1. 2.1의 두 번째 문단(적용 대상 나열) → 3.6에서 1.3.2를 다시 인용하므로 **중복. 한 문장으로 축약**
2. 3.1의 마지막 문단(판정 기준 불확정성) → 3.5로 흡수
3. 표 3(E22 범주) → 본문 서술로 전환
4. 3.3의 evidence/assurance 문단 → 각주 처리
5. 3.6의 TRITON 문단 → 한 문장으로 축약
※ 3.3의 표 2와 3.4의 고장 기준 논증은 논문의 핵심이므로 **끝까지 유지**

**IV·V장에서 지킨 것**
- IV장 첫 문단에서 **"체계적인 위협 도출을 목적으로 하지 않으며 ... 앞선 분석의 귀결을 보이는 범위에 한정한다"**고 선언. 과약속 방지 + 정식 논문 몫 보존
- IV장 4.1/4.2/4.3이 각각 III장 3.3(C-a)/3.4(A-a)/3.6(1.3.2)에 1:1 대응. R9(탐지 불가)는 별도 절로 두지 않고 IV장 마지막 문단에서 **세 예시의 공통점**으로 처리 → 반복을 피하면서 논지는 살림
- 표 4가 논문의 payoff. 관련 조항 → 잔여 위협 → ATT&CK 기법의 3열 구조
- V장 제언에서 **"제외 제도 폐지를 주장하지 않는다"**를 명시하고 그 이유("모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며")까지 씀
- V장 한계에서 **"선급의 실제 판정 실무에 대한 조사를 포함하지 않으므로 판정 편차의 존재 여부는 본 논문의 분석 범위를 벗어난다"**고 명시 → P2를 주장하지 않았음을 스스로 선언. 심사 방어선
- 향후 연구에 STRIDE + ATT&CK for ICS와 testbed를 명시 → 정식 논문과 2단계 연구를 예고하면서, 이 논문이 모델링을 하지 않았음을 분명히 함
