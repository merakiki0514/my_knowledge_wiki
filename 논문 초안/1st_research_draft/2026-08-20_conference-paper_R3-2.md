# IACS UR E26 CBS 제외 기준의 한계 분석: 사고 전이 관점에서

정성윤¹ · 이대성¹'* / ¹한국해양대학교
E-mail : meraki4.1st@gmail.com / dslee@kmou.ac.kr

An Analysis of Limitations in the CBS Exclusion Criteria of IACS UR E26
: From the Perspective of Cyber Incident Propagation
Sung-yoon Jung¹ · Dae-sung Lee¹'* / ¹Korea Maritime and Ocean University

---

## 요 약

IACS UR E26은 선박의 사이버 복원력에 관한 통합규정으로, Rev.1은 2024년 7월 1일 이후 건조계약된 선박을 대상으로 설계부터 운항까지 전 생애주기에 걸친 강제 요구사항을 제시한다. 그러나 동 UR 6.4는 특정 CBS(컴퓨터기반시스템)를 적용 범위에서 제외할 수 있는 경로를 함께 규정하고 있다. 본 논문은 UR E26 Rev.1의 6장을 발효 전 철회된 초판과 대조 분석하여 두 가지 한계를 제시한다. 첫째, 초판이 제외 판정 기준의 항목으로 두었던 사고 전이(propagation)에 관한 판정 항목과 CBS 간 연결 관계의 조사·문서화 요구가 최종안의 판정 기준에 반영되지 않았다. 전이에 관한 요구는 위험평가의 고려 요소와 적용 범위 밖 시스템의 물리적 분할 요구로 Rev.1에 남아 있으나, 이들은 잔존하는 적용 범위 측의 설계·관리 의무이며 제외를 판정하는 단계의 조건이 아니다. 둘째, 6.4는 추가 기준을 충족하지 못하는 CBS도 합리적 설명이 있으면 수용할 수 있도록 재량을 두면서, 필수 기준의 표현과 제외 수용 요건("assurance")에 대한 판정 기준 및 검증 방법을 제시하지 않아 제외 판정이 불확정적이다. 이어 본 논문은 이 두 한계가 결합하여, 시리얼 링크만으로 상위 항해 시스템에 데이터를 공급하는 계측기를 경유한 하나의 전이 경로로 남을 수 있음을 예시한다.

## ABSTRACT

IACS UR E26 Rev.1 imposes mandatory cyber resilience requirements across the lifecycle of ships contracted for construction on or after 1 July 2024. However, its Section 6.4 also provides a pathway to exclude certain Computer-Based Systems (CBSs) from the scope of applicability. This paper compares Section 6 of Rev.1 with the withdrawn first edition and presents two limitations. First, the item on cyber incident propagation and the item requiring that connections between CBSs be duly investigated and documented, both of which the first edition listed among the criteria to be considered when evaluating the acceptability of the risk level, were not carried into the criteria that must be met under Section 6.4 of Rev.1. Requirements addressing propagation do remain elsewhere in Rev.1, but they are design and documentation obligations placed on systems that remain within the scope of applicability, not conditions of the exclusion assessment itself. Second, Section 6.4 grants discretion to accept a CBS that does not fully meet the additional criteria, while giving no threshold or verification method either for the terms used in the mandatory criteria or for the "assurance" on which acceptance rests; the assessment is therefore indeterminate. This paper then illustrates how the two limitations combine into a single residual threat path, in which an excluded instrument that supplies navigational systems over a serial link alone becomes a source of corrupted data for systems that remain in scope.

**키워드** : 선박 사이버보안, IACS UR E26, CBS 제외 기준, 사고 전이, 사이버 복원력

**Keywords** : Maritime cyber security, IACS UR E26, CBS exclusion criteria, Cyber incident propagation, Cyber resilience

---

## Ⅰ. 서 론

선박은 오랫동안 육상과 분리된 폐쇄 환경으로 간주되어 왔으나, 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서 그 전제는 더 이상 성립하지 않는다. 선박은 IT와 OT가 혼재하는 융합 환경이 되었고, 이러한 변화는 사이버 위협의 유입 경로를 함께 확대하였다[1].

제도적 대응은 민간 단체의 비강제 가이드라인에서 출발하였다. BIMCO를 중심으로 발간한 지침[2]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였다. IMO는 MSC-FAL.1/Circ.3[3]으로 해사 사이버 리스크 관리 지침을 제시하였으나 이 역시 비강제 지침이다. 의무의 근거가 된 것은 결의서 MSC.428(98)[4]로, 동 결의서는 사이버 리스크를 ISM Code에 따른 안전관리체제(SMS)에서 다루도록 요구하였다. 국제선급연합회(IACS)는 구체적인 기술 기준으로 통합규정(UR)을 제정하였다. UR E22[5]는 컴퓨터기반시스템(CBS)의 요구사항과 시스템 범주(Category)를 정의하고, UR E26[6]은 선박 수준의 복원력을, UR E27[7]은 개별 장비의 보안 능력을 다룬다. UR E26 Rev.1은 2024년 7월 1일 이후 건조계약된 선박에 적용되며, 1.3.1이 정하는 선박 부류를 대상으로 한다. 동 규칙은 식별·보호·탐지·대응·복구의 기능 요소별로 요구사항을 구성하고 전 생애주기에 걸쳐 문서 제출과 실증을 요구하며, 적용 대상은 추진·조타·발전 및 배전·화재탐지 등 OT 시스템과 법정 요건이 요구하는 항해·통신 시스템, 그리고 적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스이다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 제외할 수 있는 경로를 함께 제도화하였다. 동 UR 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 적용 실무에서 특정 CBS를 제외하려는 시도가 반복적으로 관찰되는 데에서 출발하나, 그러한 관찰을 주장의 근거로 삼지 않고 UR 조문을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. UR E26 6.4의 제외 판정 기준은 제외된 CBS를 경유한 사고 전이가 발생하지 않음을 확인하기에 충분한가? 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 6장을 발효 전 철회된 초판[8]과 대조 분석하고, 그 귀결로 남는 잔여 위협을 하나의 경로로 예시하여 MITRE ATT&CK for ICS의 공격 기법에 대응시킨다. II장에서 선행연구를 정리하고, III장에서 제외 기준을 분석하며, IV장에서 잔여 위협 경로를 예시하고, V장에서 결론을 기술한다.

## Ⅱ. 관련 연구 및 배경

선박 사이버보안의 위협 분석 연구는 꾸준히 축적되어 왔다. 조용현과 차영균[1]은 이해관계자를 고려한 데이터 흐름도를 수립하고 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였으며, 대상 기기는 IEC 61162-450/460 기반 기기 목록에서 선정하였다. 이후 동 연구진의 일부가 참여한 연구에서는 MITRE ATT&CK 프레임워크를 선박 장비에 적용하여 공격 모델을 제시하였다[9].

