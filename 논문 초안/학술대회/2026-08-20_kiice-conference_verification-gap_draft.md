# IACS UR E26의 경계 방어 가정과 실증 요구의 범위

정성윤¹ · 이대성¹'* / ¹한국해양대학교
E-mail : meraki4.1st@gmail.com / dslee@kmou.ac.kr

On the Perimeter Defence Assumption and the Scope of Compliance Demonstration in IACS UR E26
Sung-yoon Jung¹ · Dae-sung Lee¹'* / ¹Korea Maritime and Ocean University

---

## 요 약

IACS UR E26은 선박의 사이버 복원력에 관한 강제 요구사항이다. 동 UR 1.3.2는 적용 대상을 운용기술(OT) 시스템으로 정의하고 선내 정보기술(IT) 영역은 시스템 자체가 아니라 적용 대상 CBS로부터 향하는 IP 기반 통신 인터페이스로만 범위에 포함하므로, 그 안전성은 보안 구역 경계의 통제가 유효하다는 가정에 의존한다. 본 논문은 각 요구사항에 부속된 "Demonstration of compliance"를 단계별로 정리하여, 규정이 4.2.1.2에서 경계 돌파의 가능성을 스스로 인정하면서도 시운전 단계의 실증은 승인 문서에 따른 적합성 확인과 서비스 거부 시험에 머무른다는 점을 확인하였다. 이로부터 적용 범위 밖 IT 영역의 실제 관리 수준, 승인 문서의 완전성을 문서와 독립적으로 확인하는 방법, 경계 우회를 다루는 시험의 수행 형태라는 세 지점을 확인이 필요한 과제로 제시한다.

## ABSTRACT

IACS UR E26 sets mandatory cyber resilience requirements for ships. Its Section 1.3.2 defines the scope in terms of Operational Technology (OT) systems and brings shipboard Information Technology (IT) into scope not as systems in themselves but only as IP-based communication interfaces from CBSs in scope; the resulting safety therefore rests on an assumption that control at the security zone boundary is effective. This paper compiles the "Demonstration of compliance" clauses attached to each requirement and observes that, while Section 4.2.1.2 itself states that breaching the perimeter is always possible, the commissioning-phase demonstrations consist of conformance checks against approved documents together with denial-of-service tests. Three points are accordingly raised as requiring confirmation: how the IT domain left outside the scope is actually managed, how the completeness of the approved documentation itself can be verified independently of that documentation, and in what form a test addressing boundary bypass could be carried out.

**키워드** : 선박 사이버보안, IACS UR E26, 적용 범위, 경계 방어, 적합성 확인

**Keywords** : Maritime cyber security, IACS UR E26, Scope of applicability, Perimeter defence, Compliance demonstration

---

## Ⅰ. 서 론

선박은 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서 더 이상 육상과 분리된 폐쇄 환경이 아니다. IMO 결의서 MSC.428(98)이 사이버 리스크를 안전관리체제에서 다루도록 요구한 이후, 국제선급연합회(IACS)는 이를 검사 가능한 기술 기준으로 구체화하여 UR E26[1]과 UR E27[2]을 제정하였다. UR E26 Rev.1은 2024년 7월 1일 이후 건조계약된 선박에 적용되며, 식별·보호·탐지·대응·복구의 기능 요소별로 요구사항을 구성하고 설계·건조·시운전·운항의 전 생애주기에 걸쳐 문서 제출과 실증을 요구한다. 비강제 지침만 존재하던 이전 상황과 비교하면 분명한 진전이다.

강제 규정이 실제로 무엇을 보장하는지는 요구사항의 문언만으로 정해지지 않는다. 규정은 요구사항과 함께 그 이행을 확인하는 절차를 두며, 확인 절차가 다루지 않는 부분은 요구사항이 존재하더라도 이행 여부가 판정되지 않은 채 남는다. UR E26은 이 점에서 특징적인 구조를 가진다. 각 요구사항마다 "Demonstration of compliance" 항을 두어 설계·건조·시운전·운항의 단계별로 무엇을 실증하여야 하는지를 명시하고, 시운전 단계의 실증 내용은 Ship cyber resilience test procedure로 집약된다(5.2.1)[1]. 즉 규정이 요구하는 실증의 범위가 조문 수준에서 확인 가능하다.

