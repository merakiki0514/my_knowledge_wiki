# IACS UR E26 CBS 제외 기준의 한계 분석 : 사고 전이 관점에서

> 작업 파일. R.2 PDF(2026-08-20)를 그대로 옮긴 것을 기준선(baseline)으로 하고,
> 리뷰 대응 수정을 여기에 누적한다. 최종본은 이 파일을 HWP로 옮겨 조판한다.
> 수정 이력은 파일 하단 `## 수정 로그` 참조.

정성윤¹ · 이대성¹˒* / ¹한국해양대학교
E-mail : meraki4.1st@gmail.com / dslee@kmou.ac.kr

An Analysis of Limitations in the CBS Exclusion Criteria of IACS UR E26
: From the Perspective of Cyber Incident Propagation
Sung-yoon Jung¹ · Dae-sung Lee¹˒* / ¹Korea Maritime and Ocean University

---

## 요 약

IACS UR E26은 선박의 사이버 복원력에 관한 통합규정으로, 설계부터 운항까지 전 생애주기에 걸친 강제 요구사항을 제시한다. 그러나 동 규칙 6.4는 특정 CBS(컴퓨터기반 시스템)를 적용 범위에서 제외할 수 있는 경로를 함께 규정하고 있다. 본 논문은 UR E26 Rev.1의 6장을 발효 전 철회된 초판과 대조 분석하여 두 가지 한계를 제시한다. 첫째, 초판이 제외 판정 기준의 항목으로 두었던 사고 전이(propagation)에 관한 판정 항목과 CBS 간 연결 관계의 조사·문서화 요구가 최종안의 판정 기준에 반영되지 않았다. 전이에 관한 요구는 위험평가의 고려 요소와 적용 범위 밖 시스템의 물리적 분리 요구로 Rev.1에 남아 있으나, 이들은 잔존하는 적용 범위 측의 설계·관리 의무이며 제외를 판정하는 단계의 조건이 아니다. 둘째, 필수 기준의 표현과 제외 수용 요건에 대한 판정 기준 및 검증 방법이 제시되지 않아 제외 판정이 불확정적이다. 이어 본 논문은 이 두 한계가 시리얼 통신 경로와 시스템 범주를 경유한 전이라는 두 가지 잔여 위협 경로로 남을 수 있음을 예시한다.

## ABSTRACT

IACS UR E26 imposes mandatory cyber resilience requirements on ships across the entire lifecycle. However, its Section 6.4 also provides a pathway to exclude certain Computer-Based Systems (CBSs) from the scope of applicability. This paper analyzes Section 6 of UR E26 Rev.1 against the withdrawn first edition and presents two limitations. First, the criterion on cyber incident propagation and the requirement that connections between CBSs be duly investigated and documented, both listed among the exclusion criteria of the first edition, were not carried into the acceptance criteria of the final text. Requirements addressing propagation do remain elsewhere in Rev.1, but they are obligations imposed on the remaining in-scope side rather than conditions of the exclusion assessment itself. Second, no threshold or verification method is given for the terms used in the mandatory criteria or for the assurance required to accept an exclusion, which leaves the assessment indeterminate. This paper then illustrates how these limitations remain as two residual threat paths: message injection over serial links, and propagation by way of the system categories.

**키워드** : 선박 사이버보안, IACS UR E26, CBS 제외 기준, 사고 전이, 사이버 복원력

**Keywords** : Maritime cyber security, IACS UR E26, CBS exclusion criteria, Cyber incident propagation, Cyber resilience

---

## Ⅰ. 서 론

선박은 오랫동안 육상과 분리된 폐쇄 환경으로 간주되어 왔으나, 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서 그 전제는 더 이상 성립하지 않는다. 선박은 IT와 OT가 혼재하는 융합 환경이 되었고, 이러한 변화는 사이버 위협의 유입 경로를 함께 확대하였다[3].