UR E26 자체를 대상으로 한 연구도 축적되고 있다. 사이버 복원력의 정의를 조사하고 UR E26을 NIST의 사이버보안 프레임워크 및 사이버 복원력 체계와 비교한 연구[10], UR E26의 요구사항과 IEC 62443 참조 모델을 함께 고려하여 선박 네트워크 토폴로지를 설계한 연구[11], 동 규칙의 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[12]가 있으며, 국외에서는 동 규칙의 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[13]가 발표되었다.

그러나 이들 연구는 공통적으로 규칙을 어떻게 준수할 것인가, 또는 규칙이 다른 프레임워크와 어떻게 다른가를 다룬다. 제외에 관하여는 제출·유지 문서의 하나로 언급되거나[12] 규칙의 구성을 소개하는 과정에서 부속 절차로 언급되는[13] 데 그치며, 그 판정 기준이 충분한지는 검토하지 않는다. 본 논문이 확인한 범위에서는 UR이 명시적으로 허용하는 제외의 판정 기준 자체를 분석 대상으로 삼은 연구가 발견되지 않았다. 본 논문은 이 지점을 다룬다.

## Ⅲ. UR E26 CBS 제외 규정 분석

### 3.1 제외 기준과 판정의 불확정성

UR E26 6.1은 적용 대상 CBS를 요구사항 적용에서 제외하는 경우 위험평가를 수행하고 위험수준이 수용 가능함을 입증하는 자료를 제시하도록 규정한다. 구체적인 수용 기준은 6.4에 있으며, 반드시 충족하여야 하는 기준 4개와 위험수준 평가 시 고려되어야 하는 기준 3개로 구성된다. 원문은 전자에 명칭을 부여하지 않고 "The following criteria shall be met to exclude a system from the scope of applicability of this UR"로 두었으며, 후자만 "additional criteria"로 명명한다. 본 논문은 서술의 편의상 전자를 필수 기준, 후자를 추가 기준이라 부른다.

**표 1. UR E26 6.4의 제외 기준 (기준 본문은 원문, 구분 명칭은 본 논문의 것)**

| 구분 | | Criteria |
|---|---|---|
| 필수 | a | The CBS shall be isolated (I.e, have no IP-network connections to other systems or networks) |
| | b | The CBS shall have no accessible physical interface ports. Unused interfaces shall be logically disabled. It shall not be possible to connect unauthorised devices to the CBS. |
| | c | The CBS must be located in areas to which physical access is controlled. |
| | d | The CBS shall not be an integrated control system serving multiple ship functions as specified in the scope of applicability of this UR (see section 1.3) |
| 추가 | a | The CBS should not serve ship functions of category III. |
| | b | Known vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment. |
| | c | The attack surface for the CBS is minimized, having considered its complexity, connectivity, physical and logical access points, including wireless access points. |

이 기준에는 세 가지 재량 요소가 있다. 첫째, 6.4는 추가 기준을 완전히 충족하지 못하는 CBS라 하더라도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"인 경우 제외를 수용할 수 있도록 한다. 둘째, 필수 기준의 "accessible", "logically disabled", "physical access is controlled"와 추가 기준 c)의 "minimized"에 대하여 판정 기준이나 검증 방법이 제시되어 있지 않으며, 6.1이 요구하는 위험평가의 방법론 역시 지정되어 있지 않다. 셋째, 6.4 두문은 제외의 수용 요건을 "only if assurance is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk"로 규정하나, 여기서 요구되는 "assurance"가 어떤 형식과 수준의 입증인지가 규정되어 있지 않다. 즉 제외 판정의 결과는 평가 주체에 따라 달라질 수 있다.

### 3.2 제외의 실질적 효과

제외가 승인된 CBS에는 UR E26 4장의 요구사항이 적용되지 않는다. 4장은 자산 목록(4.1.1), 보안 구역 및 네트워크 분할(4.2.1), 접근 통제(4.2.4), 원격 접속 통제(4.2.6), 이동형 기기 사용(4.2.7), 네트워크 운영 감시(4.3.1), 사고 대응 계획(4.4.1), 복구 계획(4.5.1), 백업·복원(4.5.2) 등 17개 요구사항으로 구성된다. 따라서 제외된 CBS는 선박 자산으로 관리할 의무가 없고, 침해가 발생하여도 이를 탐지할 수단의 확보가 강제되지 않으며, 사고 발생 시 처리·복구 절차의 마련도 강제되지 않는다. 즉 제외는 보호·탐지·대응·복구의 기능 요소에 걸쳐 강제성을 소거하는 방향으로 작용한다. 다만 이는 해당 통제가 선박에 실재하지 않는다는 뜻이 아니라 UR E26이 그 확보를 요구하지 않는다는 뜻이다. 식별 계열에 관하여는 강제 의무가 일부 잔존한다. 5.1.4는 "Risk assessment for the exclusion of CBSs"를 제출 문서로 규정하고 Appendix I은 이를 설계 승인 이후 연차·정기 검사 단계까지 유지(Maintain)하도록 하며, 6.3은 선주에게 갱신과 재제출 의무를 부과한다. 따라서 제외된 CBS의 존재와 그 위험평가는 문서로 남는다. 다만 이 문서가 담는 것은 제외의 정당화이지 해당 CBS에 대한 보호·탐지·대응·복구 통제가 아니다. 자산 목록에 관한 IACS 권고 Rec.190[14]은 제외된 CBS를 목록에 표기할 것을 권장하나, 해당 항목은 권고 내에서도 "(recommended)"로 표시되어 있으며 Rec.190 자체가 비강제 권고이다.

제외의 효과는 UR E26에 그치지 않는다. 장비 수준의 보안 능력을 다루는 UR E27[7] 1.3은 그 적용 대상을 "computer based systems specified in UR E26"으로 규정하므로, UR E26의 적용 범위에서 제외된 CBS는 UR E27의 보안 능력 요구에서도 함께 벗어나는 것으로 읽힌다.

한편 감시에 관하여는 제외 여부와 무관한 별도의 공백이 존재한다. 4.3.1.3이 열거하는 감시 능력은 과다 트래픽에 대한 감시와 보호, 네트워크 연결의 감시, 기기 관리 활동의 감시와 기록, 미승인 기기 접속에 대한 보호, 대역폭 사용률의 임계 초과 경보이다. 이들은 모두 패킷 네트워크를 전제로 하는 능력이며, 문장 단위로 브로드캐스트되는 시리얼 링크에서 관측되는 대상이 아니다. 즉 시리얼 구간의 조작은 해당 CBS가 제외되지 않았더라도 이 요구에 의하여 탐지된다고 보기 어렵다. 제외는 이 공백 위에 자산 관리와 사고 대응의 강제성 소거를 더한다.