동시에 UR E26은 적용 범위를 OT 시스템 중심으로 정의하고, 선내 IT 영역은 시스템 자체가 아니라 적용 대상 CBS로부터 향하는 통신 인터페이스로만 범위에 포함한다(1.3.2)[1]. 이 구조에서 IT 영역으로부터 유입되는 위협에 대한 방어는 보안 구역의 경계에 위임된다. 그렇다면 그 경계가 우회될 수 있는지를 확인하는 절차는 규정 안에 있는가. 이것이 본 논문의 질문이다.

Ⅱ장에서 기존 연구가 다루지 않은 지점을 정리하고, Ⅲ장에서 UR E26의 범위 설정이 의존하는 가정을 조문에서 확인한 뒤 단계별 실증 요구를 정리하여 확인이 필요한 지점을 기술한다. Ⅳ장에서 결론을 기술한다. 본 논문은 조문의 범위에서 이 질문을 다루며, 실선 환경에서의 확인과 선급의 검사 실무에 대한 조사는 포함하지 않는다. UR E26 6.4가 개별 CBS를 적용 대상에서 명시적으로 제외하는 절차를 별도로 두고 있는 점은 본 논문과 층위를 달리하므로 여기서는 다루지 않으며, 이에 대하여는 별도의 연구가 필요하다.

## Ⅱ. 기존 연구의 한계

선박 사이버보안의 위협 분석은 꾸준히 축적되어 왔다. 조용현과 차영균[3]은 이해관계자를 고려한 데이터 흐름도에 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였으며, 이후 MITRE ATT&CK 프레임워크를 선박 장비에 적용한 연구도 이어졌다. 그러나 이들 연구는 선박이라는 대상을 놓고 위협을 도출할 뿐, 강제 규정이 그 위협 가운데 무엇을 확인하도록 요구하는지와는 연결되어 있지 않다.

UR E26을 직접 다룬 연구는 규정을 준수 대상으로 놓는다. 사이버 복원력의 정의를 조사하고 동 UR을 NIST 체계와 비교한 연구[4], 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[5], 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[6]가 있다. 이들은 "요구사항을 어떻게 충족할 것인가" 또는 "다른 프레임워크와 무엇이 다른가"에 답한다.

두 계열 모두에서 다루어지지 않은 질문이 있다. 규정이 요구하는 실증을 모두 통과한 선박에 대하여, 그 통과가 보장하는 것과 보장하지 않는 것은 각각 무엇인가. 본 논문이 확인한 범위에서는 UR E26의 실증 요구 자체를 분석 대상으로 삼은 연구가 발견되지 않았다.

## Ⅲ. 경계 방어 가정과 확인이 필요한 지점

### 3.1 적용 범위가 전제하는 경계 방어

UR E26 1.3.2는 적용 대상을 두 항으로 규정한다. a)항은 물리 프로세스를 제어하거나 감시하는 OT 시스템을 대상으로 하고, 추진·조타·계류·발전 및 배전·화재탐지·빌지 및 밸러스트·수밀 및 침수 탐지·조명과 안전 계통을 열거하며, 법정 요건이 요구하는 항해 시스템과 선급 규칙·법정 요건이 요구하는 내외부 통신 시스템을 추가로 포함한다. b)항은 "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems"를 대상으로 하고, 그 "other systems"의 예시로 여객 서비스 시스템, 여객용 네트워크, 관리 네트워크, 승무원 복지 시스템, 그리고 "any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)"를 든다[1].