제도적 대응은 민간 단체의 비강제 가이드라인에서 출발하였다. BIMCO를 중심으로 발간한 지침[4]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였다. 이후 IMO가 MSC-FAL.1/Circ.3을 제정하고 결의서 MSC.428(98)을 채택함으로써 SMS/ISM Code 내에서 사이버 리스크 관리 절차가 의무화되었고, 국제선급연합회(IACS)는 구체적인 기술 기준으로 통합규정(UR)을 제정하였다. UR E22[2]는 컴퓨터기반시스템(CBS)의 요구사항과 시스템 범주(Category)를 정의하고, UR E26[1]은 선박 수준의 복원력을, UR E27[6]은 개별 장비의 보안 능력을 다룬다. UR E26은 식별·보호·탐지·대응·복구의 기능 요소별로 요구사항을 구성하고 전 생애주기에 걸쳐 문서 제출과 실증을 요구하며, 적용 대상은 추진·조타·발전 및 배전·화재탐지 등 OT 시스템과 법정 요건이 요구하는 항해·통신 시스템, 그리고 적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스이다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에, 특정 CBS를 적용 범위에서 제외할 수 있는 경로를 함께 제도화하였다. 동 규칙 6.4는 제외를 위해 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 규정하며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 본 연구의 문제의식은 적용 실무에서 특정 CBS를 제외하려는 시도가 반복적으로 관찰되는 데에서 출발하나, 그러한 관찰을 주장의 근거로 삼지 않고 규칙 조문을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. UR E26 6.4의 제외 판정 기준은 제외된 CBS를 경유한 사고 전이가 발생하지 않음을 확인하기에 충분한가? 이 질문에 답하기 위하여 본 논문은 UR E26 Rev.1의 6장을 발효 전 철회된 초판[5]과 대조 분석하고, 그 귀결로 남는 잔여 위협을 두 가지 예시로 제시하여 MITRE ATT&CK for ICS의 공격 기법에 대응시킨다. II장에서 선행연구를 정리하고, III장에서 제외 기준을 분석하며, IV장에서 잔여 위협을 예시하고, V장에서 결론을 기술한다.

## Ⅱ. 관련 연구 및 배경

선박 사이버보안의 위협 분석 연구는 꾸준히 축적되어 왔다. 조용현과 차영균[3]은 이해관계자를 고려한 데이터 흐름도를 수립하고 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였으며, 대상 기기는 IEC 61162-450/460 기반 기기 목록에서 선정하였다. 이후 동 연구진의 일부가 참여한 연구에서는 MITRE ATT&CK 프레임워크를 선박 장비에 적용하여 공격 모델을 제시하였다[7].

UR E26 자체를 대상으로 한 연구도 축적되고 있다. 사이버 복원력의 정의를 조사하고 UR E26을 NIST의 사이버보안 프레임워크 및 사이버 복원력 체계와 비교한 연구[8], UR E26의 요구사항과 IEC 62443 참조 모델을 함께 고려하여 선박 네트워크 토폴로지를 설계한 연구[9], 동 규칙의 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[10]가 있으며, 국외에서는 동 규칙의 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[11]가 발표되었다.

그러나 이들 연구는 공통적으로 규칙을 어떻게 준수할 것인가, 또는 규칙이 다른 프레임워크와 어떻게 다른가를 다룬다. 제외에 관하여는 제출·유지 문서의 하나로 언급되거나[10] 규칙의 구성을 소개하는 과정에서 부속 절차로 언급되는[11] 데 그치며, 그 판정 기준이 충분한지는 검토하지 않는다. 본 논문이 확인한 범위에서는 규칙이 명시적으로 허용하는 제외의 판정 기준 자체를 분석 대상으로 삼은 연구가 발견되지 않았다. 본 논문은 이 지점을 다룬다.

## Ⅲ. UR E26 CBS 제외 규정 분석

### 3.1 제외 기준과 판정의 불확정성

UR E26 6.1은 적용 대상 CBS를 요구사항 적용에서 제외하는 경우 위험평가를 수행하고 위험수준이 수용 가능함을 입증하는 자료를 제시하도록 규정한다. 구체적인 수용 기준은 6.4에 있으며, 반드시 충족하여야 하는 기준 4개와 위험수준 평가 시 고려되어야 하는 기준 3개로 구성된다. 원문은 전자에 명칭을 부여하지 않고 "The following criteria shall be met to exclude a system from the scope of applicability of this UR"로 두었으며, 후자만 "additional criteria"로 명명한다. 본 논문은 서술의 편의상 전자를 필수 기준, 후자를 추가 기준이라 부른다.

**표 1. UR E26 6.4의 제외 기준 (기준 본문은 원문, 구분 명칭은 본 논문의 것)**

