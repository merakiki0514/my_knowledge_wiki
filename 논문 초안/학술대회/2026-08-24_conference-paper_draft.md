# IACS UR E26의 경계 통제 가정과 실증 요구의 범위

정성윤¹ · 이대성¹'* / ¹한국해양대학교
E-mail : meraki4.1st@gmail.com / dslee@kmou.ac.kr

On the Perimeter Control Assumption and the Scope of Compliance Demonstration in IACS UR E26
Sung-yoon Jung¹ · Dae-sung Lee¹'* / ¹Korea Maritime and Ocean University

---

## 요 약

IACS UR E26은 선박의 사이버 복원력에 관한 강제 요구사항이다. 동 UR 1.3.2는 적용 대상을 운용기술(OT) 시스템으로 정의하고 선내 정보기술(IT) 영역은 시스템 자체가 아니라 적용 대상 CBS로부터 향하는 IP 기반 통신 인터페이스로만 범위에 포함하므로, 그 안전성은 보안 구역 경계의 통제가 유효하다는 가정에 의존한다. 본 논문은 각 요구사항에 부속된 "Demonstration of compliance"를 단계별로 정리하여, 규정이 4.2.1.2에서 경계 우회의 가능성을 스스로 인정하면서도 시운전 단계의 실증은 승인 문서에 따른 적합성 확인과 서비스 거부 시험에 머무른다는 점을 확인하였다. 이로부터 적용 범위 밖 IT 영역의 실제 관리 수준과 경계 우회를 다루는 시험의 수행 형태라는 두 지점을 확인이 필요한 과제로 제시한다.

## ABSTRACT

IACS UR E26 sets mandatory cyber resilience requirements for ships. Its Section 1.3.2 defines the scope in terms of Operational Technology (OT) systems and brings shipboard Information Technology (IT) into scope not as systems in themselves but only as IP-based communication interfaces from CBSs in scope; the resulting safety therefore rests on an assumption that control at the security zone boundary is effective. This paper compiles the "Demonstration of compliance" clauses attached to each requirement and observes that, while Section 4.2.1.2 itself states that breaching the perimeter is always possible, the commissioning-phase demonstrations consist of conformance checks against approved documents together with denial-of-service tests. Two points are accordingly raised as requiring confirmation: how the IT domain left outside the scope is actually managed, and in what form a test addressing boundary bypass could be carried out.

**키워드** : 선박 사이버보안, IACS UR E26, 적용 범위, 경계 통제, 적합성 확인

**Keywords** : Maritime cyber security, IACS UR E26, Scope of applicability, Perimeter control, Compliance demonstration

---

## Ⅰ. 서 론

선박은 항해·기관·화물 시스템이 상호 연결되고 위성통신을 통한 선육간 데이터 공유가 일상화되면서 더 이상 육상과 분리된 폐쇄 환경이 아니다. IMO 결의서 MSC.428(98)이 사이버 리스크를 안전관리체제에서 다루도록 요구한 이후, 국제선급연합회(IACS)는 이를 검사 가능한 기술 기준으로 구체화하여 UR E26[1]과 UR E27[2]을 제정하였다. UR E26 Rev.1은 2024년 7월 1일 이후 건조계약된 선박에 적용되며, 식별·보호·탐지·대응·복구의 기능 요소별로 요구사항을 구성하고 설계·건조·시운전·운항의 전 생애주기에 걸쳐 문서 제출과 실증을 요구한다. 비강제 지침만 존재하던 이전 상황과 비교하면 분명한 진전이다.

강제 규정이 실제로 무엇을 보장하는지는 요구사항의 문언만으로 정해지지 않는다. 규정은 요구사항과 함께 그 이행을 확인하는 절차를 두며, 확인 절차가 다루지 않는 부분은 요구사항이 존재하더라도 이행 여부가 판정되지 않은 채 남는다. UR E26은 이 점에서 특징적인 구조를 가진다. 각 요구사항마다 "Demonstration of compliance" 항을 두어 설계·건조·시운전·운항의 단계별로 무엇을 실증하여야 하는지를 명시하고, 시운전 단계의 실증 내용은 Ship cyber resilience test procedure로 집약된다(5.2.1)[1]. 즉 규정이 요구하는 실증의 범위가 조문 수준에서 확인 가능하다.