여기서 범위에 들어오는 것은 인터페이스이지 그 인터페이스가 향하는 시스템이 아니다. 선내 업무망, 여객망, 승무원 복지 시스템은 그 자체로는 동 UR의 요구사항을 적용받지 않는다. 4.2.1.3은 적용 범위 밖의 시스템·네트워크·CBS를 비신뢰 네트워크로 간주하고 보안 구역으로부터 물리적으로 분할할 것을 요구하며, 4.2.6은 비신뢰 네트워크와의 통신에 대한 보호를 요구한다[1]. 즉 UR E26이 IT 영역을 다루지 않는 것은 아니며, 정확히는 IT 영역 자체의 보안 수준을 요구하는 대신 그 영역과의 경계에서 통제가 이루어지도록 설계되어 있다.

이 구조는 경계의 통제가 유효하다는 가정에 의존한다. 그리고 규정은 그 가정이 무조건 성립하지는 않음을 스스로 진술한다. 4.2.1.2는 망 분할의 근거를 설명하면서 "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, breaching that perimeter is always possible"이라고 기술한다[1]. 경계 돌파가 언제나 가능하다는 인식은 규정 자신의 것이다.

### 3.2 단계별 실증 요구의 정리

그렇다면 규정은 이 가능성을 어떻게 확인하도록 요구하는가. UR E26은 각 요구사항의 마지막 항을 "Demonstration of compliance"로 두고 설계·건조·시운전·운항 단계별로 실증 내용을 규정하며, 5.2.1은 Ship cyber resilience test procedure의 내용이 "specified for the Commissioning phase in each subsection"임을 명시한다[1]. 따라서 시운전 단계에서 선급 입회 아래 수행되는 시험의 총합은 각 절의 시운전 항을 모으면 확정된다. 경계와 직접 관련되는 네 개 절을 정리하면 표 1과 같다.

**표 1. UR E26의 경계 관련 실증 요구 (조문 정리)**

| 절 | 설계·건조 단계 | 시운전 단계 실증 요구 | 확인의 성격 |
|---|---|---|---|
| 4.2.1 보안 구역·망 분할 | 구역·통로 도면과 사이버보안 설계기술서 제출, 건조 중 도면 갱신 | 승인 문서대로 구역이 구현되었는지 확인(설치 검사, 망 스캔 등), 구역 경계가 승인 기술서에 기재된 트래픽만 허용하는지 확인(방화벽 규칙 평가, 포트 스캔 등) | 적합성 확인 |
| 4.2.2 망 보호 | 양 단계 모두 "No requirements" | 구역 경계 장치를 대상으로 한 서비스 거부 시험, 각 망 구간 내부에서 발생하는 과다 데이터 흐름에 대한 서비스 거부 시험, 불필요 기능·포트·프로토콜·서비스의 제거 확인 | 가용성 시험, 적합성 확인 |
| 4.2.6 원격 접속·비신뢰망 통신 | 설계기술서에 해당 CBS 식별 및 준수 내용 기재, 건조 중 비신뢰망 통신의 일시적 사용 관리 | 통신 보안 및 하위 버전으로의 협상 불가 확인, 다중요소 인증, 로그인 시도 횟수 제한, 선내 승인 절차, 세션 종료, 세션 로깅 | 기능 존재 확인 |
| 4.3.1 감시 | 양 단계 모두 "No requirements" | 망 연결 단절 시 경보와 기록, 비정상 과다 트래픽 탐지와 경보, 네트워크 폭주 시 안전 거동, 감사 기록 생성, 침입탐지시스템이 설치된 경우 그것이 수동적임을 실증 | 고장·가용성 시험, 기능 존재 확인 |

먼저 망 보호(4.2.2)와 감시(4.3.1)는 설계·건조 단계의 실증 요구가 모두 "No requirements"이므로, 이 두 요구사항이 확인되는 시점은 시운전 단계뿐이다. 그 시운전 항을 모아 보면 두 가지가 드러난다.