| 구분 | | Criteria |
|---|---|---|
| 필수 | a | The CBS shall be isolated (I.e, have no IP-network connections to other systems or networks) |
| | b | The CBS shall have no accessible physical interface ports. Unused interfaces shall be logically disabled. It shall not be possible to connect unauthorised devices to the CBS. |
| | c | The CBS must be located in areas to which physical access is controlled. |
| | d | The CBS shall not be an integrated control system serving multiple ship functions as specified in the scope of applicability of this UR |
| 추가 | a | The CBS should not serve ship functions of category III. |
| | b | Known vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment. |
| | c | The attack surface for the CBS is minimized, having considered its complexity, connectivity, physical and logical access points, including wireless access points. |

이 기준에는 세 가지 재량 요소가 있다. 첫째, 6.4는 추가 기준을 완전히 충족하지 못하는 CBS라 하더라도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"인 경우 제외를 수용할 수 있도록 한다. 둘째, 필수 기준의 "accessible", "logically disabled", "physical access is controlled"와 추가 기준 c)의 "minimized"에 대하여 판정 기준이나 검증 방법이 제시되어 있지 않으며, 6.1이 요구하는 위험평가의 방법론 역시 지정되어 있지 않다. 셋째, 6.4 두문은 제외의 수용 요건을 "only if assurance is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk"로 규정하나, 여기서 요구되는 "assurance"가 어떤 형식과 수준의 입증인지가 규정되어 있지 않다. 즉 제외 판정의 결과는 평가 주체에 따라 달라질 수 있다.

### 3.2 제외의 실질적 효과

제외가 승인된 CBS에는 UR E26 4장의 요구사항이 적용되지 않는다. 4장은 자산 목록(4.1.1), 보안 구역 및 네트워크 분리(4.2.1), 접근 통제(4.2.4), 원격 접속 통제(4.2.6), 이동형 기기 사용(4.2.7), 네트워크 운영 감시(4.3.1), 사고 대응 계획(4.4.1), 복구 계획(4.5.1), 백업·복원(4.5.2) 등 17개 요구사항으로 구성된다. 따라서 제외된 CBS는 선박 자산으로 관리할 의무가 없고, 침해가 발생하여도 이를 탐지할 수단의 확보가 강제되지 않으며, 사고 발생 시 처리·복구 절차의 마련도 강제되지 않는다. 즉 제외는 식별·보호·탐지·대응·복구의 전 기능 요소에 걸쳐 강제성을 소거하는 방향으로 작용한다. 다만 이는 해당 통제가 선박에 실재하지 않는다는 뜻이 아니라 UR E26이 그 확보를 요구하지 않는다는 뜻이다. 자산 목록에 관한 IACS 권고 Rec.190[16]은 제외된 CBS를 목록에 표기할 것을 권장하나, 해당 항목은 권고 내에서도 "(recommended)"로 표시되어 있으며 Rec.190 자체가 비강제 권고이다.

제외의 효과는 UR E26에 그치지 않는다. 장비 수준의 보안 능력을 다루는 UR E27[6] 1.3은 그 적용 대상을 "computer based systems specified in UR E26"으로 규정하므로, UR E26의 적용 범위에서 제외된 CBS는 UR E27의 보안 능력 요구에서도 함께 벗어나는 것으로 읽힌다.

한편 감시에 관하여는 제외 여부와 무관한 별도의 공백이 존재한다. 4.3.1.1은 감시 대상을 "Networks in scope of this UR"로 규정하는데 1.3.2 b)가 적용 범위에 포함시키는 통신 인터페이스는 IP 기반의 것이므로, 시리얼 구간의 조작은 해당 CBS가 제외되지 않았더라도 이 요구에 의하여 탐지된다고 보기 어렵다. 제외는 이 공백 위에 자산 관리와 사고 대응의 강제성 소거를 더한다.

### 3.3 판정 기준에서의 전이 착안점 소멸

본 절은 Rev.1 6장과 초판[5] 6장을 항목 단위로 대조하고 그 처리를 승계·부분승계·축소·미반영·신설로 판정하되, 항목의 일부만 승계된 경우 문장 단위로 나누어 표기한다. 초판은 발효 전에 철회되었으므로 규범적 준거가 아니다. 본 논문이 초판을 대조하는 이유는 하나뿐이다. 어떤 조건을 제외 판정 기준의 한 항목으로 규칙 안에 둘 수 있음을 초판이 실제로 보여주기 때문이다. 즉 초판은 그러한 조건의 **존재 가능성에 대한 증명**으로만 사용되며, 그 이상의 규범적 지위나 변경의 의도는 본 논문의 주장에 포함되지 않는다.