동시에 UR E26은 적용 범위를 OT 시스템 중심으로 정의하고, 선내 IT 영역은 시스템 자체가 아니라 적용 대상 CBS로부터 향하는 통신 인터페이스로만 범위에 포함한다(1.3.2)[1]. 이 구조에서 IT 영역으로부터 유입되는 위협에 대한 통제는 보안 구역의 경계에 위임된다. 본 논문은 그 경계의 우회 가능성을 확인하는 절차가 규정 안에 있는지를 질문으로 삼는다.

Ⅱ장에서 기존 연구가 다루지 않은 지점을 정리하고, Ⅲ장에서 UR E26의 범위 설정이 의존하는 가정을 조문에서 확인한 뒤 단계별 실증 요구를 정리하여 확인이 필요한 지점을 기술한다. Ⅳ장에서 결론을 기술한다. 본 논문은 조문의 범위에서 이 질문을 다루며, 실선 환경에서의 확인과 선급의 검사 실무에 대한 조사는 포함하지 않는다. UR E26 6.4가 개별 CBS를 적용 대상에서 명시적으로 제외하는 절차를 별도로 두고 있는 점은 본 논문과 층위를 달리하므로 여기서는 다루지 않으며, 이에 대하여는 별도의 연구가 필요하다.

## Ⅱ. 기존 연구의 한계

선박 사이버보안의 위협 분석은 꾸준히 축적되어 왔다. 조용현과 차영균[3]은 이해관계자를 고려한 데이터 흐름도에 STRIDE와 Attack Tree를 적용하여 206건의 위협을 식별하였으며, 이후 MITRE ATT&CK 프레임워크를 선박 장비에 적용한 연구도 이어졌다. 그러나 이들 연구는 선박이라는 대상을 놓고 위협을 도출할 뿐, 강제 규정이 그 위협 가운데 무엇을 확인하도록 요구하는지와는 연결되어 있지 않다.

UR E26을 직접 다룬 연구는 규정을 준수 대상으로 놓는다. 사이버 복원력의 정의를 조사하고 동 UR을 NIST 체계와 비교한 연구[4], 요구조건과 제출·유지 문서를 정리하고 전주기 대응 기술을 제안한 연구[5], 요구사항을 선박 OT 시스템별 점검 항목으로 변환한 연구[6]가 있다. 이들은 "요구사항을 어떻게 충족할 것인가" 또는 "다른 프레임워크와 무엇이 다른가"에 답한다.

두 계열 모두에서 다루어지지 않은 질문이 있다. 규정이 요구하는 실증을 모두 통과한 선박에 대하여, 그 통과가 보장하는 것과 보장하지 않는 것을 구분하는 질문이다. 본 논문이 확인한 범위에서는 UR E26의 실증 요구 자체를 분석 대상으로 삼은 연구가 발견되지 않았다.

## Ⅲ. 경계 통제 가정과 확인이 필요한 지점

### 3.1 적용 범위가 전제하는 경계 통제

UR E26 1.3.2는 적용 대상을 두 항으로 규정한다. a)항은 물리 프로세스를 제어하거나 감시하는 OT 시스템을 대상으로 하고, 추진·조타·계류·발전 및 배전·화재탐지·빌지 및 밸러스트·수밀 및 침수 탐지·조명과 안전 계통을 열거하며, 법정 요건이 요구하는 항해 시스템과 선급 규칙·법정 요건이 요구하는 내외부 통신 시스템을 추가로 포함한다. b)항은 "Any Internet Protocol (IP)-based communication interface from CBSs in scope of this UR to other systems"를 대상으로 하고, 그 "other systems"의 예시로 여객 서비스 시스템, 여객용 네트워크, 관리 네트워크, 승무원 복지 시스템, 그리고 "any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)"를 든다[1].

여기서 범위에 들어오는 것은 인터페이스이지 그 인터페이스가 향하는 시스템이 아니다. 선내 업무망, 여객망, 승무원 복지 시스템은 그 자체로는 동 UR의 요구사항을 적용받지 않는다. 4.2.1.3은 적용 범위 밖의 시스템·네트워크·CBS를 비신뢰 네트워크로 간주하고 보안 구역으로부터 물리적으로 분할할 것을 요구하며, 4.2.6은 비신뢰 네트워크와의 통신에 대한 보호를 요구한다[1]. 즉 UR E26이 IT 영역을 다루지 않는 것은 아니며, 정확히는 IT 영역 자체의 보안 수준을 요구하는 대신 그 영역과의 경계에서 통제가 이루어지도록 설계되어 있다.

이 구조는 경계의 통제가 유효하다는 가정에 의존하는데, 규정은 그 가정이 무조건 성립하지는 않음을 스스로 진술한다. 4.2.1.2는 망 분할의 근거를 설명하면서 "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, breaching that perimeter is always possible"이라고 기술한다[1]. 경계 우회가 언제나 가능하다는 인식은 규정 자신의 것이다.