첫째, 공격자의 행위를 모사하는 시험은 4.2.2의 서비스 거부 시험 2건뿐이며 그 대상은 가용성이다. 승인된 경계를 우회하여 적용 범위 안쪽에 도달할 수 있는지를 확인하는 항목은, 본 논문이 확인한 범위에서 동 UR 어디에서도 확인되지 않는다. 장비 수준을 다루는 UR E27[2] 역시 6.3.2에서 공급자가 요구된 보안 능력을 시험하도록 규정하므로 능력의 구현을 실증하는 성격이며, 우회 시험에 해당하는 요구는 확인되지 않는다. 한편 4.3.1의 시운전 항은 침입탐지시스템이 설치된 경우 그것이 수동적이며 CBS의 의도된 동작에 영향을 주는 보호 기능을 작동시키지 않을 것을 실증하도록 요구한다. 이는 검증 활동이 운항에 미치는 영향을 규정이 함께 고려하고 있음을 보여준다.

둘째, 보다 근본적인 것은 4.2.1의 시운전 확인이 "승인된 문서에 따라" 구역이 구현되었는지와 "승인된 기술서에 기재된" 트래픽만 경계를 통과하는지를 대상으로 한다는 점이다. 이는 문서를 기준선으로 삼는 적합성 확인이다. 기재되지 않은 연결은 4.2.1.1의 "Only explicitly allowed traffic shall traverse a security zone boundary"에 어긋나고, 4.2.1.4.1은 기재 대상에 이산 신호와 시리얼 통신까지 포함시켜 그 범위를 넓게 설정하고 있으므로, 규정이 미기재 연결을 허용하는 것은 아니다. 다만 금지되어 있다는 것과 확인 절차가 그것을 대상으로 삼는다는 것은 별개이다. 승인 설계를 기준선으로 삼는 확인은 기재된 것이 구현되었는지를 다루므로, 문서 자체의 완전성은 같은 방법으로 검증되지 않는다. 4.2.1.4.3이 설치 검사와 망 스캔을 확인 방법으로 예시하고 있어 실무상 미기재 연결이 드러날 여지는 있으나, 규정은 확인의 기준을 승인 설계에 두고 그 방법을 지정하지 않는다. 정비 중 일시적으로 형성되는 연결은 1.3.2 b)의 예시에 명시되어 있으면서도 그 성질상 준공 도면에 남지 않는다.

정리하면 규정은 경계 돌파가 언제나 가능하다고 인식하면서, 경계가 도면대로 세워졌는지는 확인하되 그것이 돌파될 수 있는지를 확인하는 절차는 두지 않는 것으로 읽힌다.

### 3.3 확인이 필요한 지점

앞의 정리는 UR E26의 범위 설정을 문제 삼기 위한 것이 아니다. 선내 IT 영역 전체에 OT와 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 경계에 통제를 집중하는 것은 합리적인 설계이다. 다만 그 설계가 전제하는 가정과 그것을 확인하는 절차 사이에는 간격이 있다. 확인이 필요하다고 본 지점은 세 가지이다.

**첫째, 적용 범위 밖 IT 영역에 대한 조건이 없다는 점이다.** 1.3.2는 적용 대상 시스템의 목록으로 서술되어 있으나, 그 실질은 경계에서의 통제로 충분하다는 판단이다. 조문은 IT 영역을 비신뢰 네트워크로 규정할 뿐 그 영역 자체에는 조건을 두지 않으므로, 경계가 감당하는 부담이 어느 정도인지가 드러나지 않는다. 선내 업무망과 여객망의 실제 구성과 관리 수준이 이 판단을 지탱할 수 있는지에 대한 확인이 필요하다.

**둘째, 실증의 기준선이 승인 문서라는 점이다.** 승인 문서에 기재되지 않은 연결은 그 자체로 규정에 어긋나므로 있어서는 안 되는 것이다. 문제는 그 금지가 아니라, 금지가 지켜졌는지를 확인하는 방법이 규정에 지정되어 있지 않다는 데 있다. 승인 설계를 기준선으로 삼는 확인은 문서 자체의 완전성을 다루지 못한다. IP 기반 통신뿐 아니라 시리얼 링크, 무선, 이동형 매체를 포함하여 선박의 실제 연결 구성을 문서와 독립적으로 파악하는 방법이 성립하는지에 대한 확인이 필요하다.

