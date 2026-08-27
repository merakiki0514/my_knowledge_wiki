# IACS UR E26 적용 범위 이탈 경로의 한계 분석: 제외 판정과 범위 정의

정성윤¹ · 이대성¹'* / ¹한국해양대학교
E-mail : meraki4.1st@gmail.com / dslee@kmou.ac.kr

An Analysis of Limitations in the Routes out of the Scope of Applicability of IACS UR E26
: Exclusion Assessment and Scope Definition
Sung-yoon Jung¹ · Dae-sung Lee¹'* / ¹Korea Maritime and Ocean University

---

## 요 약

IACS UR E26 Rev.1은 선박 사이버 복원력에 관한 통합규정으로, 2024년 7월 1일 이후 건조계약된 선박에 강제 요구사항을 부과한다. 그러나 동 UR은 6.4의 개별 CBS(컴퓨터기반시스템) 제외와 1.3.2의 영역 단위 범위 정의라는 두 가지 이탈 방식을 함께 둔다. 전자는 Rev.1 6장을 발효 전 철회된 초판과 대조해, 초판이 판정 기준으로 두었던 사고 전이·CBS 간 연결 관계 조사 요구가 최종안에 반영되지 않았고, 6.4의 재량 수용(추가 기준 미충족 시)에 판정 기준과 검증 방법이 없어 판정이 불확정적임을 보인다. 후자는 선내 IT가 시스템이 아니라 인터페이스로만 범위에 들어와 방어가 보안 구역 경계에 위임되는데, 규정은 4.2.1.2에서 경계 침투 가능성을 스스로 진술하면서도 이행 실증은 서비스 거부 시험과 포트 스캔에 그친다. 이어 STRIDE-per-interaction과 ATT&CK for ICS를 결합해 두 방식의 잔여 위협을 체계적으로 도출하고(경로 A 열 가지, 경로 B 한 가지), 그중 두 경로를 시작부터 영향까지의 사슬로 심화한다 — 제외된 계측기의 오염된 값이 상위 항해 시스템에 전달되는 경로와, 요구사항이 미치지 않는 IT 영역에서 출발해 IP로 연결된 자동조타장치·주기관 제어 계통에 이르는 경로이다. 전자는 운항자의 상황 인식을 왜곡하는 데 그치지만 후자는 자동 제어 기능 자체에 작용하며, 성립 조건의 문턱도 후자가 상대적으로 낮다.

## ABSTRACT

IACS UR E26 Rev.1 imposes mandatory cyber resilience requirements on ships contracted on or after 1 July 2024, but also provides two ways for systems to fall outside them: exclusion of individual Computer-Based Systems (CBSs) under Section 6.4, and the scope definition in Section 1.3.2, which limits consideration to the domain level rather than the system level. For the former, comparing Section 6 with the withdrawn first edition shows that its criteria on incident propagation and on investigating and documenting CBS-to-CBS connections were dropped from Rev.1, and that Section 6.4 lets a CBS failing the additional criteria be accepted without any threshold or verification method, leaving the assessment indeterminate. For the latter, shipboard IT enters scope only as interfaces, not as systems, so defence rests on the security-zone boundary; yet although Section 4.2.1.2 itself states that breaching such a perimeter is always possible, compliance demonstration is limited to denial-of-service tests and port scanning. Combining STRIDE-per-interaction with ATT&CK for ICS, this paper derives the residual threats left by each route (ten under exclusion, one under the scope definition) and develops two into chains from initiation to impact: corrupted values from an excluded instrument reaching in-scope navigational systems, and an attack from the unregulated IT domain to the autopilot and main engine control systems over IP. The former only distorts the navigator's situational awareness; the latter acts on automated control itself, with comparatively less demanding preconditions.

**키워드** : 선박 사이버보안, IACS UR E26, 적용 범위 이탈, 제외 판정, 범위 정의, 사고 전이

**Keywords** : Maritime cyber security, IACS UR E26, Scope of applicability, Exclusion assessment, Scope definition, Cyber incident propagation

---

## Ⅰ. 서 론

현대 선박의 항해·기관·화물 계통은 선내 네트워크로 묶여 있고 위성통신을 통해 육상과 상시 연결된다. 이 연결성은 운항과 정비의 효율을 높이는 한편으로 선박을 외부에서 도달할 수 있는 대상으로 만들었다. 더욱이 업무용 정보 계통과 제어 계통이 한 선체 안에 함께 놓이는 구성은 하나의 계통에서 발생한 사고가 다른 계통으로 옮겨 갈 여지를 남긴다[1]. 선박 사이버보안의 문제는 개별 장비의 취약점에 그치지 않고 이 연결의 구조에서 발생한다.

제도적 대응은 민간 단체의 비강제 가이드라인에서 출발하였다. BIMCO를 중심으로 발간한 지침[2]은 기술적 대응 방안을 제시하였으나 이행을 강제하지 못하였다. IMO는 MSC-FAL.1/Circ.3[3]으로 해사 사이버 리스크 관리 지침을 제시하였으나 이 역시 비강제 지침이다. 의무의 근거가 된 것은 결의서 MSC.428(98)[4]로, 동 결의서는 사이버 리스크를 ISM Code에 따른 안전관리체제(SMS)에서 다루도록 요구하였다. 국제선급연합회(IACS)는 구체적인 기술 기준으로 통합규정(UR)을 제정하였다. UR E22[5]는 컴퓨터기반시스템(CBS)의 요구사항과 시스템 범주(Category)를 정의하고, UR E26[6]은 선박 수준의 복원력을, UR E27[7]은 개별 장비의 보안 능력을 다룬다. UR E26 Rev.1은 2024년 7월 1일 이후 건조계약된 선박에 적용되며, 1.3.1이 정하는 선박 부류를 대상으로 한다. 동 규칙은 식별·보호·탐지·대응·복구의 기능 요소별로 요구사항을 구성하고 전 생애주기에 걸쳐 문서 제출과 실증을 요구하며, 적용 대상은 추진·조타·발전 및 배전·화재탐지 등 OT 시스템과 법정 요건이 요구하는 항해·통신 시스템, 그리고 적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스이다.

그러나 UR E26은 요구사항의 적용을 강제하는 동시에 그 적용에서 벗어나는 두 가지 방식을 함께 두고 있다. 하나는 6.4가 규정하는 제외이다. 동 조항은 제외를 위하여 충족하여야 할 기준과 위험수준 평가 시 고려되어야 할 추가 기준을 두며, 제외가 승인된 CBS에는 4장의 요구사항이 적용되지 않는다. 다른 하나는 1.3.2의 범위 정의 자체이다. 앞에서 보았듯 선내 IT 영역은 시스템으로서가 아니라 적용 대상 CBS로부터 향하는 인터페이스로만 범위에 들어오므로, 그 영역은 어떠한 판정도 거치지 않은 채 요구사항의 대상에서 빠진다. 전자는 개별 CBS에 대한 판정을 거치고 후자는 판정 행위 자체가 없다는 점에서 두 방식은 층위가 다르다. 본 연구의 문제의식은 적용 실무에서 특정 CBS를 제외하려는 시도가 반복적으로 관찰되는 데에서 출발하나, 그러한 관찰을 주장의 근거로 삼지 않고 UR 조문을 분석 대상으로 한다.

본 논문이 제기하는 질문은 다음과 같다. UR E26에서 적용 범위를 벗어나는 방식은 그로부터 남는 위협이 통제됨을 확인하기에 충분한지가 그것이다. 벗어나는 방식은 두 가지이다. 하나는 6.4가 규정하는 개별 CBS의 제외이고, 다른 하나는 1.3.2의 범위 정의가 영역 단위로 판단의 대상을 한정하는 것이다. 본 논문은 전자에 대하여 UR E26 Rev.1의 6장을 발효 전 철회된 초판[8]과 대조 분석하고, 후자에 대하여 범위 정의가 의존하는 전제와 그 전제에 관한 이행 실증의 요구를 조문에서 확인한다. 이어 STRIDE-per-interaction과 MITRE ATT&CK for ICS[16]를 결합한 방법론으로 두 방식 각각에서 남는 잔여 위협을 체계적으로 도출하고(경로 A 열 가지, 경로 B 한 가지), 그 가운데 두 경로를 시작부터 영향까지의 사슬로 심화한다. II장에서 선행연구를 정리하고, III장에서 제외 기준과 범위 정의를 분석하며, IV장에서 잔여 위협을 모델링하고, V장에서 결론을 기술한다.

## Ⅱ. 관련 연구 및 배경

선박을 대상으로 한 위협 분석은 상당한 양이 쌓여 있다. 조용현과 차영균[1]은 IEC 61162-450/460 기반 기기 목록에서 대상을 선정하고 이해관계자를 반영한 데이터 흐름도를 수립한 뒤, STRIDE와 Attack Tree로 206건의 위협을 도출하였다. 이후 동 연구진의 일부가 참여한 연구에서는 MITRE ATT&CK 프레임워크를 선박 장비에 적용하여 공격 모델을 제시하였다[9].

UR E26 자체를 대상으로 한 연구도 축적되고 있다. 사이버 복원력의 정의를 조사하고 UR E26을 NIST의 사이버보안 프레임워크 및 사이버 복원력 체계와 비교한 연구[10], UR E26의 요구사항과 IEC 62443 참조 모델을 함께 고려하여 선박 네트워크 토폴로지를 설계한 연구[11], 동 규칙의 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[12]가 있으며, 국외에서는 동 규칙의 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[13]가 발표되었다.

그러나 이들 연구는 공통적으로 규칙을 어떻게 준수할 것인가, 또는 규칙이 다른 프레임워크와 어떻게 다른가를 다룬다. 즉 적용 대상으로 들어온 시스템을 전제하고 그에 무엇을 갖추어야 하는지를 논한다. 그 앞 단계, 곧 무엇이 적용 대상에서 빠지는가는 다루어지지 않는다. 제외에 관하여는 제출·유지 문서의 하나로 언급되거나[12] 규칙의 구성을 소개하는 과정에서 부속 절차로 언급되는[13] 데 그치며, 그 판정 기준이 충분한지는 검토하지 않는다. 범위 정의에 관하여도 적용 대상의 목록으로 소개될 뿐, 그 설정이 무엇을 전제하는지는 물어지지 않는다. 위협모델링 선행연구[1], [9] 역시 선박 시스템 일반 또는 선박 장비 전반을 대상으로 위협을 도출할 뿐, 규칙이 스스로 제외를 허용하거나 범위에서 비운 자리를 특정하여 모델링하지는 않는다. 본 논문이 확인한 범위에서는 UR E26의 적용 범위에서 벗어나는 방식 자체를 분석 단위로 삼아 그 잔여 위협을 도출한 연구가 발견되지 않았다. 본 논문은 이 지점을 다룬다.

## Ⅲ. UR E26의 제외 규정과 범위 정의 분석

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

**셋째, 그러나 전이에 관한 요구 자체가 소멸한 것은 아니다.** 관련 요구는 6.4 밖에 흩어져 남아 있으므로, 본 논문의 주장이 성립하려면 이들이 초판 c)·f)의 자리를 대신하는지를 먼저 검토하여야 한다. 확인되는 조항은 다섯이며 표 3과 같다.

**표 3. 6.4 밖에 잔존하는 전이 관련 조항과 그 성격**

| 조항 | 요구 내용 | 초판 c)·f)를 대신하지 못하는 이유 |
|---|---|---|
| **6.3** | 위험평가의 고려 요소로 "Possible effects related to integration of systems, or interfaces among systems, including systems not onboard" | 이 문구는 **초판과 Rev.1에 동일하게 존재**한다. 초판은 이를 두고도 c)를 판정 기준 목록에 별도로 두었다. 또한 고려할 요소를 열거할 뿐 그 결과가 어떠할 때 제외를 수용하는지는 규정하지 않는다 |
| **4.1.1.1** | 자산 목록의 대상에 "the networks connecting such systems to each other and to other CBSs onboard or ashore"를 포함 | 잔존 CBS 측의 자산 관리 의무이다. 제외된 CBS와의 연결이 상대편 목록에 기재될 여지가 있을 뿐이다 |
| **4.2.1.4.1** | systems integrator가 제출하는 Zones and conduit diagram과 Cyber security design description이 비신뢰 네트워크와의 통신을 "discrete signals, serial communication, and the purpose and characteristics (i.e. protocols and data flows) of IP-based network communication"으로 기술 | 초판 f)의 "duly investigated, understood and documented"에 가장 근접한 잔존 조항이나, **기술(description)의 의무일 뿐 판정 기준이 아니다.** 주체와 시점도 6.4의 수용 판정과 분리되어 있다 |
| **5.1.4 + Appendix I** | "Risk assessment for the exclusion of CBSs"를 설계 단계 제출 문서이자 검사 단계까지 유지되는 문서로 규정 | 초판 6.1·6.3의 "concise list of excluded applications"에 대응하나, **제외의 정당화를 담을 뿐** 통제를 요구하지 않는다 |
| **4.2.1.3** | "Systems, networks or CBSs outside the scope of applicability of this UR are considered untrusted networks and shall be physically segmented from security zones required by this UR" | 전이 경로에 직접 작용하는 강제 요구이다. 다만 곧바로 "Alternatively, it is accepted that such systems are part of a security zone if these OT-systems meet the same requirements as demanded by the zone"이라는 대안을 둔다. **이 판정은 순환적이다** — 4장 요구사항의 적용을 면제받은 CBS가 보안 구역이 요구하는 "the same requirements"를 충족하는지를 다시 판정하여야 하기 때문이다. 결과적으로 제외된 CBS를 물리적 분할 없이 보안 구역에 편입시킬 문언상 통로가 남는다 |