초판은 6.4의 기준을 a)~l) 12개 항목으로 규정하고 이를 모두 "shall be considered for the evaluation of risk level acceptability"로 두었으나, Rev.1에서는 필수 기준 4개와 추가 기준 3개로 재편되었다. 대조 결과는 표 2와 같다.

**표 2. UR E26 6장의 제정 과정 대조**

| 초판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
|---|---|
| 6.1·6.3 제외 목록의 선내 유지 요구("A concise list of excluded applications … onboard"), 6.3 선급의 수락·거부 권한 명문 | 미반영 |
| 6.4 두문 "only if **evidence** is given" / 재량 조항 범위 "criteria as per **a) to l)**" | "**assurance**" / "**additional criteria**"로 축소 |
| 12개 항목 전부 "shall be **considered**" | 4개는 "shall be **met**"으로 격상, 3개는 "should be considered" |
| a) **Foreseeable** vulnerabilities, threats, potential impacts … | 추가 b) 단, **Known**으로 축소 |
| b) attack surface … minimized | 추가 c) |
| c) The CBS … **cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices** | **미반영** |
| d) must not serve essential services or multiple ship services | 필수 d) 단, 통합제어시스템으로 한정 |
| e) located in areas using controlled access | 필수 c) |
| f) **The connections of CBS to other CBSs have been duly investigated, understood and documented.** In particular, … not be connected … by IP-based networks | 필수 a) 단, **굵은 문장 미반영** |
| g) no available physical interfaces … removable devices | 필수 b) |
| h)~l) 소프트웨어 식별, 유지보수 정책, 기능 무결성, 수동 조작, 사고 대응 지침 | 미반영. 대응 요구는 4장·UR E27에 존재 |
| — | 추가 a) 신설 |

**첫째, 변경은 일방적이지 않다.** 초판의 12개 항목은 전부 위험수준 수용성 평가 시의 고려 사항이었고 재량 조항도 12개 전체에 걸쳐 있었다. Rev.1은 이 가운데 4개를 통과 요건으로 격상시키고 재량 조항의 범위를 추가 기준 3개로 좁혔으며, 이는 제외 판정을 조이는 방향이다. 다른 한편 6.4 두문의 입증 수준은 "evidence"에서 "assurance"로, 추가 기준 b)의 평가 대상은 "foreseeable"에서 "known"으로 축소되었고, 제외 내역의 선내 유지 요구와 선급의 수락·거부 권한 명문은 최종안에 반영되지 않았다.

**둘째, 전이에 관한 두 항목이 판정 기준 목록에서 사라졌다.** 하나는 c) 항목으로, 제외 대상 CBS가 다른 시스템으로부터 사고의 영향을 받거나 다른 시스템으로 영향을 전파하지 않을 것을 지목한 항목이었다. 다른 하나는 f) 항목의 앞 문장으로, CBS 간 연결이 "duly investigated, understood and documented"될 것을 지목하였다. Rev.1의 필수 기준 a)는 f)의 뒷 문장인 IP 연결 부재만을 승계하였다.

**셋째, 그러나 전이에 관한 요구 자체가 소멸한 것은 아니다.** 관련 요구는 6.4 밖에 흩어져 남아 있으므로, 본 논문의 주장이 성립하려면 이들이 초판 c)·f)의 자리를 대신하는지를 먼저 검토하여야 한다. 6.3은 위험평가에서 고려할 요소로 "Possible effects related to integration of systems, or interfaces among systems, including systems not onboard"를 들지만, 이 문구는 초판과 Rev.1에 동일하게 존재하므로 초판 c)의 승계로 볼 수 없으며 — 초판은 이 문구를 두고도 c)를 판정 기준 목록에 별도로 두었다 — 고려할 요소를 열거할 뿐 그 결과가 어떠할 때 제외를 수용하는지는 규정하지 않는다. 4.1.1.1은 자산 목록의 대상에 적용 범위 내 CBS와 "the networks connecting such systems to each other and to other CBSs onboard or ashore"를 포함시키므로 제외된 CBS와의 연결이 잔존 CBS 측 목록에 기재될 여지가 있다. 4.2.1.3은 "Systems, networks or CBSs outside the scope of applicability of this UR are considered untrusted networks and shall be physically segmented from security zones required by this UR"을 강제하며, 제외된 CBS는 6.4 두문의 문언상 이 조항의 적용을 받으므로 이는 전이 경로에 직접 작용하는 강제 요구이다.