**셋째, 경계 우회를 다루는 시험이 없다는 점이다.** 규정이 요구하는 시험 가운데 공격자의 행위를 모사하는 것은 서비스 거부 시험뿐이며, 경계를 우회하여 적용 범위 안쪽에 도달할 수 있는지는 시험 대상이 아니다. 다만 4.3.1이 침입탐지시스템에 수동성을 요구하는 데에서 보이듯 규정은 검증 활동이 운항에 미치는 영향을 함께 고려하고 있으므로, 그러한 시험을 어떤 형태로 수행할 수 있는지는 시험 환경에서의 확인을 거쳐야 한다.

## Ⅳ. 결 론

본 논문은 UR E26이 요구하는 실증의 범위를 조문 수준에서 정리하였다. 동 UR은 적용 범위를 OT 시스템 중심으로 정의하고 선내 IT 영역은 인터페이스로만 포함하므로, 그 안전성은 보안 구역 경계의 통제가 유효하다는 가정에 의존한다. 규정은 4.2.1.2에서 경계 돌파가 언제나 가능함을 스스로 진술하면서도, 각 요구사항에 부속된 실증 요구는 승인 문서에 따른 적합성 확인과 가용성 시험에 머무른다. 공격자의 행위를 모사하는 항목은 서비스 거부 시험 2건이며, 승인된 경계를 우회할 수 있는지를 확인하는 항목은 본 논문이 확인한 범위에서 발견되지 않았다. 나아가 문서를 기준선으로 하는 적합성 확인에서는 문서화되지 않은 경로가 원리적으로 확인 대상이 되지 않는다.

이로부터 적용 범위 밖 IT 영역의 관리 수준, 승인 문서의 완전성을 확인하는 방법, 경계 우회를 다루는 시험의 수행 형태라는 세 지점에서 확인이 필요하다고 보았다. 이들은 조문이 아니라 실선과 시험 환경에서 확인되는 것이며, 이에 대한 연구가 필요하다. 강제 규정을 볼 때 요구사항의 문언과 함께 그에 부속된 실증 요구를 보는 관점이 유효할 수 있음을 UR E26을 대상으로 확인하였다.

본 논문은 조문에 기초하므로, 선급의 검사 실무가 이 지점들을 어느 정도 보완하는지와 동 UR 1.3.2가 대체 수용을 허용하는 IEC 61162-460 등 표준의 시험 요구가 이에 해당하는지는 확인하지 못하였다. 이에 대하여도 연구가 필요하다.

## References

[1] IACS, UR E26 Cyber resilience of ships, Rev.1, Nov. 2023.
[2] IACS, UR E27 Cyber resilience of on-board systems and equipment, Rev.1, Sep. 2023.
[3] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
[4] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024.
[5] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024.
[6] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," Turkish Journal of Maritime and Marine Sciences, vol. 10, Special Issue 1, pp. 31-50, 2024.

---
---

# 이하 원고 외 — 작업 메모 (투고본에서 삭제)

## A. 자기표절 회피 대조

정식 논문 후보인 `outputs/2026-08-20_conference-paper_R3.md`(이하 R3)와의 관계를 항목별로 정리한다.