표 3의 다섯 조항은 모두 **잔존하는 적용 범위 측에 부과된 설계·관리 의무**이며, 어느 것도 제외를 승인할지 판정하는 단계의 조건이 아니다. 초판은 전이 여부와 연결 관계 파악을 판정 기준 목록 안에 두어 평가자가 그 시점에 이를 확인하도록 지시하였으나, Rev.1의 6.4에는 대응 항목이 없다. 즉 본 논문이 지적하는 것은 전이에 관한 요구의 부재가 아니라 **제외 판정 단계에서 전이를 확인하도록 지시하는 착안점의 소멸**이다. 나아가 4.2.1.3의 "physically segmented"에 대하여도 판정 기준과 검증 방법이 없으므로 3.1의 불확정성이 그대로 적용된다. 연결 관계의 식별은 Rev.1 이후 발간된 Rec.190[14]에서 자산 목록의 한 항목("to determine that all connections have been identified")으로 다시 나타나지만, 이 역시 비강제 권고의 권장 항목이며 제외 판정의 조건은 아니다.

UR E26 1.3.4가 명시하는 비강제 권고 Rec.166[15]에도 전이에 관한 요구가 있으므로 이를 함께 검토한다. 동 권고 6.5는 기능 요구로 "Impact of cyber incidents should be contained to the network zone of origin"(R1)과 안전 필수 기능의 가용성에 영향을 주는 OT 시스템으로 장애가 확장되는 것을 격리하여 최소화할 것(R2)을 두며, 7.3.2.6은 단일 사고가 시스템의 넓은 부분을 오염시키는 파급을 막도록 기능을 분리할 것("decouple capabilities in order to prevent ripple effects")을 든다. 그러나 이들도 초판 c)·f)의 자리를 대신하지 못한다. 첫째, Rec.166은 비강제 권고이며, 1.3.4는 동일 주제에 관하여 양자의 요구가 다를 경우 UR이 우선한다고 규정한다. 둘째, 위 항목들은 적용 대상 시스템의 설계에 부과되는 기능 요구이지 개별 CBS를 제외할지 판정하는 기준이 아니다. 셋째, 본 논문이 확인한 범위에서 Rec.166에는 개별 시스템을 적용 대상에서 배제하는 절차 자체가 없다. 오히려 동 권고 2.2는 적용 대상을 OT 시스템과 함께 "other systems which are connected to onboard OT systems in a way that may affect their operation (as identified by risk assessment)"로 규정하여, 연결과 영향의 관계 자체를 적용 범위를 정하는 척도로 삼는다. UR E26은 적용 범위를 1.3.2의 열거로 정하고 6.4에 개별 제외를 둔다. 두 문서는 적용 대상을 정하는 방식이 다르며, 강제 문서인 UR 쪽의 제외 판정 기준에 전이에 관한 항목이 남지 않았다는 것이 본 절의 확인이다.

다만 초판은 2024년 1월 1일 발효 이전에 철회되었으므로, 위 변경은 시행 중인 요구사항이 완화된 것이 아니라 제정 과정에서 최종안에 반영되지 않은 것으로 이해하여야 한다. IACS는 변경 사유를 공개한 바 없으므로 본 논문은 변경의 의도를 추정하지 않으며, 그 결과로 남은 조문의 상태만을 분석 대상으로 한다.

### 3.4 범위 정의에 의한 이탈과 경계 통제의 전제

3.1부터 3.3까지는 6.4의 제외를 다루었다. 개별 CBS를 판정을 거쳐 요구사항의 적용에서 배제하는 절차이다. 그러나 UR E26의 적용 범위에서 벗어나는 방식이 이것 하나는 아니다. 1.3.2의 범위 정의 자체가 또 하나의 방식을 이루며, 두 가지는 층위가 다르다.

**표 4. 적용 범위에서 벗어나는 두 방식**

| | 6.4 제외 | 1.3.2 범위 정의 |
|---|---|---|
| 작동 단위 | 개별 CBS | 영역 |
| 판정 | 선급이 수용 여부를 판정 | 판정 행위가 존재하지 않음 |
| 문서화 | 6.1의 위험평가, 5.1.4·Appendix I의 제출·유지 문서 | 없음 |
| 본 논문에서 | 3.1~3.3, 4.2, 4.5 | 본 절, 4.3, 4.4 |

1.3.2 a)는 추진·조타·계류·발전 및 배전·화재탐지 등의 OT 시스템과 법정 요건이 요구하는 항해·통신 시스템을 적용 대상으로 열거한다. b)가 여기에 더하는 것은 시스템이 아니라 인터페이스이다. 적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스, 곧 "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems"가 그것이다. 인터페이스가 향하는 상대편으로는 여객 서비스 시스템과 여객용 네트워크, 관리 네트워크, 승무원 복지 시스템이 열거되고, 마지막에 "any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)"가 덧붙는다. 따라서 선내 업무망과 여객망, 승무원 복지 시스템, 정비를 위하여 일시적으로 연결되는 장비는 그 자체로는 요구사항이 적용되는 대상이 아니다.

이것이 UR E26이 IT 영역을 고려하지 않는다는 뜻은 아니다. 4.2.1.3은 적용 범위 밖의 시스템·네트워크·CBS를 비신뢰 네트워크로 간주하고 보안 구역으로부터의 물리적 분할을 요구하며, 4.2.1.1은 보안 구역이 "isolated (i.e. air gapped)"인 상태와 "connected to other security zones or networks"인 상태를 나란히 두고 후자의 경계 수단으로 "firewalls/routers, simplex serial links, TCP/IP diodes, dry contacts"를 예시한다. 즉 규정이 요구하는 것은 그 영역 자체의 보안 수준이 아니라 그 영역과의 경계에서 이루어지는 통제이다. 이 구성에서 IT 영역으로부터 유입되는 위협에 대한 방어는 경계에 위임된다.

그리고 그 위임이 무조건 성립하지는 않는다는 것은 규정 자신의 진술이기도 하다. 4.2.1.2는 표제를 Rationale로 두고 망을 왜 분할하여야 하는지를 밝히는데, 그 서두가 다음과 같다. "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, breaching that perimeter is always possible." 방화벽으로 둘레를 두르고 침입 탐지·차단 장치로 유입 트래픽을 감시하더라도 그 둘레를 뚫는 일은 언제나 가능하다는 것이며, 분할은 그 전제 위에서 공격의 확산을 어렵게 하는 수단으로 제시된다.

그 가능성의 확인 여부는 경계 보호를 다루는 4.2.2의 이행 실증 요구에서 드러난다. 설계 단계(4.2.2.4.1)와 건조 단계(4.2.2.4.2)가 모두 "No requirements"이고, 요구가 부과되는 것은 시운전 단계(4.2.2.4.3) 하나이다. 그 내용은 세 가지로, 구역 경계 보호 장치를 대상으로 하는 서비스 거부 시험, 각 네트워크 세그먼트 내부에서 발신되는 과도한 데이터 흐름에 대한 서비스 거부 시험, 그리고 불필요한 기능·포트·프로토콜·서비스가 공급자의 하드닝 지침에 따라 제거되었는지를 분석적 평가와 포트 스캔으로 확인하는 것이다. 뒤의 두 시험은 CBS 인증 과정에서 수행되었다면 생략할 수 있다. 세 시험이 보는 것은 경계 장치가 부하를 견디는지, 그리고 불필요한 노출면이 남아 있는지이다. 경계가 우회될 수 있는지 자체를 확인하는 시험은 요구되지 않는다.

여기서 3.1의 불확정성이 다른 형태로 나타난다. 6.4에서는 판정 기준이 존재하되 그 기준을 적용할 척도와 검증 방법이 규정되어 있지 않았다. 1.3.2에서는 판정이라는 행위 자체가 없고, 그 범위 설정이 의존하는 전제를 확인하는 시험도 요구되지 않는다. 두 방식은 이렇게 성격이 다르므로 하나로 묶어 다루지 않는다. Ⅳ장은 각각에서 남는 잔여 위협을 체계적으로 도출하고, 그 가운데 두 경로를 심화한다.

## Ⅳ. 잔여 위협의 체계적 모델링

Ⅲ장은 두 이탈 경로 각각에서 판정 또는 전제가 불확정적임을 조문 대조로 확인하였다. 본 장은 그 불확정성이 실제로 남기는 위협을 체계적으로 도출한다. 4.1은 분석 단위(신뢰 경계)와 방법론을 정의한다. 4.2와 4.3은 각각 경로 A(6.4 제외)와 경로 B(1.3.2 범위 정의)에서 남는 잔여 위협을 조항 단위로 매핑한다. 4.4와 4.5는 그 가운데 두 경로를 선택하여 시작부터 영향까지의 사슬로 심화한다.

### 4.1 신뢰 경계와 방법론

**신뢰 경계.** 선행연구는 대체로 육상-선박 또는 선박-외부의 경계를 신뢰 경계로 설정한다[1], [9]. 본 논문의 분석 단위는 이와 다르다. 문제의식이 "무엇이 UR E26의 적용 대상에서 벗어나는가"에 있으므로, 신뢰 경계도 **UR E26 4장의 요구사항이 적용되는 CBS와 그렇지 않은 CBS 사이**에 긋는다. 이 경계의 안쪽에는 추진·조타·발전 및 배전·화재탐지 등 UR E26 1.3.2 a)가 열거하는 OT 시스템과 법정 항해·통신 시스템이 있고, 바깥쪽에는 두 부류가 있다. 하나는 6.4의 제외 판정을 통과하여 범위를 벗어난 CBS(경로 A)이고, 다른 하나는 1.3.2의 범위 정의에 의하여 처음부터 시스템으로서는 범위에 들어오지 않는 선내 IT 영역(경로 B)이다. 이 구도는 대상 선박의 전형적인 구성에 대응한다. 선내망은 흔히 시리얼 기반의 OT 세그먼트(통합제어감시시스템(ICMS) 하위의 항해·기관·안전·화재탐지·화물 계통)와 IP 기반의 LAN(선내 업무망, CCTV, 승무원 복지용 PC, 스마트십 솔루션)으로 나뉘며, 후자는 위성통신(VSAT)이나 무선망을 통하여 육상과 상시 연결된다. 두 세그먼트의 경계에는 방화벽이 놓인다. 경로 A의 후보는 OT 세그먼트 안에서 제외 판정을 받는 개별 CBS이고, 경로 B는 이 LAN 세그먼트 전체에 해당한다.

**방법론.** STRIDE나 ATT&CK for ICS를 단독으로 적용하는 것은 선행연구의 재탕이 된다. 선박 장비 전반에 DFD를 수립하고 STRIDE와 Attack Tree로 위협을 도출한 연구[1]와 ATT&CK 프레임워크로 선박 장비의 공격 모델을 제시한 연구[9]가 이미 있기 때문이다. 본 논문은 두 방법을 다음과 같이 결합한다. 먼저 **STRIDE-per-interaction**으로 신뢰 경계를 넘나드는 개별 인터페이스(시리얼 문장, 물리 포트, 원격 접속, IP 인터페이스)마다 무엇이 가능한지를 도출한다. 이 단계의 산출은 규정이 통과시키는 CBS의 성질로부터 연역되므로, 그 자체로는 발생 여부를 주장하지 않는다. 다음으로 **ATT&CK for ICS 매핑**으로 그 가능성이 실제로 관측된 기법에 대응하는지를 확인한다. 이 이중 구성이 뜻하는 바는, STRIDE 단계의 산출 가운데 대응하는 ATT&CK 기법이나 선행 사례가 없는 항목은 사변으로 남긴다는 것이다. 두 방법의 결합 자체는 신규성의 근거가 아니다. 본 논문의 신규성은 이 방법론이 적용되는 **대상**에 있다 — 선박 시스템 일반이 아니라, **UR E26이 스스로 제외를 허용하거나 범위에서 비운 자리**가 분석 단위이다.