### 3.3 판정 기준에서의 전이 착안점 소멸

본 절은 Rev.1 6장과 초판[8] 6장을 항목 단위로 대조하고 그 처리를 승계·부분승계·축소·미반영·신설로 판정하되, 항목의 일부만 승계된 경우 문장 단위로 나누어 표기한다. 초판은 발효 전에 철회되었으므로 규범적 준거가 아니다. 본 논문이 초판을 대조하는 이유는 하나뿐이다. 어떤 조건을 제외 판정 기준의 한 항목으로 규칙 안에 둘 수 있음을 초판이 실제로 보여주기 때문이다. 즉 초판은 그러한 조건의 **존재 가능성에 대한 증명**으로만 사용되며, 그 이상의 규범적 지위나 변경의 의도는 본 논문의 주장에 포함되지 않는다.

초판은 6.4의 기준을 a)~l) 12개 항목으로 규정하고 이를 모두 "shall be considered for the evaluation of risk level acceptability"로 두었으나, Rev.1에서는 필수 기준 4개와 추가 기준 3개로 재편되었다. 대조 결과는 표 2와 같다.

**표 2. UR E26 6장의 제정 과정 대조**

| 초판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
|---|---|
| 6.1·6.3 제외 목록의 선내 유지 요구("A concise list of excluded applications … onboard"), 6.3 선급의 수락·거부 권한 명문 | 미반영 |
| 6.4 두문 "only if **evidence** is given" / 재량 조항 범위 "criteria as per **a) to l)**" | "**assurance**" / "**additional criteria**"로 축소 |
| 12개 항목 전부 "shall be **considered**" | 4개는 "shall be **met**"으로 격상, 3개는 "should be considered" |
| a) **Foreseeable** vulnerabilities, threats, potential impacts … | 추가 b) 단, **Known**으로 축소 |
| b) attack surface … minimized | 추가 c) |
| c) The CBS, **considered in its function and role in the integrated system it is part of**, **cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices** | **미반영** |
| d) must not serve essential services or multiple ship services | 필수 d) 단, 통합제어시스템으로 한정 |
| e) located in areas using controlled access | 필수 c) |
| f) **The connections of CBS to other CBSs have been duly investigated, understood and documented.** In particular, … not be connected … by IP-based networks | 필수 a) 단, **굵은 문장 미반영** |
| g) no available physical interfaces … removable devices | 필수 b) |
| h)~l) 소프트웨어 식별, 유지보수 정책, 기능 무결성, 수동 조작, 사고 대응 지침 | 미반영. 대응 요구가 4장·UR E27에 존재하나 적용 범위 내 CBS에 한하며 제외된 CBS에는 미치지 않는다(3.2 참조) |
| — | 추가 a) 신설 |

**첫째, 변경은 일방적이지 않다.** 초판의 12개 항목은 전부 위험수준 수용성 평가 시의 고려 사항이었고 재량 조항도 12개 전체에 걸쳐 있었다. Rev.1은 이 가운데 4개를 통과 요건으로 격상시키고 재량 조항의 범위를 추가 기준 3개로 좁혔으며, 이는 제외 판정을 조이는 방향이다. 다른 한편 6.4 두문의 입증 수준은 "evidence"에서 "assurance"로, 추가 기준 b)의 평가 대상은 "foreseeable"에서 "known"으로 축소되었고, 제외 내역의 선내 유지 요구와 선급의 수락·거부 권한 명문은 최종안에 반영되지 않았다.

이 가운데 제외 대상의 범위를 가장 크게 넓힌 것은 초판 d)의 한정이다. 초판 d)는 제외 대상이 "essential services or multiple ship services"를 담당하지 않을 것을 지목하였으나, Rev.1 필수 d)는 이를 "an integrated control system serving multiple ship functions"로 좁혔다. 초판 문언에서는 필수 용도를 담당하는 CBS가 단일 기능이더라도 제외 후보에서 배제되는 방향으로 읽히나, Rev.1 문언에서는 통합제어시스템이 아닌 한 단일 필수 용도를 담당하는 CBS도 제외 후보가 된다. 이는 전이의 관점에서 초판 c)의 미반영과 결합할 때 의미가 커진다. 전이의 출발점이 될 수 있는 시스템의 범위가 넓어지는 동시에, 그 전이를 판정 단계에서 확인하도록 지시하는 항목은 사라졌기 때문이다.

**둘째, 전이에 관한 두 항목이 판정 기준 목록에서 사라졌다.** 하나는 c) 항목으로, 제외 대상 CBS가 다른 시스템으로부터 사고의 영향을 받거나 다른 시스템으로 영향을 전파하지 않을 것을 지목한 항목이었다. 다른 하나는 f) 항목의 앞 문장으로, CBS 간 연결이 "duly investigated, understood and documented"될 것을 지목하였다. Rev.1의 필수 기준 a)는 f)의 뒷 문장인 IP 연결 부재만을 승계하였다.

**셋째, 그러나 전이에 관한 요구 자체가 소멸한 것은 아니다.** 관련 요구는 6.4 밖에 흩어져 남아 있으므로, 본 논문의 주장이 성립하려면 이들이 초판 c)·f)의 자리를 대신하는지를 먼저 검토하여야 한다. 확인되는 조항은 다섯이다.

**(i) 6.3**은 위험평가에서 고려할 요소로 "Possible effects related to integration of systems, or interfaces among systems, including systems not onboard"를 든다. 그러나 이 문구는 초판과 Rev.1에 동일하게 존재하므로 초판 c)의 승계로 볼 수 없다. 초판은 이 문구를 두고도 c)를 판정 기준 목록에 별도로 두었다. 또한 6.3은 고려할 요소를 열거할 뿐 그 결과가 어떠할 때 제외를 수용하는지는 규정하지 않는다.

**(ii) 4.1.1.1**은 자산 목록의 대상에 적용 범위 내 CBS와 "the networks connecting such systems to each other and to other CBSs onboard or ashore"를 포함시키므로, 제외된 CBS와의 연결이 잔존 CBS 측 목록에 기재될 여지가 있다.

**(iii) 4.2.1.4.1**은 systems integrator가 제출하는 Zones and conduit diagram과 Cyber security design description이 보안 구역과 비신뢰 네트워크 사이의 통신을 "discrete signals, serial communication, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"으로 기술하도록 강제한다. 제외된 CBS는 4.2.1.3에 의하여 비신뢰 네트워크로 간주되므로, 그와의 시리얼 연결은 이 문서화의 대상이 된다. 초판 f)의 "duly investigated, understood and documented"에 가장 근접한 잔존 조항이다.