세 조항은 모두 **잔존하는 적용 범위 측에 부과된 설계·관리 의무**이며, 어느 것도 제외를 승인할지 판정하는 단계의 조건이 아니다. 초판은 전이 여부와 연결 관계 파악을 판정 기준 목록 안에 두어 평가자가 그 시점에 이를 확인하도록 지시하였으나, Rev.1의 6.4에는 대응 항목이 없다. 즉 본 논문이 지적하는 것은 전이에 관한 요구의 부재가 아니라 **제외 판정 단계에서 전이를 확인하도록 지시하는 착안점의 소멸**이다. 나아가 4.2.1.3의 "physically segmented"에 대하여도 판정 기준과 검증 방법이 없으므로 3.1의 불확정성이 그대로 적용된다. 연결 관계의 식별은 Rev.1 이후 발간된 Rec.190[16]에서 자산 목록의 한 항목("to determine that all connections have been identified")으로 다시 나타나지만, 이 역시 비강제 권고의 권장 항목이며 제외 판정의 조건은 아니다.

다만 초판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 제정 과정에서 최종안에 반영되지 않은 것으로 이해하여야 한다. IACS는 변경 사유를 공개한 바 없으므로 본 논문은 변경의 의도를 추정하지 않으며, 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.

## Ⅳ. 잔여 위협의 예시

본 장은 III장의 한계가 조문 해석상 배제되지 않는 위협 경로로 어떻게 남는지를 예시한다. 체계적인 위협 도출을 목적으로 하지 않으며, 공격 기법은 MITRE ATT&CK for ICS[12]의 식별자로 표기한다.

### 4.1 제외 후보 CBS와 필수 기준 a)의 판정 경계

먼저 제외 판정을 통과할 수 있는 CBS의 성격을 규정한다. 어떤 기기가 이에 해당하는지는 선박의 설계와 시스템 통합 방식에 따라 달라지므로 일반화하여 특정할 수 없다. 다만 6.4에 따르면 IP 네트워크 연결이 없고(필수 a), 노출된 물리 인터페이스가 없으며(필수 b), 접근이 통제되는 구역에 설치되고(필수 c), 통합제어시스템이 아니며(필수 d), Category III 기능을 담당하지 않는(추가 a) 단일 기능 기기가 후보가 된다. 선교에 설치되는 단독 계측기가 이 성격에 부합한다. 음향측심기, 선속계, 풍향풍속계 등은 자체 IP 스택을 갖지 않고 IEC 61162-1 시리얼 링크의 talker로서 측정값을 송출하며, 그 값은 전자해도표시시스템(ECDIS), 자동조타장치, 항해기록장치 등에 입력된다.

여기서 분명히 하여야 할 것은 ECDIS와 자동조타장치가 제외 대상이 아니라는 점이다. 이들은 법정 요건이 요구하는 항해 시스템으로서 UR E26 1.3.2의 적용 범위에 명시되어 있어 6.4에 의하여 제외될 수 없다. 본 장이 다루는 구성은 이들이 제외될 수 있다는 것이 아니라, **제외된 talker에서 발생한 데이터 오염이 제외되지 않은 이들 시스템으로 전달되는 경로**이다. 즉 제외된 계측기가 전이의 출발점이고 ECDIS와 자동조타장치는 종착점이다. 이 구성은 물리계층 구조와도 정합한다. IEC 61162-1은 단방향 simplex의 single-talker/multiple-listener 구조이므로 listener 위치의 기기는 회선을 구동할 수 없어 주입이 불가능한 반면, talker 위치의 계측기는 정상 동작으로서 회선을 구동하며 수신 측은 그 문장을 검증할 수단을 갖지 않는다.