**잔여 위협의 정의.** 본 논문에서 잔여 위협이라 부르는 것은 다음 두 조건 중 하나를 만족하는 위협이다. (a) 경로 A: 6.4의 필수 기준 4개와 추가 기준 3개를 모두 충족한 상태에서도 성립하는 위협. 어느 한 기준이라도 충족하지 못하면 애초에 제외가 성립하지 않으므로 본 논문의 분석 대상이 아니다. (b) 경로 B: 1.3.2가 정의하는 범위 밖 IT 영역, 곧 판정 자체가 없는 영역에서 성립하는 위협. 이 정의에 따라 4.2와 4.3의 매핑표는 각 행마다 "어떤 조항의 어떤 문구가 이 위협을 통과시키는가"를 먼저 밝히고, 그 다음에 잔여 위협을 서술하는 순서를 취한다.

**범위.** 본 장은 정성적 매핑과 서사적 시나리오로 구성되며, IMO FSA 방식의 정량적 위험도 산정, 기존에 설치된 방벽의 목록화, 완화 방안의 제시, 실선 환경에서의 실증은 포함하지 않는다. 이들은 후속 연구(2단계 testbed)의 몫이다.

### 4.2 경로 A(6.4 제외)의 잔여 위협

경로 A의 잔여 위협은 6.4의 필수 기준 4개와 추가 기준 3개를 **모두 충족한 CBS에서도** 남는 것들이다. 표 5는 이를 필수·추가 기준 단위로 정리한다. R1~R10의 번호는 이후 서술과 4.5의 참조를 위하여 붙인다.

**표 5. 경로 A(6.4 제외)의 잔여 위협 매핑**

| # | 통과되는 기준 | 기준이 통과시키는 것의 한계 | 잔여 위협 | ATT&CK for ICS |
|---|---|---|---|---|
| R1 | 필수 a) | "IP-network connections" 부재만 요구, 시리얼 연결은 제한하지 않음 | NMEA 0183·RS-485·Modbus RTU 등은 인증·암호화·무결성이 없어 물리 접속만으로 메시지 주입·변조 가능. 4.2.1.1은 zone 연결 수단으로 simplex serial links를 명시 허용하고 4.2.1.4.1은 비신뢰 네트워크 기술서에 discrete signals·serial communication 포함을 요구한다 — 규정은 시리얼의 존재를 인지하면서도 제외 판정에서는 IP 연결 유무만을 본다[17], [23], [24] | T1692.001/.002 Unauthorized Message, T1695.001 Block Communications: Serial COM, T0830 Adversary-in-the-Middle, T0842 Network Sniffing |
| R2 | 필수 a) | 격리의 정의가 IP 연결 유무로 한정 | USB, 정비용 노트북, 무선(Wi-Fi/BLE), 위성단말 백채널 등 비IP 경로 전체가 판정의 시야 밖에 남음. 위성단말 백채널은 VSAT 위협모델링 문헌[26]이 별도로 다룸 [확인필요 — USB·정비용 노트북·무선 Wi-Fi/BLE 경로에 대한 1차 문헌 미확보] | T0847 Replication Through Removable Media, T0864 Transient Cyber Asset, T0860 Wireless Compromise, T0887 Wireless Sniffing |
| R3 | 필수 b) | "accessible"·"logically disabled"의 판정 기준이 규정에 없음 | 디버그 UART·JTAG·내부 헤더·서비스 커넥터는 케이스 개방 시 노출되며, 논리적 비활성화는 펌웨어 수준에서 복구될 수 있음[29] | T1693 Modify Firmware, T0862 Supply Chain Compromise |
| R4 | 필수 c) | 구역 지정의 근거·수준·검증 방법이 규정에 없음 | 브릿지·기관실은 정박 중 검사관·기술자·항만 인력·벤더가 상시 출입하나, 6.4에는 출입 로깅·이중 통제·감사에 관한 요구가 없음 [확인필요 — 항만 정박 중 승선 인원에 관한 통계·문헌] | T0864 Transient Cyber Asset, T0847 Replication Through Removable Media |
| R5 | 필수 d) | 배제 대상이 "다기능 통합제어시스템"으로 한정되어, 단일기능 CBS는 후보로 남음(3.3 참조) | 단일기능 CBS도 상위 통합시스템(ICMS)이나 육상으로 데이터를 중계하면 그 시스템의 무결성 원천이 됨. Smart ship solution이 대표적 예이다[19], [26] | T0832 Manipulation of View, T0829 Loss of View, T0882 Theft of Operational Information |
| R6 | 추가 a) | Category는 고장 결과 기준이지 공격 기준이 아님(3.1 참조) | Cat I 자산이 Cat II·III 자산으로 가는 피벗이 될 수 있으나 6.4에 전이 검증 절차가 없고, UR E22[5] 3.2는 "Cat I이 Cat II·III에 영향 없어야 한다"면서 검증 방법을 제시하지 않음[21], [27] | T0867 Lateral Tool Transfer, T0859 Valid Accounts, T0866 Exploitation of Remote Services |
| R7 | 추가 b) | "Known"으로 한정되어 미공개·독자 프로토콜 취약점은 판정 대상 밖(3.3 참조) | 선박 장비는 폐쇄형 독자 프로토콜의 비중이 높아 CVE가 존재하지 않는 경우가 다수임 — R3와 근거를 공유한다[29] | T0862 Supply Chain Compromise |
| R8 | 추가 c) | 공격면 최소화에 정량 기준·측정 방법이 없음(3.1 참조) | [확인필요 — 정성 평가 방법론의 재현성에 관한 1차 자료 미확보. rules/의 관련 해설본은 IACS 원문이 아니므로 인용하지 않는다] | — |
| R9 | 전체 | 제외된 CBS는 4.1.1 자산목록·4.3.1 감시·4.4.1 사고대응계획에서 함께 배제됨(3.2 참조) | 침해가 발생해도 탐지·대응 수단의 확보가 강제되지 않아, "감시받지 않는 노드"가 명세상 보장됨[28] | T0872 Indicator Removal on Host, T0878 Alarm Suppression |
| R10 | 전체 | 6.4는 CBS를 개별 단위로만 심사 | 제외된 CBS가 다수 누적될 때 결합되는 공격면을 평가하는 절차가 없음 [추론 — 선행 문헌 미확인] | — |

R1과 R5는 서로 다른 마디에서 결합하여 하나의 경로를 이룬다. R1은 회선의 **조작 가능성**을, R5는 그 조작된 값이 상위 시스템으로 **전달되는 경로**를 규정한다. 4.5는 이 결합을 계측기 사례로 구체화한다.

### 4.3 경로 B(1.3.2 범위 정의)의 잔여 위협

경로 B는 판정 자체가 없으므로 표 5와 같은 조항별 매핑이 성립하지 않는다. 대신 3.4에서 확인한 범위 정의와 경계 통제 전제 전체가 하나의 항목(R11)을 이룬다.

**표 6. 경로 B(1.3.2 범위 정의)의 잔여 위협 매핑**

| # | 관련 조항 | 조항이 통과시키는 것의 한계 | 잔여 위협 | ATT&CK for ICS |
|---|---|---|---|---|
| R11 | 1.3.2 b) | 선내 IT를 시스템이 아니라 "적용 대상 CBS로부터 다른 시스템으로 향하는 IP 기반 통신 인터페이스"로만 범위에 넣음(3.4 참조) | 선내 업무망·여객망·CCTV·무선망·스마트십 솔루션·정비용 임시 연결 장비가 시스템으로서는 판정 대상이 아니며, 방어는 보안 구역의 경계(4.2.1.1)와 비신뢰 네트워크 간주(4.2.1.3)에 위임됨. 경계 침투가 "always possible"이라는 규정 자신의 진술(4.2.1.2)에도 불구하고, 이행 실증은 설계·건조 단계 "No requirements", 시운전은 서비스 거부 시험과 포트 스캔에 그침(3.4 참조) | T0819 Exploit Public-Facing Application, T0822 External Remote Services, T0866 Exploitation of Remote Services, T0867 Lateral Tool Transfer, T0859 Valid Accounts |

R11은 R1~R10과 층위가 다르다. R1~R10은 6.4의 명시적 제외를 통과한 CBS의 잔여 위협이지만, R11은 1.3.2의 범위 정의로 인하여 애초에 판단 대상에 들어오지 않는 영역의 문제이다. 4.4는 이 항목을 kill-chain으로 심화한다.

### 4.4 심층 시나리오 — IT 영역에서 제어 계통에 이르는 경로

R11이 서술하는 것은 방어가 경계에 위임된다는 사실이지, 그 경계가 어떻게 넘어지는지는 아니다. 본 절은 그 과정을 시작부터 영향까지의 사슬로 구체화한다. 표시되는 값이 아니라 **제어 자체**에 작용한다는 점에서 4.5가 다루는 경로와 구별된다.

**출발점 — 요구사항이 미치지 않는 영역.** 선내 업무망과 여객망, 승무원 복지 시스템, 정비를 위하여 일시적으로 연결되는 장비는 그 자체로는 UR E26의 요구사항이 적용되는 대상이 아니며, 이들로부터의 방어는 보안 구역의 경계에 위임된다. 운용의 측면에서도 이 영역은 OT 계통에 비하여 관리의 우선순위가 낮게 놓인다. 본 절은 이 영역을 출발점으로 삼는다.

한 가지를 먼저 짚어야 한다. 4.2.1.3이 요구하는 물리적 분할이 그대로 관철되면 아래의 경로는 성립하지 않는다. 그러나 동 조항은 3.3에서 검토한 "Alternatively, it is accepted that such systems are part of a security zone if these OT-systems meet the same requirements as demanded by the zone"이라는 대안을 함께 두고, 4.2.1.1은 연결된 보안 구역을 격리된 구역과 나란히 두면서 그 경계 수단으로 방화벽과 라우터를 예시한다. 즉 규정은 분할만을 전제하지 않으며, 연결이 존재하고 그 경계에서 통제가 이루어지는 구성을 함께 상정한다. 아래는 그 구성을 대상으로 하며, 경계 침투가 언제나 가능하다는 4.2.1.2의 진술이 선박 환경에서 무엇을 뜻하는지를 하나의 경로로 구체화한 것이다.

**초기 접근과 잠복.** 이 영역에 이르는 통로는 실재한다. 보안 업체의 기술보고서[19]는 초기 접근 경로로 인터넷에 노출된 VPN 집선장치와 침해된 IT 워크스테이션을 들며, 전자는 2025년 폴란드의 사례로 보고된 것이다. 선박 장비에서도 위성통신 단말의 웹 관리 구성요소에서 원격 코드 실행이 가능한 취약점이 보고되었다(CVE-2023-44857, CVSS 3.1 기준 8.1)[22]. 이 취약점은 인증을 전제하므로 그 자체로 경계를 여는 것은 아니나, 선내 IT 영역에 웹 인터페이스를 갖는 장비가 존재하고 그것이 공격 표면을 이룬다는 사실을 보인다. 이러한 진입 이후 악성코드가 즉시 작동하지 않고 잠복하는 형태는 제어 환경의 사고에서 반복적으로 관측되어 왔다[28]. 대응하는 기법은 T0819 Exploit Public-Facing Application과 T0822 External Remote Services이다.

**경계 통과.** 산업제어시스템에서는 IT 망을 침투한 뒤 양쪽 환경에 모두 접근 가능한 시스템을 경유하여 OT 망으로 이동하고, 그로부터 통상 격리된 망 구간에 놓이는 엔지니어링 워크스테이션을 감염시켜 안전계장시스템의 컨트롤러에 이른 사례가 보고되었다[21]. 격리된 것으로 관리되던 구간이 도달되었다는 점에서 이 사례는 경계 통제가 무조건 성립하지는 않음을 보인다. 선박 환경에서도 시리얼-IP 변환장치를 이용하여 선내 네트워크를 침해할 수 있음이 시연된 바 있다[20]. 대응하는 기법은 T0866 Exploitation of Remote Services와 T0886 Remote Services이다. 본 논문은 특정 선박에서 이러한 경계 통과가 어떤 조건에서 성립하는지를 다루지 않는다. 필요한 것은 그러한 경로가 **보고된 바 있다**는 사실이며, 이는 앞서 인용한 4.2.1.2의 진술과도 어긋나지 않는다.

**표적의 구성 — 단일 경계가 아니다.** 여기서 표적을 명확히 해 둘 필요가 있다. 자동조타장치와 주기관 원격제어 계통은 통상 서로 다른 보안 구역에 속하므로, 둘 모두에 도달하려면 원칙적으로 서로 다른 두 차례 이상의 경계 통과가 필요하다. 아래 시나리오가 상정하는 것은 두 계통이 통합제어감시시스템(ICMS)이나 통합선교시스템(IBS)과 같은 공통 백본에 연결되어, 그 백본에 이르는 하나의 경계를 통과하면 두 계통 모두에 대한 명령 경로가 열리는 구성이다. 이러한 통합이 존재하지 않는 선박에서는 아래 경로가 계통별로 별도의 경계 통과를 필요로 하며, 이는 공격의 난이도를 높이는 요인이다.