**(iv) 5.1.4와 Appendix I**은 "Risk assessment for the exclusion of CBSs"를 설계 단계 제출 문서이자 이후 검사 단계까지 유지되는 문서로 규정한다. 초판 6.1·6.3의 "concise list of excluded applications"에 대응하는 잔존 조항이다.

**(v) 4.2.1.3**은 "Systems, networks or CBSs outside the scope of applicability of this UR are considered untrusted networks and shall be physically segmented from security zones required by this UR"을 강제한다. 제외된 CBS는 6.4 두문의 문언상 이 조항의 적용을 받으므로, 이는 전이 경로에 직접 작용하는 강제 요구이다. 다만 동 조항은 곧바로 "Alternatively, it is accepted that such systems are part of a security zone if these OT-systems meet the same requirements as demanded by the zone"이라는 대안을 함께 둔다. 이 대안의 판정은 순환적이다. 제외란 4장 요구사항의 적용을 면제받는 것인데, 면제받은 CBS가 보안 구역이 요구하는 "the same requirements"를 충족하는지를 다시 판정하여야 하기 때문이다. 결과적으로 이 문장은 제외된 CBS를 물리적 분할 없이 보안 구역 내부에 편입시킬 문언상 통로를 남긴다.

다섯 조항은 모두 **잔존하는 적용 범위 측에 부과된 설계·관리 의무**이며, 어느 것도 제외를 승인할지 판정하는 단계의 조건이 아니다. (iii)과 (iv)는 기술(description)과 문서 유지의 의무일 뿐 판정 기준을 제공하지 않으며, 그 주체와 시점도 6.4의 수용 판정과 분리되어 있다. 초판은 전이 여부와 연결 관계 파악을 판정 기준 목록 안에 두어 평가자가 그 시점에 이를 확인하도록 지시하였으나, Rev.1의 6.4에는 대응 항목이 없다. 즉 본 논문이 지적하는 것은 전이에 관한 요구의 부재가 아니라 **제외 판정 단계에서 전이를 확인하도록 지시하는 착안점의 소멸**이다. 나아가 4.2.1.3의 "physically segmented"에 대하여도 판정 기준과 검증 방법이 없으므로 3.1의 불확정성이 그대로 적용된다. 연결 관계의 식별은 Rev.1 이후 발간된 Rec.190[14]에서 자산 목록의 한 항목("to determine that all connections have been identified")으로 다시 나타나지만, 이 역시 비강제 권고의 권장 항목이며 제외 판정의 조건은 아니다.

다만 초판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 제정 과정에서 최종안에 반영되지 않은 것으로 이해하여야 한다. IACS는 변경 사유를 공개한 바 없으므로 본 논문은 변경의 의도를 추정하지 않으며, 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.

## Ⅳ. 잔여 위협 경로의 예시

본 장은 III장의 두 한계가 조문 해석상 배제되지 않는 위협 경로로 어떻게 남는지를 하나의 사례로 예시한다. 체계적인 위협 도출을 목적으로 하지 않으며, 공격 기법은 MITRE ATT&CK for ICS[15]의 식별자로 표기한다.

**제외 후보 CBS와 전이의 구성.** 먼저 제외 판정을 통과할 수 있는 CBS의 성격을 규정한다. 어떤 기기가 이에 해당하는지는 선박의 설계와 시스템 통합 방식에 따라 달라지므로 일반화하여 특정할 수 없다. 다만 6.4에 따르면 IP 네트워크 연결이 없고(필수 a), 노출된 물리 인터페이스가 없으며(필수 b), 접근이 통제되는 구역에 설치되고(필수 c), 통합제어시스템이 아니며(필수 d), Category III 기능을 담당하지 않는(추가 a) 단일 기능 기기가 후보가 된다. 선교에 설치되는 단독 계측기가 이 성격에 부합한다. 음향측심기, 선속계, 풍향풍속계 등은 자체 IP 스택을 갖지 않고 IEC 61162-1 시리얼 링크의 talker로서 측정값을 송출하며, 그 값은 전자해도표시시스템(ECDIS), 자동조타장치, 항해기록장치 등에 입력된다.

본 장의 구성에서 ECDIS와 자동조타장치는 제외되지 않은 채 적용 범위 안에 남아 있는 시스템으로 둔다. 다루는 것은 이들의 제외 가부가 아니라, **제외된 talker에서 발생한 데이터 오염이 제외되지 않은 이들 시스템으로 전달되는 경로**이다. 즉 제외된 계측기가 전이의 출발점이고 ECDIS와 자동조타장치는 종착점이다.

이 구성은 시리얼 링크의 물리계층 구조와 정합한다. IEC 61162-1은 단방향 simplex의 single-talker/multiple-listener 구조이므로, listener 위치의 기기는 회선을 구동할 수 없어 상위 시스템으로 문장을 주입할 수 없다. 반면 talker 위치의 계측기는 정상 동작으로서 회선을 구동한다. 수신 측이 아무런 검사를 하지 않는다는 뜻은 아니다. IEC 61162-1 문장은 체크섬과 유효성 플래그를 가지며 수신 장비는 입력의 상실이나 무효를 경보로 현시한다. 다만 이들은 전송 오류와 기기 고장을 검출하기 위한 수단이며, 문장의 출처를 **암호학적으로 인증**하는 수단은 규격에 없다. 따라서 물리적으로 그럴듯한 범위 안의 변조는 검사와 경보를 모두 통과한다. 한편 실선의 계측기가 순수한 talker인 경우는 오히려 드물다. 시각 동기나 위치 문장을 수신하기 위한 입력 포트, 설정과 교정을 위한 양방향 서비스 포트를 함께 갖는 것이 일반적이며, 이러한 역방향 경로의 존재는 아래에서 다루는 접근 경로와 직접 연결된다.

이 경로에서 III장의 두 한계는 각각 다른 마디를 담당한다. 필수 기준 a)의 판정 경계는 이 계측기를 **조작할 수 있는가**를, 추가 기준 a)가 근거로 삼는 시스템 범주는 **조작된 값이 상위 시스템으로 가는가**를 결정한다.

**필수 기준 a) — 판정 경계의 미정의.** 필수 기준 a)는 격리를 "have no IP-network connections to other systems or networks"로 정의하여 IP 연결의 부재만을 요구하며 시리얼 연결은 제한하지 않는다. 문제는 이 요건의 판정 경계가 규칙에 정의되어 있지 않다는 점이다. 당해 CBS 자신이 IP 인터페이스를 갖지 않으면 충족한다고 보는 **문언 기준**과, 시리얼-IP 변환장치나 게이트웨이를 경유하여 IP 영역에 도달할 수 있으면 충족하지 못한다고 보는 **경로 기준**이 모두 가능하나, 규칙은 어느 쪽을 취하는지도 판정 대상의 경계를 어디까지로 볼 것인지도 밝히지 않는다. 본 논문은 문언 기준을 **작업가정으로** 채택한다. 근거는 조문이 "The CBS shall be isolated"로 판정의 주어를 당해 CBS에 두고 있다는 점이며, 규칙이 다른 기준을 지시하지 않으므로 이 가정은 잠정적이다. 아래의 논의는 이 가정 위에서 성립하며, 경로 기준을 취하면 해당 CBS는 애초에 제외 후보가 되지 않는다.