| 축 | R3 (정식 투고 예정) | 본 원고 (학술대회) |
|---|---|---|
| 분석 대상 조문 | **6.4** 제외 판정 기준 (+ 초판 대조) | **1.3.2** 적용 범위 정의 + 각 절의 **Demonstration of compliance** |
| 이탈의 성격 | 개별 CBS를 요구사항 적용에서 **명시적으로 배제** | 영역 단위로 **애초에 판단 대상에 들어오지 않음** |
| 핵심 주장 | 제외 판정 단계에 전이 착안점이 없고 판정이 불확정적이다 | 범위 설정이 의존하는 경계 가정을 검증하는 시험 요구가 없다 |
| 방법 | Rev.1 ↔ 초판 항목 단위 대조 | 단계별 실증 요구의 열거와 성격 분류 |
| 근거의 성격 | 판(version) 간 차이 | 요구사항과 그 실증 요구 사이의 불일치 |
| 결과물 | 잔여 위협 경로 1건 예시 (시리얼 talker 계측기) | 확인이 필요한 지점 3건 (범위 밖 IT 영역의 조건 부재 / 실증 기준선이 승인 문서 / 우회 시험 부재) |
| 주의 | — | 미기재 연결은 4.2.1.1·4.2.1.4.1 위반이므로 "존재 여부"를 논점으로 삼지 말 것. 논점은 **금지 여부가 아니라 확인 방법의 부재**이다 |
| 초판(Apr 2022) | 핵심 근거 | **사용하지 않음** |
| 시리얼 위협 경로 | IV장 전체 | **사용하지 않음** (3.3 둘째 항목에서 확인 대상의 하나로만 언급) |
| ATT&CK 매핑 | 사용 | **사용하지 않음** |

**중복 서술 관리**
- 서론 첫 문단의 배경 서술은 R3과 소재가 같으므로 **문장을 새로 썼다.** 투고 전 두 원고를 나란히 놓고 문장 단위로 재확인할 것.
- 관련 연구([3]~[6])는 동일 문헌을 인용하나, R3은 "제외를 다루지 않았다"로, 본 원고는 "실증 요구를 다루지 않았다"로 서로 다른 gap을 지목한다. 요약 문장도 다르게 썼다.
- 4.2.1.3(비신뢰망 물리적 분할)은 양쪽에 등장하나, R3은 "Alternatively" 대안의 **순환성**을 논하고 본 원고는 IT 영역이 **경계로만 다루어진다**는 사실 확인에 그친다. 본 원고에서 순환성 논거는 **의도적으로 쓰지 않았다.**
- 4.2.1.1의 `isolated` 이중 정의, 4.2.1.4.1의 시리얼 기술 의무를 근거로 삼는 논증은 R3의 것이므로 본 원고에서 **사용하지 않았다.** 4.2.1.4.1은 표 1과 3.2에서 사실 확인용으로만 인용된다.
- 6.4에 관한 언급은 서론 마지막 한 문장("여기서는 다루지 않는다")뿐이다.

**게재 순서** — 본 원고를 먼저 발표하고 R3을 정식 투고하는 순서가 안전하다. 두 원고의 주장이 겹치지 않으므로 R3에서 본 원고를 선행 문헌으로 인용할 필요는 없으나, KIICE의 후속 게재 정책은 투고 전에 확인할 것(`outputs/NOTICE_참고문헌_확인필요.md`).

## B. 원문 대조 검증 메모

`rules/UR-E26-Rev.1-Nov-2023-CR.pdf`, `rules/UR-E27-Rev.1-Sep-2023-CLN.pdf` 원문에서 직접 확인함. [규정]