**표적과 영향.** 이 경로의 표적은 IP로 연결된 제어 계통, 곧 자동조타장치와 주기관 원격제어 계통이다. 이들은 UR E26 1.3.2가 적용 범위에 명시한 추진 및 조타 기능에 해당하므로 4장의 요구사항이 적용되며, UR E22의 범주로도 상위에 놓인다. 그럼에도 공격의 출발점이 되는 영역에는 요구사항이 미치지 않는다. 표적에 도달한 공격자가 정규 형식의 제어 명령을 발행하면(T1692.001 Unauthorized Message: Command Message) 침로와 기관 출력이 조작될 수 있다(T0831 Manipulation of Control). 다만 그 귀결을 "조종 불능"으로 단정할 수는 없다. 조타에는 통상 수동·NFU(non-follow-up) 전환 경로가, 기관에는 국소 제어반과 하드와이어드 트립 인터록이 법정 요건으로 존재하며, 이들은 자동 제어 계통과 물리적으로 분리된 백업 수단이다. 본 논문이 다루는 것은 이 백업 경로 자체의 무력화가 아니라, **자동 제어 계통에 대한 명령 개입이 성립한다는 것**이다. 그 귀결은 표시의 왜곡이 아니라 자동 제어 기능의 상실(T0880 Loss of Safety)이며, 수동 대체가 즉시 개입되지 않는 구간(전환 지연, 무인기관실의 야간 당직 등)에서 그 영향이 커진다. 백업 경로가 능동적으로 무력화되는 시나리오는 본 논문의 범위 밖이다.

R1과 R11을 가르는 것은 개입의 깊이이다. 4.5가 다루는 R1·R5 결합은 값을 바꾸어 사람의 판단을 오도하고, 본 절의 R11은 사람의 판단을 거치지 않고 자동 제어에 직접 작용한다. 두 경로의 공통점은 출발점이 모두 UR E26의 요구사항이 미치지 않는 지점이라는 데에 있다.

**표 7. IT 영역에서 출발하는 경로**

| 단계 | 내용 | ATT&CK for ICS |
|---|---|---|
| 출발 | 1.3.2 b)가 범위에 넣는 것은 IT 시스템이 아니라 그 시스템으로 향하는 IP 인터페이스. 4.2.1.3은 해당 영역을 비신뢰 네트워크로 간주 | — |
| 초기 접근 | 인터넷에 노출된 원격 접속 설비, 침해된 업무용 단말, 웹 인터페이스를 갖는 선내 장비 | T0819 Exploit Public-Facing Application, T0822 External Remote Services |
| 경계 통과 | 양쪽 환경에 모두 접근 가능한 시스템을 경유한 이동. 4.2.1.2가 경계 침투의 가능성을 명시 | T0866 Exploitation of Remote Services, T0886 Remote Services |
| 제어 개입 | 공통 백본(ICMS/IBS)을 전제로, IP로 연결된 자동조타장치·주기관 원격제어 계통에 정규 형식의 명령 발행 | T1692.001 Unauthorized Message: Command Message |
| 영향 | 침로 및 기관 출력의 조작 — 자동 제어 기능의 상실. 법정 백업 경로(수동/NFU 전환, 국소 제어)의 무력화는 본 논문의 범위 밖 | T0831 Manipulation of Control, T0880 Loss of Safety |

### 4.5 대비 사례 — 제외된 계측기를 경유한 데이터 오염

R1과 R5가 결합하는 경로를 계측기 사례로 구체화한다. 4.4의 경로와 달리 값을 바꾸어 사람의 판단을 오도하는 데 그치므로, 아래에서는 성립 조건이 좁다는 점을 함께 짚는다.

**제외 후보 CBS.** 6.4에 따르면 IP 네트워크 연결이 없고(필수 a), 노출된 물리 인터페이스가 없으며(필수 b), 접근이 통제되는 구역에 설치되고(필수 c), 통합제어시스템이 아니며(필수 d), Category III 기능을 담당하지 않는(추가 a) 단일 기능 기기가 제외 후보가 된다. 선교에 설치되는 단독 계측기가 이 성격에 부합한다. 음향측심기, 선속계 등은 자체 IP 스택을 갖지 않고 IEC 61162-1 시리얼 링크의 talker로서 측정값을 송출하며, 그 값은 전자해도표시시스템(ECDIS)과 자동조타장치에 입력된다. ECDIS와 자동조타장치는 이 구성에서 제외되지 않은 채 적용 범위 안에 남아 있는 시스템으로 둔다.

이 구성은 시리얼 링크의 물리계층 구조와 정합한다. IEC 61162-1은 단방향 simplex의 single-talker/multiple-listener 구조이므로, listener 위치의 기기는 회선을 구동할 수 없어 상위 시스템으로 문장을 주입할 수 없다. 반면 talker 위치의 계측기는 정상 동작으로서 회선을 구동한다. 수신 측이 아무런 검사를 하지 않는다는 뜻은 아니다. IEC 61162-1 문장은 체크섬과 유효성 플래그를 가지며 수신 장비는 입력의 상실이나 무효를 경보로 현시한다. 다만 이들은 전송 오류와 기기 고장을 검출하기 위한 수단이며, 문장의 출처를 **암호학적으로 인증**하는 수단은 규격에 없다. 시리얼 통신이 그 자체로 안전하다는 인식은 선행 연구에서 이미 반박되었다. 장지웅과 김휘강[17]은 시리얼 기반 DNP3.0 통신의 내재적 보안성이라는 통념을 탭핑 실험으로 반박하였다(대상은 육상 전력 제어시스템이므로 본 논문은 선행 사례로만 인용한다). IEC 61162 계열에서도 보안 요구사항은 기본 규격이 아니라 별도의 add-on 표준인 IEC 61162-460[18]에 규정된다.

**필수 기준 a)의 판정 경계와 4.2.1.3의 적용 여부.** 이 요건의 불확정성은 규칙 자신의 용어법에서도 확인된다. 6.4 필수 a)는 격리를 "isolated (i.e, have no IP-network connections to other systems or networks)"로 정의하는 반면, 4.2.1.1은 보안 구역에 대하여 "Security zones shall either be isolated (i.e. air gapped) or connected to other security zones or networks…"라고 하여 동일한 용어를 air gap으로 정의한다. 같은 규칙 안에서 같은 용어가 서로 다른 두 상태를 가리키며, 두 정의 사이에는 시리얼 링크만을 갖는 CBS라는 간극이 놓인다. 이 계측기는 6.4의 정의로는 격리되어 있고 4.2.1.1의 정의로는 격리되어 있지 않으며, 변환장치를 CBS의 경계에 포함시키는지에 따라 판정이 뒤집힐 수 있다. 본 논문은 이 가운데 6.4 문언 자체가 가리키는 대상, 곧 문언 기준을 작업가정으로 채택한다. 이 계측기가 적용 범위 내 시스템에 시리얼로 배선되어 있으면 3.3의 4.2.1.3("physically segmented")과 충돌하는 것처럼 보일 수 있으나, 이 지점 역시 3.1과 같은 성격의 판정 불확정성으로 다루어야 한다. 4.2.1.1이 simplex serial link를 구역 간 통제 수단으로 명시하므로 그러한 배선을 규칙이 허용하는 conduit으로 볼 여지가 있는 한편, 4.2.1.3의 문언("outside the scope of applicability of this UR")이 6.4로 제외된 CBS까지 가리키는지는 규칙에 명시되어 있지 않다. 본 논문은 이 가운데 어느 쪽이 옳다고 단정하지 않으며, 두 해석이 모두 가능하다는 사실 자체가 3.1의 불확정성이 4.2.1.3의 적용 범위에서도 반복됨을 보여준다는 점만을 논거로 삼는다.

**초기 접근 경로.** 필수 기준 c)는 판정 대상을 CBS가 설치된 구역으로 한정하므로, 트랜스듀서·센서 본체가 놓이는 선저 탱크·마스트·갑판 접속함이나 거주구역·케이블 트레이를 지나는 배선은 판정 대상에 포함되는지가 불분명하다. 필수 기준 b)의 "Unused interfaces shall be logically disabled"는 사용 중인 서비스 포트를 대상으로 하지 않으므로, 계측기의 설정·교정용 양방향 포트를 통하여 정비 인력이나 벤더 기술자가 접근하는 경로는 비활성화 대상이 아니다. 이 경로는 ATT&CK for ICS의 T0864 Transient Cyber Asset(정비용 단말의 일시 접속)과 T0862 Supply Chain Compromise(교정 도구·펌웨어 공급망 경유)에 대응한다. 다만 이 경로 자체가 성립하려면 정비 인력으로 위장하거나 그 접근 권한을 탈취하는 별도의 단계가 필요하며, 4.4의 경계 통과보다 성립 조건이 좁다.

**추가 기준 a)를 경유한 전이.** 추가 기준 a)는 "should"로 규정되어 통과 요건이 아니며, 판정 척도로 삼는 UR E22의 시스템 범주는 고장의 안전 결과를 재는 척도이지 공격을 상정하지 않는다(3.1 참조). 계측기는 감시·정보 기능을 담당하므로 낮은 범주로 분류되기 쉬우나 데이터의 소비자가 아니라 **공급자**이며, 선속계가 송출하는 대수속력은 레이더·ARPA의 sea-stabilized 연산 입력이 되어 그 변조가 최근접점·최근접시간의 오판으로 이어진다. 다만 이 회선 조작 단계는 물리적으로 시리얼 회선을 절단하고 in-line 장치를 삽입하는 절차를 전제하므로, 필수 기준 b)·c)가 요구하는 물리 접근 통제·미노출 인터페이스 상태와 정면으로 충돌한다. 즉 이 경로가 성립하려면 앞의 초기 접근 단계가 이미 그 통제를 무너뜨린 상태여야 한다.

두 경우 모두 오염된 값이 이르는 곳은 운항자의 상황 인식이며, 자율운항선박과 같이 사람의 판단이 개입하지 않는 구성으로 발전할수록 그 값은 자동 조타 기능의 직접적인 입력이 된다.

**표 8. 제외된 계측기를 경유한 잔여 위협 경로**

| 단계 | 근거 조항과 그 한계 | ATT&CK for ICS |
|---|---|---|
| 제외 | 필수 a)~d)와 추가 a)를 충족하는 시리얼 talker 계측기가 적용 범위에서 배제됨 | — |
| 초기 접근 | 필수 c)가 평가하는 것은 CBS 설치 구역이지 케이블 경로가 아니며, 필수 b)의 "Unused"는 사용 중인 서비스 포트를 대상으로 하지 않음 | T0864 Transient Cyber Asset, T0862 Supply Chain Compromise |
| 회선 조작 | 필수 a)가 IP 연결만을 판정 대상으로 삼아 시리얼 링크가 제한되지 않음. 다만 in-line 장치 삽입은 필수 b)·c)의 충족 상태와 충돌 | T1692.002 Unauthorized Message: Reporting Message, T0830 Adversary-in-the-Middle, T1695.001 Block Communications: Serial COM |
| 전이 | 추가 a)의 근거인 시스템 범주가 안전 척도이며, 저범주 talker가 상위 범주에 데이터를 공급함(R5) | T0832 Manipulation of View |
| 영향 | 대수속력 변조 → 레이더·ARPA 진벡터 오류 → 최근접점·최근접시간 오판. 자율운항 구성에서는 자동 조타의 직접 입력 | — |
| 미인지 | 제외로 4.1.1 자산 목록과 4.3.1 감시 대상에서 함께 배제됨(R9) | — |

이 경로에서 확인되는 것은, 제외된 CBS 자체에서는 위 침해를 인지할 수단의 확보가 강제되지 않는다는 점이다. 다만 3.2에서 지적한 바와 같이 시리얼 구간의 감시 공백은 제외 여부와 무관하게 존재하며, 제외는 그 위에 자산 관리와 사고 대응의 강제성 소거를 더한다.

## Ⅴ. 결 론