필수 기준 a)는 격리를 "have no IP-network connections to other systems or networks"로 정의하여 IP 연결의 부재만을 요구하며 시리얼 연결은 제한하지 않는다. 문제는 이 요건의 판정 경계가 규칙에 정의되어 있지 않다는 점이다. 당해 CBS 자신이 IP 인터페이스를 갖지 않으면 충족한다고 보는 **문언 기준**과, 시리얼-IP 변환장치나 게이트웨이를 경유하여 IP 영역에 도달할 수 있으면 충족하지 못한다고 보는 **경로 기준**이 모두 가능하나, 규칙은 어느 쪽을 취하는지도 판정 대상의 경계를 어디까지로 볼 것인지도 밝히지 않는다. 본 논문은 문언 기준을 채택한다. 조문이 "The CBS shall be isolated"로 주어를 당해 CBS에 두고 있으며, 경로 기준으로 판정하려면 해당 CBS의 연결 관계를 조사·문서화하여야 하는데 3.3에서 확인한 바와 같이 바로 그 요구가 판정 기준에서 빠져 있기 때문이다. 변환장치를 CBS의 경계에 포함시키는지에 따라 판정이 뒤집힐 수 있다는 사실 자체가 3.1의 불확정성을 보여주는 사례가 된다.

한편 UR E26이 시리얼 통신의 존재를 인지하지 못하는 것은 아니다. 4.2.1.1은 보안 구역 간 연결 수단의 예시로 "firewalls/routers, simplex serial links, TCP/IP diodes, dry contacts"를 들고, 4.2.1.4.1은 비신뢰 네트워크와의 통신 기술서가 "discrete signals, serial communication"을 포함하도록 규정한다. 즉 규칙은 본문에서 시리얼 통신을 다루면서도 제외 판정에서는 IP 연결의 유무만을 기준으로 삼는다.

시리얼 통신이 그 자체로 안전하다는 인식은 선행 연구에서 이미 반박되었다. 장지웅과 김휘강[13]은 시리얼 기반 DNP3.0 통신이 "Serial 방식의 내재적 보안성" 등을 이유로 안전하다고 알려져 왔음을 지적하고, 시리얼 구간의 탭핑으로 기밀성·무결성·가용성 모두에서 취약점을 확인하였다. 다만 대상이 육상 전력 제어시스템이므로 본 논문은 이를 통념이 실험으로 반박된 선행 사례로만 인용한다. 선박 환경의 시리얼 규격에서도 전제는 같다. IEC 61162 계열에서 보안 요구사항은 기본 규격이 아니라 별도의 add-on 표준인 IEC 61162-460[15]에 규정되며, 동 표준은 스스로를 "an add-on to IEC 61162-450 where higher safety and security standards are needed"로 정의한다. UR E26 1.3.2도 항해·무선통신 시스템에 대하여 IEC 61162-460 또는 동등 표준을 UR E27 4장의 보안 능력 요구 대신 수용할 수 있도록 하되 "on the condition that requirements in UR E26 are complied with"라는 단서를 둔다. 즉 보안 기능은 기본 규격에 내재된 것이 아니라 선택적으로 추가되는 계층이다.

시리얼 구간이 IP 영역과 완전히 분리되어 있지 않은 경우도 보고된다. 보안 업체의 기술보고서[14]는 시리얼-IP 변환장치 3개 제품군에서 신규 취약점 20건을 식별하고, 변환장치를 장악한 공격자가 IP 네트워크를 오가는 시리얼 데이터를 변조할 수 있음을 실험으로 제시하였다. 동 보고서는 변환장치의 적용 사례로 "Critical shipboard systems … including propulsion and steering systems; and the Electronic Chart Display and Information System (ECDIS) used for navigation"을 명시하고, 선박 환경에서 변환장치로 선내 네트워크를 침해할 수 있음이 시연된 사례[17]도 기록하고 있다.

초기 접근 경로에도 3.1의 불확정성이 적용된다. 필수 기준 b)는 노출된 물리 인터페이스가 없을 것을 요구하면서 "Unused interfaces shall be logically disabled"로 이어지므로 정비를 위하여 사용 중인 서비스 포트는 비활성화 대상이 아니다. 필수 기준 c)의 "areas to which physical access is controlled" 역시 누구로부터의 통제인지를 규정하지 않으므로, 선교와 기관구역에 상시 출입하는 정비 인력·검사관·벤더 기술자가 통제 대상에 포함되는지는 판정 주체에 따라 달라질 수 있다.

### 4.2 시스템 범주를 경유한 전이