| 본문 서술 | 원문 |
|---|---|
| 1.3.2 b)가 인터페이스만을 범위로 함 | "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems." 예시로 passenger or visitor servicing and management systems / passenger-facing networks / administrative networks / crew welfare systems / "any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)" |
| 경계 돌파 가능성의 자기 진술 | 4.2.1.2 "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, **breaching that perimeter is always possible**." |
| 범위 밖 시스템의 취급 | 4.2.1.3 "Systems, networks or CBSs outside the scope of applicability of this UR are considered untrusted networks and shall be physically segmented from security zones required by this UR." |
| 4.2.2 설계·건조 단계 요구 없음 | 4.2.2.4.1 "No requirements." / 4.2.2.4.2 "No requirements." |
| 4.2.2 시운전 시험 3건 | 4.2.2.4.3: ① 경계 보호 장치 대상 DoS 시험 ② 각 망 구간 내부 기원 과다 데이터 흐름 DoS 시험(flooding + application layer attack) ③ 불필요 기능·포트·프로토콜·서비스 제거 확인(analytic evaluation and port scanning). ②③은 CBS 인증 시 수행되었으면 생략 가능 |
| 4.2.1 시운전 확인이 문서 기준임 | 4.2.1.4.3 "the security zones on board are implemented **in accordance with the approved documents**…" / "security zone boundaries allow only the traffic that has been **documented in the approved Cyber security description**" |
| 4.3.1 IDS 수동성 요구 | 4.3.1.4.3 "If Intrusion detection systems are implemented, demonstrate that this is **passive** and will not activate protection functions that may affect intended operation of the CBSs." |
| 4.3.1 설계·건조 단계 요구 없음 | 4.3.1.4.1 "No requirements." / 4.3.1.4.2 "No requirements." |
| 시험 총합이 시운전 항으로 확정됨 | 5.2.1 "The content of this document is specified for the Commissioning phase in each subsection 'Demonstration of compliance' in section 4." |
| E27의 시험 성격 | E27 6.3.2 "The supplier shall test the required security capabilities on the system to be delivered." E27 전문에서 penetration / fuzz / bypass / robustness 문자열 미검출 |
| 4.2.6 시운전 시험 항목 | 4.2.6.4.3의 7개 항목(하위 버전 협상 불가, MFA, 로그인 시도 제한, 선내 명시적 승인, 세션 종료, 세션 로깅, 공급자 절차) |

**[추론] 표시가 필요한 서술** — 아래는 조문에 직접 적힌 것이 아니라 본 논문의 해석이다. 심사에서 공격받을 지점이므로 문안을 지킬 것.
- "적합성 확인은 문서를 기준선으로 하므로 미문서화 경로가 원리적으로 확인 대상이 아니다" → 4.2.1.4.3 문언에서 도출한 추론. 단, 동 항이 "inspection of the physical installation, network scanning and/or other methods"를 예시하므로 **실무상 미문서화 경로가 발견될 여지는 있다.** 본문은 "원리적으로"로 한정하여 이 여지를 배제하지 않았다. 심사 대응 시 이 한정을 근거로 삼을 것.
- "IT 영역에 아무런 조건도 두지 않는다" → 4.2.5(무선), 4.2.6(원격 접속), 4.2.7(이동형 기기)이 존재하므로 **범위 밖 시스템 자체에 대한 요구가 없다**는 뜻으로만 읽혀야 한다. 본문은 "비신뢰 네트워크로 규정할 뿐 그 영역에 대하여"로 한정했으나, 심사에서 오독될 수 있으니 필요 시 각주로 4.2.5~4.2.7의 존재를 명시할 것.

## C. 남은 항목

| 항목 | 비고 |
|---|---|
| 저자행 표기 | `¹'*`의 아포스트로피를 KIICE 양식에 맞게 확인할 것 |
| 분량 확인 | KIICE 양식(2단)으로 조판 후 3쪽 초과 여부 확인. 초과 시 Ⅱ장을 3~4문장으로 축약하고 표 1에서 4.2.6 행을 각주로 내릴 것 |
| 4.2.7(이동형 기기)·4.4(대응)·4.5(복구)의 시운전 항 | 표 1에 넣지 않았다. 경계와 직접 관련되지 않는다는 판단이나, 전수 정리 후 "공격 모사 시험은 DoS 2건뿐"이라는 주장을 재확인할 것 |
| Rec.166 | E26 1.3.4가 명시하는 비강제 권고. 경계 검증에 관한 기술 요구가 있는지 미확인(`rules/rec166corr2.pdf`) |
| [4] 김진·이삼열 원본 | `papers/`에 없음. 서지사항만 확인된 상태 |