본 논문은 "UR E26에서 적용 범위를 벗어나는 방식은 그로부터 남는 위협이 통제됨을 확인하기에 충분한가"라는 질문에 대하여 UR 조문의 분석을 통해 충분하지 않다고 답한다. 6.4의 제외에 관한 근거는 두 가지이다. 첫째, 초판이 제외 판정 기준의 항목으로 두었던 '전이 여부에 관한 판정 항목'과 'CBS 간 연결 관계의 조사·문서화 요구'가 최종안의 판정 기준에 반영되지 않았다. 전이에 관한 요구 자체는 위험평가의 고려 요소(6.3), 자산 목록의 대상(4.1.1), 적용 범위 밖 시스템의 물리적 분할(4.2.1.3) 등으로 Rev.1에 남아 있고 비강제 권고 Rec.166에도 기능 요구로 존재하나, 이들은 모두 잔존하는 적용 범위 측에 부과된 설계·관리 의무이거나 강제력이 없는 권고이며 제외를 판정하는 단계의 조건이 아니다. 둘째, 6.4는 추가 기준 미충족 시에도 합리적 설명에 의한 수용을 허용하는 재량을 두면서, 필수 기준의 표현과 6.4 두문의 "assurance"에 대한 판정 기준·검증 방법, 그리고 위험평가의 방법론을 제시하지 않아 제외 판정이 불확정적이다.

1.3.2의 범위 정의는 성격이 다르다. 이 방식에는 판정 주체도 문서화 의무도 존재하지 않으며, 선내 IT 영역은 시스템이 아니라 적용 대상 CBS로부터 향하는 IP 기반 통신 인터페이스로만 범위에 들어온다. 그 결과 IT 영역으로부터의 방어는 보안 구역의 경계에 위임되는데, 규정은 4.2.1.2에서 경계 침투가 언제나 가능함을 스스로 진술하면서도 경계 보호의 이행 실증(4.2.2.4)에서 설계·건조 단계에 요구를 두지 않고 시운전 단계에서 서비스 거부 시험과 포트 스캔을 요구할 뿐, 경계가 우회될 수 있는지 자체를 확인하는 시험은 요구하지 않는다. 요컨대 6.4는 판정 기준이 존재하되 그것을 적용할 척도와 검증 방법이 없고, 1.3.2는 판정이라는 행위 자체가 없다.

Ⅳ장은 이 두 불확정성이 실제로 남기는 위협을 STRIDE-per-interaction과 ATT&CK for ICS의 결합으로 체계적으로 도출하였다. 경로 A에서는 6.4의 필수·추가 기준을 모두 충족한 CBS에서도 열 가지 잔여 위협(R1~R10)이 성립함을 확인하였고, 경로 B에서는 범위 정의와 경계 통제 전제 전체가 하나의 잔여 위협(R11)을 이룸을 확인하였다. 이 가운데 두 경로를 시작부터 영향까지의 사슬로 심화하였다. R1(회선 조작 가능성)과 R5(범주를 경유한 전이)가 결합하는 경로에서는 제외된 시리얼 계측기의 오염된 값이 상위 항해 시스템으로 전달되어 운항자의 상황 인식을 왜곡하며, 사람의 판단이 개입하지 않는 자율운항 구성으로 발전할수록 그 영향은 커진다. R11이 이르는 경로에서는 요구사항이 미치지 않는 IT 영역에서 출발하여 경계를 넘고 IP로 연결된 자동조타장치와 주기관 원격제어 계통에 정규 형식의 명령을 발행하므로, 오염되는 것이 표시되는 값이 아니라 자동 제어 기능 자체이다. 두 경로는 성립 조건의 폭에서도 차이를 보인다. 전자는 물리적으로 회선을 절단하고 in-line 장치를 삽입하는 단계를 전제하므로 그 단계 자체가 제외 기준이 요구하는 물리 접근 통제와 충돌하는 반면, 후자는 IT 영역이 처음부터 판정을 거치지 않고 경계가 논리적 수단(방화벽·라우터)에 의존한다는 점에서 성립의 문턱이 상대적으로 낮다. 본 논문이 후자를 주된 심층 사례로 다룬 이유가 여기에 있다.

본 논문의 학술적 기여는 두 가지이다. 첫째, 강제 규정을 분석할 때 요구사항의 강도와 함께 **적용 범위에서 벗어나는 방식**을 분석 단위로 삼을 수 있음을 보이고, UR E26에 대하여 판정을 거치는 이탈(경로 A)과 판정 자체가 없는 이탈(경로 B)을 구분한 것이다. 둘째, 그 분석 단위 위에서 규정이 스스로 통과시키는 CBS와 영역의 성질로부터 잔여 위협을 연역하는 방법론(STRIDE-per-interaction + ATT&CK for ICS)을 적용하여, 선박 시스템 일반이 아니라 **규정이 비운 자리**에 한정된 위협 목록(R1~R11)을 구성한 것이다. 이 분석 단위가 다른 규정에도 유효한지는 본 논문의 범위를 벗어난다. 실무적으로는 제외 판정 시 확인하여야 할 사항과 그 근거 조문을 정리한 것이 기여에 해당한다. 다만 본 논문은 제외 제도 자체의 폐지를 주장하지 않는다. 모든 CBS에 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 문제는 판정 기준의 불확정성과 판정 단계의 전이 착안점 부재에 있다. 따라서 전이에 관한 판정 항목의 복원과 판정 표현의 구체화가 필요하다. 전자는 초판 c)·f)의 문안을 6.4의 필수 기준에 되살리는 형태로, 후자는 필수 기준 a)의 판정 경계를 당해 CBS의 인터페이스로 볼 것인지 변환장치를 포함한 경로 전체로 볼 것인지를 규칙에 명시하는 형태로 가능하다. 범위 정의에 관하여는 그 설정이 의존하는 경계 통제의 유효성을 확인하는 절차가 이행 실증의 요구에 포함될 필요가 있다.

본 논문은 UR 조문의 분석에 기초하며 실선 환경에서의 실증과 선급의 판정 실무에 대한 조사를 포함하지 않는다. 따라서 판정 편차의 존재 여부는 분석 범위를 벗어나며, Ⅳ장이 도출한 잔여 위협과 그 가운데 심화한 두 경로는 조문 해석상 배제되지 않음을 보인 것이지 실선에서의 성립을 보인 것이 아니다. 매핑표의 일부 항목(R4, R8, R10)은 뒷받침할 1차 문헌을 확보하지 못하여 확인이 필요한 상태로 남겨 두었으며, 이는 후속 검토의 대상이다.

## References

[1] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
[2] BIMCO, ICS, INTERCARGO, INTERTANKO, OCIMF et al., The Guidelines on Cyber Security Onboard Ships, Version 5, 2024.
[3] IMO, Guidelines on Maritime Cyber Risk Management, MSC-FAL.1/Circ.3/Rev.2, 2022.
[4] IMO, Maritime Cyber Risk Management in Safety Management Systems, Resolution MSC.428(98), 2017.
[5] IACS, UR E22 Computer based systems, Rev.3 Corr.1, Sep. 2025.
[6] IACS, UR E26 Cyber resilience of ships, Rev.1, Nov. 2023.
[7] IACS, UR E27 Cyber resilience of on-board systems and equipment, Rev.1, Sep. 2023.
[8] IACS, UR E26 Cyber resilience of ships, New (Apr. 2022), IACS Req. 2022, 32 pp. Withdrawn before entry into force on 1 Jan. 2024; see [6] Note 1. Archived copy: American Club, https://www.american-club.com/files/files/ur-e26-new-apr-2022.pdf (accessed Aug. 26, 2026).
[9] Y. Jo, O. Choi, J. You, Y. Cha, and D. H. Lee, "Cyberattack Models for Ship Equipment Based on the MITRE ATT&CK Framework," Sensors, vol. 22, no. 5, art. no. 1860, 2022.
[10] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024.
[11] 손금준, 최상훈, 강남선, 김성록, "IACS UR E26을 고려한 선박 네트워크 토폴로지 설계," 대한조선학회논문집, 제61권, 제6호, pp. 427-436, 2024.
[12] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024.
[13] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," Turkish Journal of Maritime and Marine Sciences, vol. 10, Special Issue 1, pp. 31-50, 2024.
[14] IACS, Rec.190 Recommendation for Vessel Asset Inventory for Computer-based Systems, Jun. 2025.
[15] IACS, Rec.166 Recommendation on Cyber Resilience, Apr. 2020, Corr.2 Apr. 2022.
[16] MITRE, ATT&CK for ICS, v19.2. https://attack.mitre.org/matrices/ics/ (accessed Aug. 14, 2026).
[17] 장지웅, 김휘강, "전력 제어시스템의 시리얼 기반 DNP통신 취약점에 관한 연구," 정보보호학회논문지, 제23권, 제6호, pp. 1143-1156, 2013.
[18] IEC, IEC 61162-460, Edition 3.0, Apr. 2024.
[19] Forescout Technologies, New Vulnerabilities and Attack Scenarios in Serial-to-IP Converters, 기술보고서, 2026.
[20] K. Munro, "Hacking serial networks on ships," Pen Test Partners, 보안 업체 공개 분석, 2018. https://www.pentestpartners.com/security-blog/hacking-serial-networks-on-ships/
[21] A. Di Pinto, Y. Dragoni, and A. Carcano, "TRITON: The First ICS Cyber Attack on Safety Instrument Systems," Black Hat USA 2018 Research Paper, Nozomi Networks, 2018.
[22] NIST National Vulnerability Database, CVE-2023-44857. https://nvd.nist.gov/vuln/detail/CVE-2023-44857 (accessed Aug. 24, 2026).
[23] 홍봉조, 김춘경, 최은희, 이남용, "RS-485 통신보안에 관한 실증적 연구," 한국IT정책경영학회 논문지, 제10권, 제4호, 2018.
[24] 최동준, 이재우, "제어 네트워크의 프로토콜을 이용한 보안 위협 연구," e-비즈니스연구, 제25권, 제2호, pp. 99-108, 2020.
[25] H. Hui, K. McLaughlin, and S. Sezer, "Vulnerability Analysis of S7 PLCs: Manipulating the Security Mechanism," International Journal of Critical Infrastructure Protection, vol. 35, art. no. 100470, 2021.
[26] 유예지, 이정연, 이지연, 양소윤, 최현우, "선박 사이버 보안 위협 모델링: VSAT 및 위성 통신 취약점 분석과 대응 전략," 한국정보처리학회 학술대회논문집, 제31권, 제2호, 2024.
[27] O. Arkin, "Bypassing Network Access Control Systems," Insightix Ltd., Technical Whitepaper, Sep. 2006.
[28] M. McFail, "Detection Engineering in ICS: Ukraine 2016 Case Study," MITRE Technical Report MTR210688, 2022.
[29] A. Keliris and M. Maniatakos, "ICSREF: A Framework for Automated Reverse Engineering of Industrial Control Systems Binaries," in Proc. NDSS Symposium, San Diego, CA, 2019.


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
| **[19] Forescout 보고서 URL·접근일** | 규·학·편 |
| **[10] 김진·이삼열 논문 원본** | `papers/`에 없음. 서지사항만 확인 |
| ~~Rec.166 검토~~ | **8차 개정에서 처리** |
| IEC 61162-450 게이트웨이·VDR의 시리얼-IP 경계 지위 | 선 I4·I5 |
| 분량 약 8.9쪽 | 6쪽 수준 기준 대비 초과. 조정 필요 시 지시 |

### 6차 개정 — 정식 논문 승격 및 경로 B 신설

**정식 논문으로 승격**(2026-08-20). 학술대회 3쪽 제약이 사라졌으므로 당시 제외했던 논거를 되살렸다.

| 대상 | 조치 | 원문 대조 |
|---|---|---|
| **3.4 신설** | "범위 정의를 경유한 두 번째 이탈 경로". 1.3.2 b)가 IT 시스템 자체가 아니라 "IP 기반 통신 인터페이스"만 범위에 넣는다는 점, 이 설정이 경계 방어의 유효성을 전제한다는 점, 그런데 **4.2.2.4.1(설계)·4.2.2.4.2(건조)가 "No requirements"**이고 시운전은 DoS 2건 + 포트 스캔뿐이어서 **경계 우회 가능성을 검증하는 시험이 없다**는 점 | E26 1.3.2 b) / 4.2.2.4.1~3 |
| **표 3 신설** | 경로 A(6.4 제외) vs 경로 B(1.3.2 범위 정의) 대비 — 근거 조항·작동 방식·판정 주체·문서화. 기존 표 3은 표 4로 | — |
| 층위 구분 명시 | 경로 A는 6.4를 통과한 개별 CBS에 무엇이 남는가, 경로 B는 어떤 영역이 애초에 판단 대상이 되지 않는가. 섞지 않도록 3.4 말미에 명시 | llm_wiki R11 |
| 초록·서론·결론·키워드 | 경로 B 반영. 기여 진술을 "이탈 경로의 판정 기준" → "이탈 경로"로 확장하고 두 경로의 구분을 기여에 편입 | — |

**범위 밖으로 확정** — 위협모델링과 위험평가는 이번 논문에 포함하지 않는다(저자 결정). 리뷰 보 M3·M4·M5·M7, 학 m7 해당분 미반영.