### 3.2 단계별 실증 요구의 정리

규정이 이 가능성을 어떻게 확인하도록 요구하는지는 각 요구사항의 마지막 항인 "Demonstration of compliance"에서 드러난다. UR E26은 이 항을 통해 설계·건조·시운전·운항 단계별로 실증 내용을 규정하며, 5.2.1은 Ship cyber resilience test procedure의 내용이 "specified for the Commissioning phase in each subsection"임을 명시한다[1]. 따라서 시운전 단계에서 선급 입회 아래 수행되는 시험의 총합은 각 절의 시운전 항을 모으면 확정된다. 경계와 직접 관련되는 네 개 절을 정리하면 표 1과 같다.

**표 1. UR E26의 경계 관련 실증 요구 (조문 정리)**

| 절 | 설계·건조 단계 | 시운전 단계 실증 요구 | 확인의 성격 |
|---|---|---|---|
| 4.2.1 보안 구역·망 분할 | 구역·통로 도면과 사이버보안 설계기술서 제출, 건조 중 도면 갱신 | 승인 문서대로 구역이 구현되었는지 확인(설치 검사, 망 스캔 등), 구역 경계가 승인 기술서에 기재된 트래픽만 허용하는지 확인(방화벽 규칙 평가, 포트 스캔 등) | 적합성 확인 |
| 4.2.2 망 보호 | 양 단계 모두 "No requirements" | 구역 경계 장치를 대상으로 한 서비스 거부 시험, 각 망 구간 내부에서 발생하는 과다 데이터 흐름에 대한 서비스 거부 시험, 불필요 기능·포트·프로토콜·서비스의 제거 확인 | 가용성 시험, 적합성 확인 |
| 4.2.6 원격 접속·비신뢰망 통신 | 설계기술서에 해당 CBS 식별 및 준수 내용 기재, 건조 중 비신뢰망 통신의 일시적 사용 관리 | 통신 보안 및 하위 버전으로의 협상 불가 확인, 다중요소 인증, 로그인 시도 횟수 제한, 선내 승인 절차, 세션 종료, 세션 로깅 | 기능 존재 확인 |
| 4.3.1 감시 | 양 단계 모두 "No requirements" | 망 연결 단절 시 경보와 기록, 비정상 과다 트래픽 탐지와 경보, 네트워크 폭주 시 안전 거동, 감사 기록 생성, 침입탐지시스템이 설치된 경우 그것이 수동적임을 실증 | 고장·가용성 시험, 기능 존재 확인 |

망 보호(4.2.2)와 감시(4.3.1)는 설계·건조 단계의 실증 요구가 모두 "No requirements"이므로, 이 두 요구사항이 확인되는 시점은 시운전 단계뿐이다. 그 시운전 항을 모아 보면, 공격자의 행위를 모사하는 시험은 4.2.2의 서비스 거부 시험 2건뿐이며 그 대상은 가용성이다. 승인된 경계를 우회하여 적용 범위 안쪽에 도달할 수 있는지를 확인하는 항목은 본 논문이 검토한 범위에서 동 UR 어디에서도 발견되지 않는다. 장비 수준을 다루는 UR E27[2] 역시 6.3.2에서 공급자가 요구된 보안 능력을 시험하도록 규정하므로 능력의 구현을 실증하는 성격이며, 우회 시험에 해당하는 요구는 발견되지 않는다. 이 점은 원격 접속을 다루는 4.2.6에서 뚜렷하다. 동 절의 근거 항은 공격자가 인터넷 연결을 통해 CBS에 접근하여 "even achieve full control of the CBS"에 이를 수 있음을 명시하여[1] 네 개 절 가운데 침입을 가장 직접적으로 상정하면서도, 그 시운전 항은 다중요소 인증과 세션 관리, 로깅이 갖추어져 있는지를 확인하는 데 그친다. 기능의 존재는 확인되나 그 기능이 우회되는지는 확인되지 않는다. 한편 4.3.1의 시운전 항은 침입탐지시스템이 설치된 경우 그것이 수동적이며 CBS의 의도된 동작에 영향을 주는 보호 기능을 작동시키지 않을 것을 실증하도록 요구한다. 이는 실증 활동이 운항에 미치는 영향을 규정이 함께 고려하고 있음을 보여준다.