이 요건의 불확정성은 규칙 자신의 용어법에서도 확인된다. 6.4 필수 a)는 격리를 "isolated (i.e, have no IP-network connections to other systems or networks)"로 정의하는 반면, 4.2.1.1은 보안 구역에 대하여 "Security zones shall either be isolated (i.e. air gapped) or connected to other security zones or networks…"라고 하여 동일한 용어를 **air gap**으로 정의한다. 같은 규칙 안에서 같은 용어가 서로 다른 두 상태를 가리키며, 두 정의 사이에는 시리얼 링크만을 갖는 CBS라는 간극이 놓인다. 이 CBS는 6.4의 정의로는 격리되어 있고 4.2.1.1의 정의로는 격리되어 있지 않다. 변환장치를 CBS의 경계에 포함시키는지에 따라 판정이 뒤집힐 수 있다는 점과 함께, 이는 3.1에서 지적한 판정 불확정성을 조문 자체로 보여주는 사례가 된다.

한편 UR E26이 시리얼 통신의 존재를 인지하지 못하는 것은 아니다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, simplex serial links, TCP/IP diodes, dry contacts"를 들고, 4.2.1.4.1은 비신뢰 네트워크와의 통신 기술서가 "discrete signals, serial communication"을 포함하도록 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

이 사실은 3.3에서 검토한 4.2.1.3의 효력 범위도 함께 규정한다. 제외된 CBS가 적용 범위 내 시스템에 시리얼로 배선되어 있으면 표면상 "physically segmented" 요구와 충돌하는 것처럼 보이나, 4.2.1.1이 simplex serial link를 구역 간 통제 수단으로 명시하고 있으므로 그러한 배선은 규칙이 허용하는 conduit으로 취급될 수 있다. 즉 4.2.1.3은 본 장이 예시하는 전이 경로를 차단하지 못한다.

시리얼 통신이 그 자체로 안전하다는 인식은 선행 연구에서 이미 반박되었다. 장지웅과 김휘강[16]은 시리얼 기반 DNP3.0 통신이 "Serial 방식의 내재적 보안성" 등을 이유로 안전하다고 알려져 왔음을 지적하고, 시리얼 구간의 탭핑으로 기밀성·무결성·가용성 모두에서 취약점을 확인하였다. 다만 대상이 육상 전력 제어시스템이므로 본 논문은 이를 통념이 실험으로 반박된 선행 사례로만 인용한다. 선박 환경의 시리얼 규격에서도 전제는 같다. IEC 61162 계열에서 보안 요구사항은 기본 규격이 아니라 별도의 add-on 표준인 IEC 61162-460[17]에 규정되며, 동 표준은 스스로를 "an add-on to IEC 61162-450 where higher safety and security standards are needed"로 정의한다. UR E26 1.3.2도 항해·무선통신 시스템에 대하여 IEC 61162-460 또는 동등 표준을 UR E27 4장의 보안 능력 요구 대신 수용할 수 있도록 하되 "on the condition that requirements in UR E26 are complied with"라는 단서를 둔다. 즉 보안 기능은 기본 규격에 내재된 것이 아니라 선택적으로 추가되는 계층이다. 시리얼 구간이 IP 영역과 완전히 분리되어 있지 않은 경우도 보고된다. 보안 업체의 기술보고서[18]는 시리얼-IP 변환장치 3개 제품군에서 신규 취약점 20건을 식별하고, 변환장치를 장악한 공격자가 IP 네트워크를 오가는 시리얼 데이터를 변조할 수 있음을 실험으로 제시하였으며, 변환장치의 적용 사례로 "Critical shipboard systems … including propulsion and steering systems; and the Electronic Chart Display and Information System (ECDIS) used for navigation"을 명시하고, 선박 환경에서 변환장치를 이용하여 선내 네트워크를 침해할 수 있음이 시연된 사례[19]를 선행 연구로 함께 기록하고 있다.

**초기 접근 경로.** 본 장의 시나리오는 필수 기준 b)와 c)를 충족한 CBS를 전제하므로, 공격자가 어떻게 그 계측기 또는 회선에 도달하는지가 먼저 해명되어야 한다. 여기에도 3.1의 불확정성이 그대로 적용된다.

첫째, 필수 기준 c)는 "The CBS must be located in areas to which physical access is controlled"로 판정 대상을 **CBS가 설치된 구역**으로 한정한다. 그런데 계측기의 트랜스듀서와 센서 본체는 선저 탱크, 마스트, 갑판 접속함 등 통제 구역 밖에 있고, 그 배선은 거주구역과 케이블 트레이를 관통한다. 즉 c)가 평가하는 것은 설치 구역이지 **케이블 경로 전체가 아니며**, 규칙은 배선 경로를 판정 대상에 포함시키는지에 관하여 아무것도 규정하지 않는다.

둘째, 필수 기준 b)는 노출된 물리 인터페이스가 없을 것을 요구하면서 "Unused interfaces shall be logically disabled"로 이어지므로, 정비를 위하여 사용 중인 서비스 포트는 비활성화 대상이 아니다. 앞서 언급한 계측기의 설정·교정용 양방향 포트가 여기에 해당한다. 또한 "areas to which physical access is controlled" 역시 누구로부터의 통제인지를 규정하지 않으므로, 선교와 기관구역에 상시 출입하는 정비 인력·검사관·벤더 기술자가 통제 대상에 포함되는지는 판정 주체에 따라 달라질 수 있다. 이 경로는 ATT&CK for ICS의 T0862 Supply Chain Compromise 및 T0847 Replication Through Removable Media에 대응한다.

**추가 기준 a) — 범주를 경유한 전이.** 추가 기준 a)는 제외 대상 CBS가 Category III 기능을 담당하지 않을 것을 제시하나, 이 항목은 "should"로 규정되어 있고 6.4 두문이 추가 기준 미충족 시에도 합리적 설명이 있으면 제외를 수용하도록 하므로 통과 요건이 아니다. 또한 배제되는 것은 Category III뿐이므로 Category II 시스템도 제외 후보가 된다.