### 7차 개정 — 경로 B 회수 (2026-08-24)

`../notes/2026-08-24_track-split_note.md`의 트랙 분리 결정에 따라 **6차 개정에서 신설했던 경로 B(1.3.2 범위 정의)를 R3에서 되돌렸다.** 경로 B는 학술대회 원고(`../conference/2026-08-24_conference-paper_draft.md`)의 축으로 귀속되었으므로, R3에 남겨 두면 두 원고가 정면으로 겹친다.

| 대상 | 조치 |
|---|---|
| **3.4 삭제** | "범위 정의를 경유한 두 번째 이탈 경로" 절 전체(1.3.2 b) 인용, 4.2.2.4.1~3의 실증 요구 분석, 경로 A/B 층위 구분) |
| **표 3 삭제** | 경로 A/B 대비표. 이에 따라 표 4(잔여 위협 경로) → **표 3**으로 환원 |
| 요약·ABSTRACT | 말미의 경로 B 문장 삭제 |
| 서론 | "적용 범위에서 벗어나는 경로가 하나가 아님을 지적한다" → **범위 진술**("1.3.2가 영역 단위로 판단 대상을 한정하는 문제는 층위가 달라 다루지 않는다"). 장 구성 안내에서 "범위 정의" 삭제 |
| 결론 | 경로 B 문단 삭제. 기여 진술을 "이탈 경로 일반, 두 경로 구분" → **"적용 범위에서 벗어나는 경로의 판정 기준, UR E26 6.4"**로 환원 |

**남긴 것 — 1.3.2를 인용하는 다른 두 곳은 그대로 둔다.** 학술대회 원고가 쓰는 것은 1.3.2 **b)**(IP 기반 통신 인터페이스)이고, R3이 쓰는 것은 1.3.2 **a)**의 다른 두 문장이므로 겹치지 않는다.

| 위치 | 인용 대상 | 용도 |
|---|---|---|
| 4장 (추가 기준 a) 척도 부재) | 1.3.2 a) "Navigational systems required by statutory regulations" | E22 1.2의 법정 규정 적용 CBS 배제와 대조 |
| 4장 (시리얼 규격의 보안 전제) | 1.3.2 a) 말미의 IEC 61162-460 수용 단서 | 보안 기능이 add-on 계층임을 확인 |

**분량** — 약 8.9쪽 → 3.4 삭제분만큼 감소. 조판 후 재측정 필요.

### 8차 개정 — Rec.166 검토 (2026-08-24)

Round 2 규 R7이 요구한 **Rec.166 검토**를 처리하였다(`../rules/rec166corr2.pdf`, 57pp, `pdftotext -layout` 전문 대조).

| 대상 | 조치 | 원문 대조 |
|---|---|---|
| **3.3에 문단 신설** | Rec.166의 전이 관련 조항을 열거하고, 그것이 초판 c)·f)의 자리를 대신하지 못하는 이유 3가지를 제시 | Rec.166 6.5 R1·R2 / 7.3.2.6 (5) / 2.2 / E26 1.3.4 |
| **참고문헌 [15] 신설** | IACS Rec.166. 이에 따라 기존 [15]~[19] → **[16]~[20]** 시프트 | — |

**대조한 원문**

| 조항 | 원문 |
|---|---|
| Rec.166 6.5 R1 | "Impact of cyber incidents should be contained to the network zone of origin." |
| Rec.166 6.5 R2 | "Minimize by isolating the extension of possible disruption to OT system which affects the availability of safety critical functions." |
| Rec.166 7.3.2.6 (5) | "The aim should be to decouple capabilities in order to prevent ripple effects that can contaminate large portions of the systems as the result of a single cyber incident." |
| Rec.166 2.2 | "The recommendation covers onboard OT systems and other systems which are connected to onboard OT systems in a way that may affect their operation (as identified by risk assessment)." |
| E26 1.3.4 | "…when both this UR and Recommendation 166 are used, should any difference in requirements addressing the same topic be found between the two instruments, the requirements in this UR shall prevail." |

**부정 주장의 근거 — "Rec.166에는 제외 절차가 없다"**

루트 `CLAUDE.md`의 서술 원칙(부정 주장에는 대체 조항을 먼저 논박한다)에 따라 전문 문자열 검색으로 확인하였다. `exclud`, `exempt`, `waiv`, `omit`, `dispens`, `need not`, `not required`, `outside` — **전 57쪽에서 일치 0건.** 적용 범위를 정하는 곳은 2.1~2.5이며, 2.2가 연결·영향 관계를 척도로 삼는다. 원고에는 "본 논문이 확인한 범위에서"를 붙여 한정하였다.

**논지에 대한 함의** — 이 검토는 3.3의 주장을 약화시키지 않고 강화한다. E26이 참조하는 비강제 권고는 적용 범위를 **연결과 영향의 관계**로 정하는데, 강제 문서인 UR은 이를 열거와 개별 제외로 바꾸면서 제외 판정 기준에서 전이 항목을 두지 않았다. 다만 Rec.166(2020)은 E26보다 앞서 발간된 별개 문서이므로, **"E26이 Rec.166을 완화하였다"는 서술은 하지 않았다.** 초판 대조에서와 같은 이유이다.

### 9차 개정 — Ⅳ장을 두 예시로 분리 (2026-08-24)

**저자 결정 두 건.** ① 문서 부담(Appendix I) 논거는 **폐기**한다 — 논문의 무게중심을 기술적 논증에 둔다. ② Ⅳ장에 **IT 영역에서 출발하는 두 번째 예시**를 넣는다.

**작업 경위** — 처음에 IT 경유 경로를 4.1의 초기 접근으로 붙였으나, 이는 저자 의도와 다른 구성이었다. 두 예시는 **표적도 귀결도 다르다.** 되돌린 뒤 별도 절로 다시 썼다.

| | 4.1 | 4.2 |
|---|---|---|
| 출발 | 6.4로 제외된 시리얼 계측기 | 적용 범위 밖인 선내 IT 영역 |
| 표적 | 계측기가 값을 공급하는 상위 항해 시스템 | IP로 연결된 자동조타·주기관 원격제어 |
| 개입 | 데이터 오염 → 운항자의 상황 인식 왜곡. 자율운항 구성에서 영향 확대 | 제어에 직접 작용 → 침로·기관 출력 조작 |
| 조문 | 6.4 필수 a)·추가 a)의 판정 | 4.2.1.3(비신뢰 네트워크), 4.2.1.1(경계 수단) |

**4.2의 구성** — 출발점(요구사항이 미치지 않는 영역) → 초기 접근과 잠복 → 경계 통과 → 표적과 영향. 표 4 신설.

**주장 강도** — 경계 통과가 어떤 조건에서 성립하는지를 **조문으로 논증하지 않았다.** "그러한 경로가 보고된 바 있다"는 문헌 사실만 전제로 둔다. 루트 `CLAUDE.md`의 회색문헌 취급 원칙에 따른 것이다. CVE-2023-44857은 **인증을 전제하는 취약점**이므로 "그 자체로 경계를 여는 것은 아니다"를 명시하였다.

**검증한 출처**

| 출처 | 확인 내용 |
|---|---|
| [21] TRITON (Black Hat USA 2018) | IT 망 침투 → 양쪽 환경 접근 가능 시스템 경유 → OT 망 → 통상 격리된 구간의 엔지니어링 워크스테이션 → Triconex 컨트롤러 |
| [19] Forescout | 초기 접근 경로로 인터넷 노출 VPN 집선장치(2025 폴란드)·침해된 IT 워크스테이션 명시 |
| [22] NVD CVE-2023-44857 | Cobham SAILOR VSAT Ku 164B019, `acu_web` 구성요소 코드 인젝션(CWE-94), CVSS 3.1 기준 8.1, **인증 필요** |

**ATT&CK 식별자 검증** — 현행판 v19.2에서 직접 조회.

| ID | 명칭 | 전술 |
|---|---|---|
| T0819 | Exploit Public-Facing Application | Initial Access (TA0108) |
| T0822 | External Remote Services | Initial Access (TA0108) |
| T0866 | Exploitation of Remote Services | Initial Access / Lateral Movement |
| T0886 | Remote Services | Initial Access / Lateral Movement |
| T1692.001 | Unauthorized Message: Command Message | Impair Process Control (TA0106) |
| T0831 | Manipulation of Control | Impact (TA0105) |
| T0880 | Loss of Safety | Impact (TA0105) |

**⚠ 학술대회 원고와의 관계가 다시 열렸다.** 4.2는 "선내 IT 영역이 요구사항의 대상이 아니다"를 출발점으로 삼으므로, 7차 개정에서 R3에서 빼내어 학술대회 원고로 귀속시켰던 **범위 정의(경로 B) 축과 다시 만난다.** 다만 두 원고가 그 사실로부터 끌어내는 것은 다르다 — 학술대회 원고는 **규정이 요구하는 실증의 범위**를 논하고, 이 원고는 **위협 경로의 예시**를 든다. 4.2에서 학술대회 원고의 논거(4.2.1.2의 "breaching that perimeter is always possible" 인용, 각 절 `Demonstration of compliance` 정리표, 1.3.2 b) 인용)는 쓰지 않았다. 투고 전에 두 원고를 나란히 놓고 재확인할 것.

**남은 것** — 집필 순서 원칙에 따라 **요약·ABSTRACT·서론·결론은 본론이 확정된 뒤에 다시 쓴다.** 현재 이 넷은 4.1만을 반영한 상태이다.

**미해결** — VDR의 시리얼-IP 경계 지위(선 I5)는 1차 자료가 없어 서술하지 않았다.

### 10차 개정 — 확장판 관계 확정에 따른 제약 해제 (2026-08-24)

**저자 확인** — 이 원고는 학술대회 원고의 **확장판**이며, 분리의 목적은 자기표절 방지(문장 단위 중복 회피) 하나이다. 논거를 갈라놓을 필요가 없다.

이에 따라 9차 개정에서 4.2가 일부러 비켜 갔던 조문 둘을 복원하였다.

| 대상 | 조치 | 원문 |
|---|---|---|
| **1.3.2 b) 인용** | 4.2 출발점 문단에 추가 — 범위에 들어오는 것은 IT 시스템이 아니라 그 시스템으로 향하는 IP 인터페이스 | "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems" + 여객 서비스·여객망·관리망·승무원 복지·"any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)" |
| **4.2.1.2 인용** | 경계가 무조건 유지되지 않는다는 것이 **규정 자신의 진술**임을 명시. 절 제목이 Rationale임을 함께 적음 | "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, breaching that perimeter is always possible" |
| 경계 통과 문단 | 과도한 유보("조문으로 논증하지 않으며")를 조정. 특정 선박에서의 성립 조건은 다루지 않되, 문헌 보고가 4.2.1.2의 진술과 어긋나지 않음을 적음 | — |
| 표 4 | `출발`·`경계 통과` 행에 위 두 조문 반영 | — |

**남은 것** — 학술대회 원고가 먼저 게재되면 이 원고에서 **선행 문헌으로 인용**한다. 투고처의 확장판 정책 확인 필요. 서론 첫 문단과 관련 연구는 두 원고의 소재가 같으므로 투고 전 **문장 단위 대조**가 필요하다.

### 11차 개정 — Ⅲ장에 3.4 신설 (2026-08-24)

4.2가 Ⅲ장의 근거 없이 Ⅳ장에서 시작하는 구조였다. 이를 받아 줄 절을 Ⅲ장에 두었다.

| 대상 | 조치 |
|---|---|
| **3.4 신설** | "범위 정의에 의한 이탈과 경계 방어의 전제". ① 6.4 제외와 1.3.2 범위 정의의 층위 대비(표 3) ② 1.3.2 b)는 시스템이 아니라 인터페이스를 범위에 넣음 ③ 4.2.1.3·4.2.1.1 — 방어가 경계에 위임됨 ④ 4.2.1.2 — 경계 돌파 가능성은 규정 자신의 진술 ⑤ 4.2.2.4의 실증 요구 — 설계·건조 `No requirements`, 시운전은 DoS 2건 + 포트 스캔 |
| **표 3 신설** | 두 방식 대비(작동 단위·판정·문서화·본 논문에서의 위치). 기존 표 3→**표 4**, 표 4→**표 5** |
| Ⅲ장 제목 | "UR E26 CBS 제외 규정 분석" → **"UR E26의 제외 규정과 범위 정의 분석"** |
| 4.2 출발점 압축 | 3.4와 중복되던 조문 인용을 걷어내고 3.4를 가리키도록 함. 4.2.1.3의 물리적 분할 요구와 `Alternatively` 문장에 대한 선제 대응은 4.2에 남김 |
| 서론 | 7차 개정에서 넣었던 범위 진술("1.3.2는 다루지 않는다")을 철회. 장 구성 안내도 수정 |