추가 기준 a)는 제외 대상 CBS가 Category III 기능을 담당하지 않을 것을 제시한다. 다만 이 항목은 "should"로 규정되어 있고 6.4 두문이 추가 기준 미충족 시에도 합리적 설명이 있으면 제외를 수용하도록 하므로 통과 요건이 아니다. 나아가 이 범주는 애초에 보안을 기준으로 정의된 것이 아니다. UR E26 1.3.3은 "System categories are defined in IACS UR E22 on the basis of the consequences of a system failure to human safety, safety of the vessel and/or threat to the environment"라고 규정한다. 즉 범주는 우발적 고장의 안전 결과를 재는 척도이며 의도를 가진 공격자를 상정하지 않는다. 고장의 영향은 기능적 중요도에 비례하는 경향이 있으나, 공격자는 최종 목표가 아닌 시스템을 경유 지점으로 선택한다.

4.1에서 규정한 계측기가 이 경우에 해당한다. 이들은 감시·정보 기능을 담당하므로 낮은 범주로 분류되기 쉬우나, 데이터의 소비자가 아니라 **공급자**이며 그 공급 대상이 상위 범주 시스템이다. 음향측심기가 송출하는 수심이나 선속계가 송출하는 대수속력이 오염되면 ECDIS의 표시가 오염되고, 이는 운항자의 상황 인식 오류로 이어져 조타 판단의 오류를 유발할 수 있다. 자율운항선박과 같이 사람의 판단이 개입하지 않는 구성으로 발전할 경우 오염된 측정값은 자동 조타 및 항로 유지 기능의 직접적인 입력이 된다.

이 가능성은 규칙 자체에서도 부분적으로 인식된다. UR E22[2] 3.2는 Category I 시스템이 통상 선급의 검증 대상이 아니라고 하면서도, 해당 시스템에 관한 정보가 "ensure that they do not influence the operation of systems in category II and category III"를 위하여 요구될 수 있다고 규정한다. 그러나 이를 확인하는 절차는 UR E22와 UR E26 어느 쪽에도 없다. 여기서 범주 분류의 자기정합성 문제가 드러난다. 상위 범주 기능에 영향을 미치는 CBS는 그 영향을 확인한 뒤라야 낮은 범주로 분류할 수 있으나, 바로 그 확인을 제외 판정 단계에서 지시하는 항목이 6.4에 존재하지 않는다.

**표 3. 잔여 위협 예시와 대응 공격 기법**

| 제외 후보 CBS | 관련 조항 | 잔여 위협 | ATT&CK for ICS | 전이의 종착점과 영향 |
|---|---|---|---|---|
| IP 인터페이스 없이 시리얼 링크만 갖는 단일 기능 계측기 (음향측심기, 선속계 등) | 6.4 필수 기준 a) | IP 연결이 없어도 시리얼 경로를 통한 메시지 주입·변조 및 통신 차단이 가능 | T1692 Unauthorized Message (.001 Command, .002 Reporting), T1695.001 Block Communications: Serial COM, T0830 Adversary-in-the-Middle | 수신 측 항해 시스템에 오염된 값 또는 결측이 전달됨 |
| 같음 (61162-1 talker 지위) | 6.4 추가 기준 a) | 낮은 범주로 분류되어 제외된 CBS가 상위 범주 시스템으로 향하는 오염원이 됨 | T1692.002 Unauthorized Message: Reporting Message, T0832 Manipulation of View | ECDIS 표시 오염 → 운항자 상황 인식 오류 → 조타 판단 오류. 자율운항 구성에서는 자동 조타의 직접 입력 |

두 예시에 공통되는 것은 해당 CBS가 제외됨으로써 4.1.1의 자산 목록과 4.3.1의 감시 대상에서도 함께 빠진다는 점이다. 즉 제외된 CBS 자체에서는 위 경로를 통한 침해를 인지할 수단의 확보가 강제되지 않는다. 다만 3.2에서 지적한 바와 같이 시리얼 구간의 감시 공백은 제외 여부와 무관하게 존재하며, 제외는 그 위에 자산 관리와 사고 대응의 강제성 소거를 더한다.

## Ⅴ. 결 론