이 기준에는 척도 자체가 존재하지 않는 부류도 있다. 추가 기준 a)는 판정 척도로 UR E22의 시스템 범주를 사용하는데, UR E22[5] 1.2는 "Computer-based systems that are covered by statutory regulations are excluded from the requirements of this UR"로 규정하고 그 예시로 SOLAS 제V장·제IV장이 요구하는 항해·무선통신 시스템을 든다. 그런데 UR E26 1.3.2는 바로 그 법정 항해·통신 시스템을 적용 범위에 포함시킨다. 즉 이 부류는 UR E26의 적용 대상이면서 UR E22의 범주 체계 밖에 있으므로, "Category III 기능을 담당하지 않는다"는 판정을 내릴 척도가 존재하지 않는다. 추가 기준 a)가 "should"이고 6.4 두문이 추가 기준 미충족 시의 수용을 허용하므로 이 공백이 제외를 막지는 않으나, 판정의 근거가 비어 있는 상태로 제외가 성립한다는 점에서 3.1의 불확정성이 다시 확인된다.

나아가 이 범주는 애초에 보안을 기준으로 정의된 것이 아니다. UR E26 1.3.3은 "System categories are defined in IACS UR E22 on the basis of the consequences of a system failure to human safety, safety of the vessel and/or threat to the environment"라고 규정한다. 즉 범주는 우발적 고장의 안전 결과를 재는 척도이며 의도를 가진 공격자를 상정하지 않는다. 앞의 계측기는 감시·정보 기능을 담당하므로 낮은 범주로 분류되기 쉬우나, 데이터의 소비자가 아니라 **공급자**이며 그 공급 대상이 상위 범주 시스템이다. 두 계측기의 오염이 이르는 곳은 서로 다르다.

선속계가 송출하는 대수속력은 ECDIS의 표시에만 쓰이지 않는다. 레이더·ARPA가 타선의 진침로와 진속력을 산출하는 sea-stabilized 연산의 입력이므로, 대수속력의 변조는 타선 벡터의 산출을 왜곡하고 이는 최근접점과 최근접시간의 오판으로 이어진다. 즉 충돌 회피 판단의 근거가 되는 값이 오염된다. 음향측심기의 경우 ECDIS의 좌초 회피 기능은 해도의 수심 데이터에 기초하므로 실측 수심의 변조가 곧바로 좌초로 이어지지는 않으나, 천수 경보의 무력화, 용골 하 여유수심 판단의 오류, 항해기록장치에 남는 기록의 오염이 발생한다.

두 경우 모두 오염된 값은 운항자의 상황 인식을 왜곡하며, 자율운항선박과 같이 사람의 판단이 개입하지 않는 구성으로 발전할 경우에는 자동 조타 및 항로 유지 기능의 직접적인 입력이 된다.

이 가능성은 규칙 자체에서도 부분적으로 인식된다. UR E22[5] 3.2는 Category I 시스템이 통상 선급의 검증 대상이 아니라고 하면서도, 해당 시스템에 관한 정보가 "shall be required upon request to determine the correct category or ensure that they do not influence the operation of systems in category II and category III"라고 규정한다. 관련 절차도 존재한다. E22 4.3.3은 시스템별 범주 결정을 요구하고 그 문서를 "upon request" 제출하도록 하며, 4.3.4는 선급이 요구하는 경우 범주 결정을 위한 위험평가를 수행하도록 한다. 다만 이들은 본 논문의 논점을 대신하지 못한다. 첫째, 모두 선급의 요구가 있을 때에만 작동하는 조건부 절차이다. 둘째, 판정 척도가 **고장의 영향**이지 사이버 사고의 전이가 아니다. 셋째, 어느 것도 UR E26 6.4의 제외 수용 판정의 조건으로 편입되어 있지 않다. 여기서 범주 분류의 자기정합성 문제가 드러난다. 상위 범주 기능에 영향을 미치는 CBS는 그 영향을 확인한 뒤라야 낮은 범주로 분류할 수 있으나, 바로 그 확인을 제외 판정 단계에서 지시하는 항목이 6.4에 존재하지 않는다.

**표 3. 제외된 계측기를 경유한 잔여 위협 경로**

| 단계 | 근거 조항과 그 한계 | ATT&CK for ICS |
|---|---|---|
| 제외 | 필수 a)~d)와 추가 a)를 충족하는 시리얼 talker 계측기가 적용 범위에서 배제됨 | — |
| 초기 접근 | 필수 c)가 평가하는 것은 CBS 설치 구역이지 케이블 경로가 아니며, 필수 b)의 "Unused"는 사용 중인 서비스 포트를 대상으로 하지 않음 | T0862 Supply Chain Compromise, T0847 Replication Through Removable Media |
| 회선 조작 | 필수 a)가 IP 연결만을 판정 대상으로 삼아 시리얼 링크가 제한되지 않음 | T1692.002 Unauthorized Message: Reporting Message (측정값 문장의 변조·위조) |
| 〃 (대안) | 위와 같음. 다만 simplex 링크에서는 회선 절단과 in-line 장치 삽입을 전제하므로 필수 b)·c)의 충족 상태와 충돌한다 | T0830 Adversary-in-the-Middle, T1695.001 Block Communications: Serial COM |
| 전이 | 추가 a)의 근거인 시스템 범주가 안전 척도이며, 저범주 talker가 상위 범주에 데이터를 공급함 | T0832 Manipulation of View |
| 영향 | 대수속력 변조 → 레이더·ARPA 진벡터 오류 → 최근접점·최근접시간 오판. 수심 변조 → 천수 경보 무력화·용골 하 여유수심 오판. 자율운항 구성에서는 자동 조타의 직접 입력 | — |
| 미인지 | 제외로 4.1.1 자산 목록과 4.3.1 감시 대상에서 함께 배제됨 | — |

이 경로에서 확인되는 것은, 제외된 CBS 자체에서는 위 침해를 인지할 수단의 확보가 강제되지 않는다는 점이다. 다만 3.2에서 지적한 바와 같이 시리얼 구간의 감시 공백은 제외 여부와 무관하게 존재하며, 제외는 그 위에 자산 관리와 사고 대응의 강제성 소거를 더한다.

## Ⅴ. 결 론

본 논문은 "UR E26 6.4의 제외 판정 기준은 제외된 CBS를 경유한 사고 전이가 발생하지 않음을 확인하기에 충분한가"라는 질문에 대하여 UR 조문의 대조 분석을 통해 충분하지 않다고 답한다. 근거는 두 가지이다. 첫째, 초판이 제외 판정 기준의 항목으로 두었던 '전이 여부에 관한 판정 항목'과 'CBS 간 연결 관계의 조사·문서화 요구'가 최종안의 판정 기준에 반영되지 않았다. 전이에 관한 요구 자체는 위험평가의 고려 요소(6.3), 자산 목록의 대상(4.1.1), 적용 범위 밖 시스템의 물리적 분할(4.2.1.3)로 Rev.1에 남아 있으나, 이들은 모두 잔존하는 적용 범위 측에 부과된 설계·관리 의무이며 제외를 판정하는 단계의 조건이 아니다. 둘째, 6.4는 추가 기준 미충족 시에도 합리적 설명에 의한 수용을 허용하는 재량을 두면서, 필수 기준의 표현과 6.4 두문의 "assurance"에 대한 판정 기준·검증 방법, 그리고 위험평가의 방법론을 제시하지 않아 제외 판정이 불확정적이다.