**대조한 원문**

| 조항 | 확인 |
|---|---|
| 4.2.2.4.1 / 4.2.2.4.2 | 각각 "No requirements." |
| 4.2.2.4.3 | ① 구역 경계 보호 장치 대상 DoS ② 각 네트워크 세그먼트 내부 발신 과도 데이터 흐름 DoS(flooding + application layer attack) ③ 불필요 기능·포트·프로토콜·서비스 제거 여부를 "analytic evaluation and port scanning"으로 확인. **"The second and third tests may be omitted if performed during the certification of CBSs as per section 5.2.1."** |
| 1.3.2 b) | "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems" + 여객 서비스·여객망·관리망·승무원 복지·"any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)" |
| 4.2.1.2 (Rationale) | "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, breaching that perimeter is always possible" |

**⚠ 학술대회 원고와 가장 크게 겹치는 지점** — 3.4의 ⑤(4.2.2.4의 실증 요구)는 학술대회 원고의 핵심이다. 확장판 관계이므로 다루는 것 자체는 문제가 없으나, ⓐ **문장을 새로 썼고** ⓑ 학술대회 원고의 단계별 정리표(표 1)는 옮기지 않고 **문단으로 압축**했으며 ⓒ 이 원고에서 ⑤는 결론이 아니라 **4.2의 전제**로 쓰인다. 학술대회 원고가 게재되면 이 자리에서 **선행 문헌으로 인용**한다.

**남은 것** — 요약·ABSTRACT·서론·결론이 아직 4.1과 6.4만 반영한 상태이다. 특히 결론의 기여 진술은 7차 개정에서 "6.4"로 좁혀 둔 것이므로 3.4·4.2를 반영하여 다시 써야 한다.

### 12차 개정 — 결론 재작성 · 분석 단위 확대 · R4 전환 (2026-08-24)

집필 순서(루트 `CLAUDE.md`)에 따라 본론 확정 후 결론을 다시 썼다. 4문단 → **6문단**.

| 문단 | 내용 | 변경 |
|---|---|---|
| 1 | 연구 질문과 답, 근거 두 가지 | 잔존 조항 열거에 **Rec.166**을 추가하고 "강제력이 없는 권고"로 논박(8차 개정 반영) |
| 2 | **신설** — 1.3.2 범위 정의에 의한 이탈. 판정 주체·문서화 부재, 방어의 경계 위임, 4.2.1.2의 자기 진술, 4.2.2.4의 실증 요구 범위, 두 방식의 층위 차이 | 3.4 반영 |
| 3 | 두 예시. 4.1은 **데이터 오염 → 상황 인식 왜곡 → 자율운항에서 확대**, 4.2는 **제어 자체에 개입 → 자동조타·주기관** | 종전에는 4.1만 서술 |
| 4 | 기여 | 분석 단위를 "제외 경로의 판정 기준" → **"적용 범위에서 벗어나는 방식"**으로 넓히고, **판정을 거치는 이탈과 판정 자체가 없는 이탈의 구분**을 기여에 편입 |
| 5 | 제외 제도 폐지를 주장하지 않음 + 필요한 것 | 종전 둘(전이 판정 항목 복원, 판정 표현 구체화)에 **범위 정의에 관한 한 문장** 추가 — 경계 통제의 유효성을 확인하는 절차가 이행 실증에 포함될 필요 |
| 6 | 범위 진술 | Ⅳ장의 두 경로가 **조문 해석상 배제되지 않는 경로의 예시이지 실선에서의 성립을 보인 것이 아님**을 명시 |

**결론 압축** — 6문단으로 썼다가 **4문단으로 줄였다.** 병합 내역은 ①+② 유지, ②의 실증 요구와 ③의 두 예시를 한 문단으로, ④+⑤(기여와 제언)를 한 문단으로, ⑥ 범위 진술 유지.

**분석 단위 확대 (저자 결정)** — 3.4·4.2가 본문에서 차지하는 비중에 맞추어 논문의 축을 **6.4 제외 하나에서 "적용 범위에서 벗어나는 두 방식"으로 넓혔다.**

| 대상 | 이전 | 이후 |
|---|---|---|
| 국문 제목 | IACS UR E26 CBS 제외 기준의 한계 분석: 사고 전이 관점에서 | **IACS UR E26 적용 범위 이탈 경로의 한계 분석: 제외 판정과 범위 정의** |
| 영문 제목 | An Analysis of Limitations in the CBS Exclusion Criteria… : From the Perspective of Cyber Incident Propagation | **An Analysis of Limitations in the Routes out of the Scope of Applicability…: Exclusion Assessment and Scope Definition** |
| 연구 질문 | "6.4의 제외 판정 기준은 제외된 CBS를 경유한 사고 전이가 발생하지 않음을 확인하기에 충분한가" | **"UR E26에서 적용 범위를 벗어나는 방식은 그로부터 남는 위협이 통제됨을 확인하기에 충분한가"** — 이어서 두 방식을 제시 |
| 결론 첫 문장 | 위 질문 인용 | 새 질문 인용 |

**주장 강도 점검** — 제언은 세 가지 모두 "필요하다" 수준에 머문다. 조문 개정안의 문안을 제시하지 않았다. 마지막 문단이 실증 부재를 스스로 한정하므로 향후 연구 절은 두지 않았다(루트 `CLAUDE.md`).

---

## R4 전환 (2026-08-24)

7차 개정부터는 R3가 아니라 **R4**로 진행했어야 했다. 파일명을 `2026-08-20_conference-paper_R3.md` → **`2026-08-24_journal-paper_R4.md`**로 바꾸었다. "conference-paper"는 학술대회 트랙이 `conference/`로 분리된 이후 실제 내용과 맞지 않아 `journal-paper`로 고쳤다.

**⚠ R3 스냅샷은 남아 있지 않다.** 7~12차 개정이 R3 파일에서 제자리로 이루어졌고 사본을 두지 않았다. 복원은 불가하며, 변경 내역은 위 7~12차 개정 항목에 전부 기록되어 있다. 직전으로 거슬러 확인할 수 있는 판은 `2026-08-18_conference-paper_draft_rev2.md`와 `IACS UR E26 CBS 제외 기준의 한계 분석_정성윤 R.2.pdf`이다.

**앞으로** — 개정 번호를 올릴 때는 **먼저 파일을 복사해 이전 판을 얼려 두고** 새 파일에서 작업한다. 루트 `CLAUDE.md`에도 적었다.

**R4의 남은 작업**

| 항목 | 비고 |
|---|---|
| 요약·ABSTRACT | 아직 6.4와 4.1만 반영. 집필 순서상 **마지막** |
| 서론 | 연구 질문 문장과 장 구성 안내는 고쳤으나 전체 통독 필요 |
| 키워드 | 새 제목·축에 맞추어 재검토 |
| 문헌 탐색 프로토콜 1문장 | 학 M5. **저자만 작성 가능** |
| [8] 초판 입수 경로, [19] Forescout URL·접근일 | 저자 확인 필요 |
| [10] 김진·이삼열 원본 | `papers/`에 없음 |
| VDR의 시리얼-IP 경계 지위 | 선 I5. 1차 자료 없음 |
| 분량 | 본문 약 3.2만 자. 조판 후 재측정 |
| 학술대회 원고와의 문장 단위 대조 | 투고 전 필수. 특히 서론 첫 문단·관련 연구 |

### 13차 개정 — 논의 장 미도입 결정 · 서론 재작성 · 중복 검사 (2026-08-24)

**논의 장을 두지 않는다(저자 결정).** 조문 분석 논문에서는 반론 대응이 각 주장 바로 옆에 붙는 것이 자연스럽고, 이를 따로 모으면 같은 말을 두 번 하게 되어 분량만 는다. 대신 예상 반론이 본문 어디에서 받아지는지를 점검하였다.

| 예상 반론 | 대응 위치 |
|---|---|
| 6.3·4.1.1·4.2.1.4.1·5.1.4·4.2.1.3이 전이를 다룬다 | 3.3 (i)~(v) |
| Rec.166에 사고 봉쇄 요구가 있다 | 3.3 마지막 문단 |
| 제외되어도 Rec.190 자산 목록에 남는다 | 3.2 |
| E22가 범주 확인 절차를 둔다 | 4.1 (E22 3.2·4.3.3·4.3.4) |
| 4.2.1.3의 물리적 분할이 관철되면 4.2는 성립하지 않는다 | 4.2 첫머리 |
| 선급이 실무로 메운다 | 결론 마지막 문단(범위 진술) |

**서론 재작성**

| 대상 | 조치 |
|---|---|
| 1문단 | **전면 재작성.** 학술대회 원고 1문단과 어절 단위로 겹쳤다. 연결의 구조에서 문제가 발생한다는 방향으로 새로 씀 |
| 3문단 | "제외할 수 있는 경로" 하나 → **두 방식**(6.4 제외 / 1.3.2 범위 정의)을 제시하고 층위 차이를 명시 |
| 4문단 | 연구 질문·방법·장 구성을 새 축에 맞춤(12차 개정에서 선행) |
| Ⅱ장 gap 진술 | "제외의 판정 기준" → **"적용 범위에서 벗어나는 방식 자체"**로 확대. 선행연구가 "적용 대상으로 들어온 시스템을 전제한다"는 점을 명시 |
| 키워드 | CBS 제외 기준 → **적용 범위 이탈, 제외 판정, 범위 정의**. 영문도 동일하게 |

**학술대회 원고와의 문장 단위 중복 검사** — 두 원고의 문장을 6-gram Jaccard로 전수 대조하였다(학술대회 89문장 × 정식 304문장).

| 유형 | 처리 |
|---|---|
| 저자행·이메일·참고문헌 서지 | 동일한 것이 정상. 대상 외 |
| **서론 1문단** | 유사도 최고였다. 재작성으로 **임계값 아래로 내려감** |
| **4.2.1.2 인용 도입부** | "망 분할의 근거를 설명하면서" → "표제를 Rationale로 두고 …그 서두가 다음과 같다"로 바꾸고 **국문 부연을 덧붙임** |
| **1.3.2 b) 인용 도입부** | 문장 구조를 바꾸고 예시 열거 방식을 달리함 |
| Ⅱ장 첫 문장 | "위협 분석 연구는 꾸준히 축적되어 왔다" → "위협 분석은 상당한 양이 쌓여 있다" |
| 조용현·차영균 소개 문장 | 서술 순서를 바꿈(대상 선정 → DFD → STRIDE·Attack Tree) |

잔여 유사 쌍은 **UR 원문 인용문 자체**와 **키워드**뿐이다. 규정 원문을 같은 문구로 인용하는 것은 자기표절이 아니며, 두 원고 모두 인용부호로 출처를 밝히고 있다.

**남은 것** — 요약·ABSTRACT. 집필 순서상 마지막이며, 아직 6.4와 4.1만 반영한 상태이다.

### 14차 개정 — 요약·ABSTRACT 재작성 · 3.3 표 전환 · 분량 점검 (2026-08-24)

**요약·ABSTRACT 재작성** — 새 축(적용 범위에서 벗어나는 두 방식)에 맞추어 다시 썼다. 두 방식 → 각각의 분석 결과 → 두 예시 → 둘의 차이 순서. 요약 717자, ABSTRACT 252 words.

**3.3 (i)~(v)를 표 3으로 전환** — 잔존 조항 5개를 문단으로 늘어놓던 것을 `조항 / 요구 내용 / 초판 c)·f)를 대신하지 못하는 이유` 3열 표로 바꾸었다. 표 번호가 밀려 기존 표 3~5 → **표 4~6**.

**4.1 압축** — Forescout 보고서[19]의 접근 경로 서술이 4.2와 중복되어 4.1에서는 걷어내고 "4.2에서 다룬다"로 넘겼다. 영향 사슬 마지막 문장도 다듬었다.

**투고처 확정 — 한국정보통신학회(KIICE) 국문지 JKIICE**

| 항목 | 확인 내용 | 출처 |
|---|---|---|
| 투고 시스템 | dbpiaone.com/jkiice | kiice.org 국문지 투고 방법(2023) |
| 심사료 | 일반 4만원 / 긴급 8만원 | 〃 |
| 양식 | `한국정보통신학회_국문지양식(2023).zip` | 〃 |
| 트랙 | **Full Paper / Short Paper 구분** | jkiice.org Instructions for Authors 2종 |
| 게재료 | 2023.07 인상. 상세는 학회 자료실 "게재료 산출표(2023)" | kiice.org 공지 166174 |
| 게재료 구간 | **[미확인]** 6쪽 이하 15만원 / 7~8쪽 15만원+초과 쪽당 3만원 / 9쪽 이상 21만원+초과 쪽당 4만원 — **검색 요약으로만 확인. 산출표 원본 대조 필요** | — |