정리하면 규정은 경계 우회가 언제나 가능하다고 인식하면서, 표 1의 4.2.1이 보여주듯 경계가 도면대로 세워졌는지는 확인하되 그것이 우회될 수 있는지를 확인하는 절차는 두지 않는 것으로 읽힌다.

### 3.3 확인이 필요한 지점

앞의 정리는 UR E26의 범위 설정을 문제 삼기 위한 것이 아니다. 선내 IT 영역 전체에 OT와 동일한 요구사항을 적용하는 것은 현실적이지 않으며, 경계에 통제를 집중하는 것은 합리적인 설계이다. 다만 그 설계가 전제하는 가정과 그것을 확인하는 절차 사이에는 간격이 있다. 확인이 필요하다고 본 지점은 두 가지이다.

**첫째, 적용 범위 밖 IT 영역에 대한 조건이 없다는 점이다.** 1.3.2는 적용 대상 시스템의 목록으로 서술되어 있으나, 그 실질은 경계에서의 통제로 충분하다는 판단이다. 조문은 IT 영역을 비신뢰 네트워크로 규정할 뿐 그 영역 자체에는 조건을 두지 않으므로, 경계가 감당하는 부담이 어느 정도인지가 드러나지 않는다. 선내 업무망과 여객망의 실제 구성과 관리 수준이 이 판단을 지탱할 수 있는지에 대한 확인이 필요하다.

**둘째, 경계 우회를 다루는 시험이 없다는 점이다.** 앞서 정리한 대로 경계를 우회하여 적용 범위 안쪽에 도달할 수 있는지는 시험 대상이 아니다. 다만 4.3.1이 침입탐지시스템에 수동성을 요구하는 데에서 보이듯 규정은 실증 활동이 운항에 미치는 영향을 함께 고려하고 있으므로, 그러한 시험을 어떤 형태로 수행할 수 있는지는 시험 환경에서의 확인을 거쳐야 한다.

## Ⅳ. 결 론

본 논문은 UR E26이 요구하는 실증의 범위를 조문 수준에서 정리하였다. 동 UR은 적용 범위를 OT 시스템 중심으로 정의하고 선내 IT 영역은 인터페이스로만 포함하므로, 그 안전성은 보안 구역 경계의 통제가 유효하다는 가정에 의존한다. 규정은 4.2.1.2에서 경계 우회가 언제나 가능함을 스스로 진술하면서도, 각 요구사항에 부속된 실증 요구는 승인 문서에 따른 적합성 확인과 가용성 시험에 머무른다. 공격자의 행위를 모사하는 항목은 서비스 거부 시험 2건이며, 승인된 경계를 우회할 수 있는지를 확인하는 항목은 본 논문이 검토한 범위에서 발견되지 않았다.

이로부터 적용 범위 밖 IT 영역의 관리 수준과 경계 우회를 다루는 시험의 수행 형태라는 두 지점에서 확인이 필요하다고 보았다. 이들은 조문이 아니라 실선과 시험 환경에서 확인되는 것이며, 이에 대한 연구가 필요하다. 강제 규정을 볼 때 요구사항의 문언과 함께 그에 부속된 실증 요구를 보는 관점이 유효할 수 있음을 UR E26을 대상으로 확인하였다.

본 논문은 조문에 기초하므로, 선급의 검사 실무가 이 지점들을 어느 정도 보완하는지와 동 UR 1.3.2가 대체 수용을 허용하는 IEC 61162-460 등 표준의 시험 요구가 이에 해당하는지는 확인하지 못하였다. 이에 대하여도 연구가 필요하다.

## References

[1] IACS, UR E26 Cyber resilience of ships, Rev.1, Nov. 2023.
[2] IACS, UR E27 Cyber resilience of on-board systems and equipment, Rev.1, Sep. 2023.
[3] 조용현, 차영균, "위협 모델링을 이용한 선박 사이버보안 요구사항 연구," 정보보호학회논문지, 제29권, 제3호, pp. 657-673, 2019.
[4] 김진, 이삼열, "선박의 사이버 복원력 통합 요구사항(IACS UR E26)과 기존 사이버보안 및 사이버 복원력 프레임워크의 비교," 정보보호학회논문지, 제34권, 제5호, pp. 1149-1159, 2024.
[5] 강남선, 손금준, 박래천, 이창식, 유성상, "국제선급협회 공통 규칙 - 선박의 사이버 복원력에 대한 기술적 분석," 한국항행학회논문지, 제28권, 제1호, pp. 27-36, 2024.
[6] G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," Turkish Journal of Maritime and Marine Sciences, vol. 10, Special Issue 1, pp. 31-50, 2024.