본 논문은 "UR E26 6.4의 제외 판정 기준은 제외된 CBS를 경유한 사고 전이가 발생하지 않음을 확인하기에 충분한가"라는 질문에 대하여 규칙 조문의 대조 분석을 통해 충분하지 않다고 답한다. 근거는 두 가지이다. 첫째, 초판이 제외 판정 기준의 항목으로 두었던 '전이 여부에 관한 판정 항목'과 'CBS 간 연결 관계의 조사·문서화 요구'가 최종안의 판정 기준에 반영되지 않았다. 전이에 관한 요구 자체는 위험평가의 고려 요소(6.3), 자산 목록의 대상(4.1.1), 적용 범위 밖 시스템의 물리적 분리(4.2.1.3)로 Rev.1에 남아 있으나, 이들은 모두 잔존하는 적용 범위 측에 부과된 설계·관리 의무이며 제외를 판정하는 단계의 조건이 아니다. 둘째, 필수 기준의 표현과 6.4 두문의 "assurance"에 대한 판정 기준·검증 방법, 그리고 위험평가의 방법론이 규칙에 제시되어 있지 않아 제외 판정이 불확정적이다.

이어 본 논문은 이 두 한계가 조문 해석상 배제되지 않는 잔여 위협 경로로 어떻게 남는지를, 시리얼 링크만을 갖는 계측기를 제외 후보로 두고 예시하였다. 두 경우 모두 제외된 CBS 자체에서는 침해의 인지 수단을 확보할 의무가 발생하지 않는다. 여기서 본 논문이 더하는 바는, 강제 규정의 실효성이 요구사항의 강도뿐 아니라 적용 범위에서 이탈하는 경로의 판정 기준에 의하여도 결정된다는 점을 조문 수준에서 보인 것이다.

본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 문제는 판정 기준의 불확정성과 판정 단계의 전이 착안점 부재에 있다. 따라서 전이에 관한 판정 항목의 복원과 판정 표현의 구체화가 필요하다. 전자는 초판 c)·f)의 문안을 6.4의 필수 기준에 되살리는 형태로, 후자는 필수 기준 a)의 판정 경계를 당해 CBS의 인터페이스로 볼 것인지 변환장치를 포함한 경로 전체로 볼 것인지를 규칙에 명시하는 형태로 가능하다.

본 논문은 규칙 문헌의 분석에 기초하며 실선 환경에서의 실증과 선급의 판정 실무에 대한 조사를 포함하지 않으므로, 판정 편차의 존재 여부는 분석 범위를 벗어난다.

## References

[1] IACS, UR E26 Cyber resilience of ships, Rev.1, Nov. 2023.
[2] IACS, UR E22 Computer based systems, Rev.3 Corr.1, Sep. 2025
[3] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
[4] BIMCO, ICS, INTERCARGO, INTERTANKO, OCIMF et al., The Guidelines on Cyber Security Onboard Ships, Version 5, 2024.
[5] IACS, UR E26 Cyber resilience of ships, New (Apr. 2022), IACS Req. 2022, 32 pp. Withdrawn before entry into force on 1 Jan. 2024; see [1] Note 1.
[6] IACS, UR E27 Cyber resilience of on-board systems and equipment, Rev.1, Sep. 2023.
[7] Y. Jo, O. Choi, J. You, Y. Cha, and D. H. Lee, "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," Sensors, vol. 22, no. 5, art. no. 1860, 2022.
[8] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024
[9] 손금준, 최상훈, 강남선, 김성록, "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회논문집, 제61권, 제6호, pp. 427-436, 2024.
[10] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024.
[11] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," Turkish Journal of Maritime and Marine Sciences, vol. 10, Special Issue 1, pp. 31-50, 2024.
[12] MITRE, ATT&CK for ICS, v19.2. https://attack.mitre.org/matrices/ics/ (accessed Aug. 14, 2026).
[13] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013.
[14] Forescout Technologies, New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters, 기술보고서, 2026. (선박 시스템 언급은 §2.1, 신규 취약점 20건은 §3.2)
[15] IEC, IEC 61162-460, Edition 3.0, Apr. 2024.
[16] IACS, Rec.190 Recommendation for Vessel Asset Inventory for Computer-based Systems, Jun. 2025.
[17] K. Munro, "Hacking serial networks on ships," Pen Test Partners, 보안 업체 공개 분석, 2018. https://www.pentestpartners.com/security-blog/hacking-serial-networks-on-ships/

---