→ 위 구간이 맞다면 **6쪽은 하드 리밋이 아니라 게재료 문턱**이다. 분량을 6쪽에 맞추는 것이 목표가 아니게 되며, 논문이 나아지는 축약만 하면 된다.

**분량 점검** — 조판 밀도는 `outputs/IACS UR E26 CBS 제외 기준의 한계 분석_정성윤 R.2.pdf`(A4 5쪽)에서 실측하였다. 페이지당 2,406~3,400자(공백 제외), 본문이 찬 페이지 평균 2,787자.

| 구간 | 문자수(공백 제외) |
|---|---|
| Ⅲ장 | 약 9,700 |
| Ⅳ장 | 약 8,500 |
| References (22건) | 2,132 |
| ABSTRACT | 1,626 |
| 결론 | 1,440 |
| 서론 | 1,398 |
| 요약 | 717 |
| Ⅱ장 | 703 |
| **본문 합계** | **26,478 → 약 7.8~9.5쪽** |

**⚠ 이번 축약은 분량을 거의 줄이지 못했다(26,604 → 26,478).** 표 3 전환이 가독성은 높였으나 근거를 보존하느라 문자수는 오히려 늘었고, 4.1 압축분과 상쇄되었다. 실질적으로 분량을 줄이려면 **표 2(초판 대조표)의 축소** 또는 **두 예시 중 하나의 삭제**밖에 남지 않는데, 둘 다 논문의 핵심 근거이므로 권하지 않는다.

**남은 것**

| 항목 | 비고 |
|---|---|
| 게재료 산출표(2023) 원본 확인 | 학회 자료실. 6쪽 초과 비용 확정 |
| Full Paper / Short Paper 트랙 선택 | 현재 분량은 Full Paper |
| JKIICE 투고규정 원문 | jkiice.org 접속이 되지 않아 미확인. 초록 단어수·키워드 개수·참고문헌 양식 확인 필요 |
| **KIICE 학술대회 → 국문지 확장 투고 정책** | 같은 학회이므로 반드시 확인(journal@kiice.org) |
| Ⅱ장 관련 연구 703자 | 전체의 3%. 정식 논문으로는 짧다 |
| 문헌 탐색 프로토콜 1문장 | 저자만 작성 가능 |
| [8] 초판 입수 경로, [19] Forescout URL·접근일 | 저자 확인 필요 |
| [10] 김진·이삼열 원본 | `papers/`에 없음 |

### 15차 개정 — round-03 리뷰 계기 위협모델링 재도입 · R5 전환 (2026-08-26)

**배경.** `2026-08-24_journal-paper_R4-short.md`(6쪽 축약본)에 대해 round-03 리뷰(4인, Major×2/Minor×2)를 수행한 결과, (1) 4.2절의 TRITON[19]/Forescout[17] 인용 오류(S1) — 단, 이는 R4-short 축약 과정에서만 생긴 오류로 R4 원본에는 없었음을 재확인, (2) 6쪽 목표와 IV장 두 예시 구성의 구조적 충돌(C1), (3) 4.1의 문언 기준 채택이 미확정 해석에 의존한다는 지적(C2)이 확인되었다. 저자와의 논의 결과 다음과 같이 방침을 전환하였다 — ① JKIICE 투고를 Full Paper·분량 제한 없음으로 확정(6쪽 목표 폐기), ② 위협모델링을 이 논문 자체에 재도입(2nd_research/paper2_threat-modeling은 미착수 계획서일 뿐이므로 자기표절·중복 우려 없음을 확인), ③ IT→OT 경로(경로 B)가 물리적 분할이 아닌 논리적 분할에 의존한다는 저자의 위협 판단에 따라 이를 주된 심층 사례로, 계측기 경로(경로 A)는 대비 사례로 재배치. 상세 근거는 `CLAUDE.md`(2026-08-26 갱신분) 참조.

**IV장 전면 재구성.** "잔여 위협 경로의 예시"(4.1·4.2 두 예시) → "잔여 위협의 체계적 모델링"(4.1 방법론 → 4.2·4.3 R1~R11 매핑표 → 4.4·4.5 심층 시나리오)으로 재편하였다.

| 절 | 내용 | 비고 |
|---|---|---|
| 4.1 | 신뢰경계(E26 대상 CBS vs 경로 A·B 이탈 CBS) + STRIDE-per-interaction·ATT&CK for ICS 방법론 + 잔여 위협의 조작적 정의 | 신설 |
| 4.2 | 경로 A(6.4) 잔여 위협 R1~R10 매핑표 | 신설. `llm_wiki/2026-08-13_e26-exclusion-residual-threat_mapping.md` 기반 |
| 4.3 | 경로 B(1.3.2) 잔여 위협 R11 매핑표 | 신설 |
| 4.4 | IT→OT 심층 시나리오(구 4.2 확장) | I1 반영 — "조종 불능" → "자동 제어 기능의 상실"로 하향, 수동/NFU·국소제어 백업 경로 존재를 명시. I2 반영 — 자동조타·주기관 동시 도달에 공통 백본(ICMS/IBS) 전제가 필요함을 명시 |
| 4.5 | 계측기 대비 사례(구 4.1 축소) | R1 반영 — 4.2.1.3을 6.4 제외 CBS에 확장 적용하는 것을 "3.1과 같은 성격의 불확정성"으로 재프레이밍(순환논증 단정 대신). S3 반영 — 초기 접근 T0847(이동식 매체)을 T0864(Transient Cyber Asset)로 교체 |

**신규 참고문헌 [23]~[29] 추가** — R1~R10 매핑표의 근거로 RS-485 실증연구, 제어네트워크 프로토콜 위협연구, S7 PLC 취약점 분석, VSAT 위협모델링, Bypassing NAC, MITRE Detection Engineering, ICSREF를 추가하였다. 이들은 `papers/`에 로컬로 보관된 자료에서 서지사항을 직접 확인하였다. R4·R8·R10 세 항목은 뒷받침할 1차 문헌을 확보하지 못하여 [확인필요]/[추론]으로 표기하고 지어내지 않았다.

**[8] 초판 입수 경로 해소** — American Club(P&I 클럽)이 재게시한 사본(`https://www.american-club.com/files/files/ur-e26-new-apr-2022.pdf`)이 로컬 파일(`rules/ur-e26-new-apr-2022.pdf`)과 파일명이 일치함을 확인하여 각주로 추가하였다. `[19] Forescout URL·접근일`은 여전히 미해결.

**서론·요약·ABSTRACT·결론 갱신** — IV장 재구성에 맞추어 두 방식을 "예시"가 아니라 "체계적으로 도출"한다는 서술로 교체하고, 결론에 두 심층 경로의 성립 조건 폭 차이(계측기 경로는 물리적 회선 조작을 전제하여 문턱이 높고, IT→OT 경로는 판정 자체가 없어 문턱이 낮음)를 반영하였다. 논문 작성 순서 원칙에 따라 결론 → 서론 → 요약/ABSTRACT 순으로 수정하였다.

**파일 계보** — `2026-08-24_journal-paper_R4.md`(압축 전 원본)를 얼린 뒤 복사하여 `2026-08-26_journal-paper_R5.md`로 이번 개정을 진행하였다. `R4-short.md`는 6쪽 목표가 폐기되어 더 진행하지 않으나 삭제하지 않는다.

**남은 것**

| 항목 | 비고 |
|---|---|
| [19] Forescout URL·접근일 | 여전히 미해결 |
| [10] 김진·이삼열 원본 | `papers/`에 없음 |
| R4·R8·R10의 1차 문헌 확보 | 확인필요로 남겨 둠 |
| 표 5~8의 분량·가독성 | Full Paper 기준이므로 분량 제약은 없으나, 표가 4개로 늘어난 만큼 가독성 재점검 필요 |
| Ⅱ장 703자 | 여전히 짧음. 위협모델링 선행연구([1],[9]) 외 확장 여지 검토 |

### 16차 개정 — 문체·인용·구조 정합성 점검 (2026-08-27)

R5 전체(본문 1~664줄)를 통독하여 확인한 것들. 저자가 검토 후 일괄 적용을 지시하여 반영하였다.

| 항목 | 조치 | 근거 |
|---|---|---|
| **수사의문문 종결 2건** | 서론(연구 질문)과 3.4("그렇다면 그 가능성은 어떻게 확인되는가.")를 평서형으로 전환 | 사용자가 국문 학술지 문체에서 반복적으로 지적해 온 패턴 |
| **"경계 돌파"·"경계 방어" 용어 정리** | "경계 방어"(3건, 3.4 절 제목 포함)는 "경계 통제"로 통일. "경계 돌파"(6건)는 저자 검토 결과 맥락에 따라 둘로 나누었다 — 4.2.1.2("breaching that perimeter is always possible")의 진술을 직접 가리키는 자리(요약·ABSTRACT·3.4·표 6·표 7·결론, 6건)는 **"경계 침투"**로, 이행 실증이 검증하는지를 묻는 자리(3.4·결론, 기존 "우회" 표현 2건)는 **"경계 우회"**를 그대로 유지 — "침투는 가능하다고 진술하지만, 우회 여부를 확인하는 시험은 없다"는 대비가 되도록 정리 | 사용자가 예전에 군사적 어감을 지적했고, "돌파"는 "침투"가 더 정확하다는 저자 판단(2026-08-27) |
| **표 4 "본 논문에서" 행 정정** | `경로 A: 3.1~3.3, 4.1` / `경로 B: 본 절, 4.2` → **`경로 A: 3.1~3.3, 4.2, 4.5`** / **`경로 B: 본 절, 4.3, 4.4`**. 15차 개정(Ⅳ장 전면 재구성)이 반영되지 않은 채 남아 있던 옛 목차 참조였다 | — |
| **4.5 "필수 기준 a)의 판정 경계" 문단 재작성** | "3.1에서 확인하였듯 …"이라는 도입이 실제로는 3.1에 없는 내용(a)의 문언/경로 판정 경계 구분)을 가리키고 있었다. R4.md(158행, 15차 개정에서 얼려 둔 직전판)에 있던 **"isolated"의 규칙 내 이중 정의**(6.4 필수 a="have no IP-network connections" vs 4.2.1.1="air gapped", 그 간극에 시리얼 전용 CBS가 놓인다는) 문단이 Ⅳ장 재구성 과정에서 누락되어 있던 것을 복원하고, 근거 없는 "3.1에서 확인하였듯"을 규정 조문 자체에 근거를 두는 서술로 교체했다 | 루트 `CLAUDE.md`가 확정 발견으로 명시한 항목("`isolated`는 규칙 안에서 정의가 둘이다") |
| **참고문헌 [16] 미인용 해소** | MITRE ATT&CK for ICS[16]가 표 5~8에서 T0xxx/T1xxx로 수십 회 쓰이면서도 본문에 한 번도 인용되지 않고 있었다. 서론(장에서 "MITRE ATT&CK for ICS" 최초 언급)에 [16] 추가 | — |
| **표 5 R2 행 인용 재검토** | R2("USB·정비용 노트북·무선·위성단말 백채널 등 비IP 경로")에 붙어 있던 [21](TRITON)·[25](S7CommPlus 프로토콜 우회)를 원문 확인한 결과 둘 다 **IP 네트워크 기반 공격 사례**로, R2가 말하는 비IP 경로를 뒷받침하지 않았다. 위성단말 백채널 부분만 기존 [26](VSAT 위협모델링)로 대체하고, USB·노트북·무선 부분은 1차 문헌을 확보하지 못하여 [확인필요]로 남겼다 | `CLAUDE.md` 검증 원칙("출처를 모르면 확인 필요로 남긴다") |

**적용 범위** — 위 조치는 본문(Ⅰ~Ⅴ장, 1~256줄)에 한정했다. 수정 로그(6~15차 개정 기록)는 당시 시점의 서술을 그대로 남기는 것이 기록으로서 맞다고 판단하여 손대지 않았다.

**요약·ABSTRACT 압축** — 국문 요약이 길게 느껴진다는 저자 의견에 따라 국문·영문 모두 다시 썼다. 국문: 855자 → 725자(공백 제외 659→558자, 약 15% 축소) — "하나는 ~이고 다른 하나는 ~이다" 병렬 구문을 "6.4의 ~와 1.3.2의 ~라는 두 가지 이탈 방식"으로 압축하고, "판정 기준의 항목으로 두었던"·"수용을 허용하면서도" 등 중복 수식을 덜어냈다. 영문: 292단어(1,913자) → 234단어(1,598자, 약 20% 축소) — 같은 방식으로 병렬 문장을 압축하고 수동태·중복 관사구를 줄였다. 두 언어 모두 주장·조문 근거는 그대로 남겨 내용 손실은 없다.