이어 본 논문은 이 두 한계가 결합하여 조문 해석상 배제되지 않는 잔여 위협 경로로 어떻게 남는지를, 시리얼 링크만을 갖는 계측기를 제외 후보로 두고 하나의 경로로 예시하였다. 필수 기준 a)의 판정 경계는 그 계측기를 조작할 수 있는지를, 추가 기준 a)가 근거로 삼는 시스템 범주는 조작된 값이 상위 시스템으로 전달되는지를 각각 결정하며, 이 경로에서 제외된 CBS 자체에서는 침해의 인지 수단을 확보할 의무가 발생하지 않는다. 본 논문의 학술적 기여는 강제 규정을 분석할 때 요구사항의 강도와 함께 **적용 범위에서 이탈하는 경로의 판정 기준**을 분석 단위로 삼을 수 있음을 보이고, UR E26 6.4에 대하여 그 분석을 수행한 데 있다. 이 분석 단위가 다른 규정에도 일반적으로 유효한지는 본 논문의 범위를 벗어난다. 실무적으로는 제외 판정 시 확인하여야 할 사항과 그 근거 조문을 조문 수준에서 정리한 것이 기여에 해당한다.

본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 문제는 판정 기준의 불확정성과 판정 단계의 전이 착안점 부재에 있다. 따라서 전이에 관한 판정 항목의 복원과 판정 표현의 구체화가 필요하다. 전자는 초판 c)·f)의 문안을 6.4의 필수 기준에 되살리는 형태로, 후자는 필수 기준 a)의 판정 경계를 당해 CBS의 인터페이스로 볼 것인지 변환장치를 포함한 경로 전체로 볼 것인지를 규칙에 명시하는 형태로 가능하다.

본 논문은 UR 조문의 분석에 기초하며 실선 환경에서의 실증과 선급의 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 분석 범위를 벗어난다.

## References

[1] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
[2] BIMCO, ICS, INTERCARGO, INTERTANKO, OCIMF et al., The Guidelines on Cyber Security Onboard Ships, Version 5, 2024.
[3] IMO, Guidelines on Maritime Cyber Risk Management, MSC-FAL.1/Circ.3/Rev.2, 2022.
[4] IMO, Maritime Cyber Risk Management in Safety Management Systems, Resolution MSC.428(98), 2017.
[5] IACS, UR E22 Computer based systems, Rev.3 Corr.1, Sep. 2025.
[6] IACS, UR E26 Cyber resilience of ships, Rev.1, Nov. 2023.
[7] IACS, UR E27 Cyber resilience of on-board systems and equipment, Rev.1, Sep. 2023.
[8] IACS, UR E26 Cyber resilience of ships, New (Apr. 2022), IACS Req. 2022, 32 pp. Withdrawn before entry into force on 1 Jan. 2024; see [6] Note 1.
[9] Y. Jo, O. Choi, J. You, Y. Cha, and D. H. Lee, "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," Sensors, vol. 22, no. 5, art. no. 1860, 2022.
[10] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024.
[11] 손금준, 최상훈, 강남선, 김성록, "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회논문집, 제61권, 제6호, pp. 427-436, 2024.
[12] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024.
[13] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," Turkish Journal of Maritime and Marine Sciences, vol. 10, Special Issue 1, pp. 31-50, 2024.
[14] IACS, Rec.190 Recommendation for Vessel Asset Inventory for Computer-based Systems, Jun. 2025.
[15] MITRE, ATT&CK for ICS, v19.2. https://attack.mitre.org/matrices/ics/ (accessed Aug. 14, 2026).
[16] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013.
[17] IEC, IEC 61162-460, Edition 3.0, Apr. 2024.
[18] Forescout Technologies, New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters, 기술보고서, 2026.
[19] K. Munro, "Hacking serial networks on ships," Pen Test Partners, 보안 업체 공개 분석, 2018. https://www.pentestpartners.com/security-blog/hacking-serial-networks-on-ships/


---

## 수정 로그 (Round 2 대응)

기준선: R3 5차. 리뷰 라운드 2(Major ×3 / Minor ×1) 반영.

### P0

| # | 액션 | 근거 | 원문 대조 |
|---|---|---|---|
| 1 | 3.3 잔존 조항 열거를 3개 → **5개**로 확장. 4.2.1.4.1(Zones and conduit diagram·CSDD의 serial communication 기술 의무)과 5.1.4·Appendix I(제외 위험평가 문서의 제출·유지)을 추가하고, 각각 초판 f)·6.1의 대응물임을 명시한 뒤 "기술·문서 의무일 뿐 판정 기준이 아니다"로 구분 | 규 M1 | E26 4.2.1.4.1 / 5.1.4 / Appendix I |
| 2 | **4.2.1.3 예외 문장 복원 + 순환성 분석** — "Alternatively … meet the same requirements as demanded by the zone"을 인용하고, 4장 적용을 면제받은 CBS가 zone의 same requirements를 충족하는지 판정하는 것이 순환적임을 지적 | 규 M2 | E26 4.2.1.3 |
| 3 | IV장 자산 충돌 해소 — **"ECDIS·자동조타는 6.4에 의하여 제외될 수 없다"는 문장 삭제.** 6장 전문에 법정 설비를 제외 대상에서 배제하는 문언이 없으므로 이 주장은 규정 근거가 없었고, 동시에 음향측심기·선속계 예시와 자기모순이었다. "본 장의 구성에서 제외되지 않은 채 남아 있는 시스템으로 둔다"로 대체 | 규 M4·보 M6·선 M1 | E26 6장 전문 |
| 4 | **문언 기준의 순환 논거 삭제** — "3.3에서 확인한 바와 같이 그 요구가 빠져 있으므로"를 제거하고, 조문이 주어를 당해 CBS에 둔다는 근거만 남긴 뒤 **작업가정**으로 명시적 격하 | 학 M4 | — |
| 5 | **초기 접근 경로 신설** — 필수 c)가 평가하는 것은 CBS 설치 구역이지 케이블 경로가 아니라는 논거(트랜스듀서·배선은 통제 구역 밖). T0862·T0847 매핑 | 보 M1·선 M2 | E26 6.4 c) |
| 6 | **표 3 재구성** — T1692.001(Command) 삭제(talker는 명령을 받지 않음), T0830·T1695.001을 별도 행으로 분리하고 **회선 절단·in-line 삽입 전제가 필수 b)·c)와 충돌함을 명시**, 주 경로는 T1692.002 변조로 집중 | 보 M2·선 M3-c | — |
| 7 | **"수신 측은 검증 수단을 갖지 않는다" 정정** — 61162-1은 체크섬·유효성 플래그를 가지며 수신 장비는 상실·무효를 경보한다는 사실을 인정한 뒤, 없는 것은 **암호학적 출처 인증**이며 따라서 물리적으로 그럴듯한 범위의 변조는 통과함을 논증 | 보/선 C4 | IEC 61162 계열 |
| 8 | **"확인 절차가 없다" → 3항 축소 명제** — E22 4.3.3·4.3.4의 존재를 인정하고 ① 모두 upon request 조건부 ② 척도가 고장 영향 ③ 6.4 판정 조건에 미편입으로 논박 | 규 M5 | E22 4.3.3 / 4.3.4 |
| 9 | **3.2 한정** — 5.1.4·Appendix I·6.3의 잔존 의무를 반영하여 "전 기능 요소 소거" → "보호·탐지·대응·복구의 강제성 소거, 식별 계열은 일부 잔존". 표 2 h)~l) 주석에 "제외된 CBS에는 미치지 않는다(3.2 참조)" 추가 | 규 M3·학 M3 | E26 5.1.4 / Appendix I |
| 10 | **Rev.1 적용 시점·선박 부류 명시** (2024.7.1 이후 건조계약, 1.3.1) — 서론과 영문 초록 | 규 M6 | E26 Note 2 |
| 11 | **초록–결론 정합** — 3.1의 첫째 재량 요소(추가 기준 미충족 시 합리적 설명에 의한 수용)를 국문 요약·영문 초록·결론에 편입 | 학 M7 | — |
| 12 | **형식·서지** — 작업 메모 블록 삭제, 제목 콜론 공백 제거, 저자행 U+02D2 교체, CBS 표기 통일, **IMO 문헌 2건 추가**(MSC-FAL.1/Circ.3/Rev.2, MSC.428(98))하고 비강제 지침과 의무 근거를 분리 서술, **참고문헌 전체를 최초 등장 순서로 재번호(1~19)** | 4명 공통·규 M9 | — |
| 13 | **용어** — `physically segmented`를 "물리적 **분할**"로 통일하여 6.4 a)의 격리(isolation)와 구분. `evidence`/`assurance`는 영문 유지. UR을 "규칙"으로 지칭하지 않도록 전역 수정 | 규·보·편 | — |

### P1

| # | 액션 | 근거 |
|---|---|---|
| 14 | **초판 d) 축소를 3.3 "첫째" 단락에 편입** — "essential services or multiple ship services" → "an integrated control system serving multiple ship functions". 단일 필수 용도 CBS가 제외 후보가 되며, 이것이 초판 c) 미반영과 결합할 때 전이 출발점의 범위가 넓어짐을 서술 | 규·학 M1 |
| 15 | **`isolated`의 규칙 내 이중 정의 추가** — 6.4 a)는 "have no IP-network connections", 4.2.1.1은 "air gapped". 같은 UR 안에서 같은 용어가 다른 상태를 가리키며 그 간극에 시리얼 전용 CBS가 놓임 | 규 R5 |
| 16 | **4.2.1.1의 함의 정리** — simplex serial link가 구역 간 conduit으로 명시되어 있으므로 4.2.1.3이 본 논문의 전이 경로를 차단하지 못함 | 선 M3-d |
| 17 | **영향 사슬 재작성** — 대수속력 변조 → 레이더·ARPA sea-stabilized 진벡터 오류 → 최근접점·최근접시간 오판. 음향측심기는 천수 경보 무력화·용골 하 여유수심 오판·VDR 기록 오염으로 정확히 한정 | 선 M4·M4' |
| 18 | **추가 기준 a)의 척도 부재 발견 신설** — E22 1.2가 법정 규정 적용 CBS를 E22 범위에서 배제하는데 E26 1.3.2는 법정 항해·통신 시스템을 적용 범위에 포함시키므로, 이 부류에는 "Category III를 담당하지 않는다"는 판정 척도가 존재하지 않음. 추가 a)가 should이고 6.4가 재량을 두므로 제외는 성립하나 판정 근거가 비어 있음 | 규 D1(b) |
| 19 | **Cat II도 제외 후보**임을 명시 (추가 a)는 Cat III만 배제) | 선 I7 |
| 20 | **E22 3.2 인용 정정** — "shall be required upon request **to determine the correct category or** ensure that…" 전문 복원 | 규 R6 |
| 21 | **기여 진술 범위 조정** — "강제 규정 일반"에 대한 일반화를 철회하고 분석 단위의 제시로 한정, 학술적/실무적 기여 분리 | 학 M6 |
| 22 | **순수 talker 전제 완화** — 실선 계측기는 시각·위치 문장 수신 포트와 설정·교정용 양방향 서비스 포트를 갖는 것이 일반적임을 명시하고 초기 접근 논거와 연결 | 선 I3 |

### 이번 논문에서 다루지 않기로 한 것 (저자 결정)

위협모델링과 위험평가는 본 논문의 범위에 포함하지 않는다. 이에 따라 다음 지적은 반영하지 않았다.

| 항목 | 근거 리뷰 |
|---|---|
| 정성적/정량적 위험 산정 제시 | 보 M4 |
| 기존 방벽(existing barriers) 분석, C/I/A/Safety 영향 분리 | 보 M3 |
| Mitigation 추적성 확대 | 보 M5 |
| 위상 구조 그림 신설 | 보 M7·학 m7·선 |
| 실제 해사 사이버 사고 사례 비교 | 보 M8 |

### 남은 항목

| 항목 | 비고 |
|---|---|
| **문헌 탐색 프로토콜 1문장 + gap의 중요성 논증** | 학 M5. 실제 수행한 검색 절차는 저자만 알 수 있으므로 대신 작성하지 않음 |
| **[8] 초판의 입수 경로** | 학 m3. IACS 웹 아카이브 URL 확보 시 기입 |
| **[18] Forescout 보고서 URL·접근일** | 규·학·편 |
| **[10] 김진·이삼열 논문 원본** | `papers/`에 없음. 서지사항만 확인 |
| Rec.166 검토 (E26 1.3.4가 명시) | 규 R7. 원문은 `rules/rec166corr2.pdf`에 있음 |
| IEC 61162-450 게이트웨이·VDR의 시리얼-IP 경계 지위 | 선 I4·I5 |
| 분량 약 8.1쪽 | 저자 판단으로 6쪽 수준까지 허용. 초과분 조정 필요 시 지시 |
