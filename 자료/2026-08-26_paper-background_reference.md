# 배경지식 및 질의응답 대비 참고자료

작성: 2026-08-26
대상 원고: `outputs/2026-08-26_journal-paper_R5.md`(정식 논문, JKIICE 투고 예정), `conference/2026-08-24_conference-paper_draft.md`(학술대회 원고)

**이 문서의 목적** — 논문 본문에는 지면 제약과 서술 밀도 때문에 풀어 쓰지 못한 배경지식, 이 논문이 실제로 쓰고 있는 기술·개념·규정의 세부, 그리고 심사·발표에서 나올 법한 질문과 그에 대한 답변 방향을 한 곳에 모은다. **논문 본문이 아니다.** 본문의 표현·인용 규칙(evidence/assurance, isolated/physically segmented 등 영문 유지, UR을 "규칙"으로 부르지 않기 등)은 여기서는 적용하지 않고 이해를 돕는 쪽을 우선한다. 다만 사실관계는 본문·규정 원문과 어긋나지 않도록 검증했다.

**정확성 표기** — 아래에서도 본 프로젝트의 검증 규칙을 따른다. `[규정]` = 규정 원문에 직접 있는 내용, `[논문 내용]` = R5.md 본문에 있는 서술, `[추론]` = 해석, `[확인필요]` = 출처 미확보.

---

## 목차

1. 연구를 한 문단으로 — 무엇을, 왜
2. 규정 생태계 지도
3. 핵심 조문 원문 사전
4. 용어 사전
5. 선박 시스템·설비 배경지식
6. 통신 프로토콜 배경지식 (시리얼 vs IP)
7. 방법론 배경지식 (STRIDE, ATT&CK for ICS, kill-chain, 신뢰경계)
8. 이 논문이 쓰는 ATT&CK for ICS 기법 전체 목록
9. 논문 구조 지도 (R5.md 장절 요약)
10. R1~R11 잔여위협 매핑 요약표
11. 참고문헌 해제 — 각 인용이 무엇을 말하고 왜 쓰였는지
12. 의사결정 히스토리 타임라인
13. 예상 질문과 답변 (Q&A)
14. 프로젝트 파일 지도

---

## 1. 연구를 한 문단으로 — 무엇을, 왜

**연구 질문**: IACS UR E26에 근거해서 대상 CBS(컴퓨터기반시스템)를 제외시키는 것으로 충분할까?

**한 문장 답**: 충분하지 않다. UR E26은 요구사항 적용에서 벗어나는 두 가지 방식(6.4의 개별 CBS 제외, 1.3.2의 범위 정의 자체)을 두고 있는데, 둘 다 그로부터 남는 위협이 통제됨을 확인하는 절차가 불확정적이거나 아예 없다.

**진짜 논지(표면적 논지와 구분할 것)** — 표면적으로는 "기술적 취약점이 있다"는 논문처럼 보이지만, 실제 문제의식은 **"규정이 허술하면 선급마다 검사가 달라지고, 문서화 부담을 지는 업체·조선소는 어떻게든 제외시키려 한다"**는 것이다. "보안을 위한 게 아니라 요구조건만 충족하면 끝"이라는 관행이 만연해 있다는 것이 핵심 문제의식이며, 기술적 취약점 목록 자체는 목적이 아니라 그 문제의식을 뒷받침하는 증거다. 발표나 질의응답에서 "그래서 어떤 취약점을 찾았느냐"는 질문에만 답하면 이 논문의 핵심을 놓친 답변이 된다 — 항상 "제외/범위설정 판정 절차의 불확정성"으로 되돌아와야 한다.

**연구 로드맵**: 1단계(현재, 이 논문) 문헌·조문 기반 위협모델링, 실증 없음 → 2단계(후속 연구) testbed 구축·실증·방어 방법 연구. 2단계는 이 논문의 범위 밖이며, 본문에 "향후 연구" 절을 넣지 않기로 한 것은 저자 결정이다(가장 약한 장을 자인하는 모양이 되는 것을 피하기 위함).

**두 이탈 경로 — 절대 섞어 쓰면 안 되는 구분**:

| | 경로 A (6.4 제외) | 경로 B (1.3.2 범위 정의) |
|---|---|---|
| 작동 단위 | 개별 CBS | 영역(선내 IT 전체) |
| 판정 | 선급이 수용 여부를 판정 | 판정 행위 자체가 없음 |
| 문서화 | 6.1 위험평가, 5.1.4/Appendix I 제출·유지 | 없음 |
| 논문에서 | III장 3.1~3.3, IV장 4.2·4.5 | III장 3.4, IV장 4.3·4.4 |
| 잔여위협 번호 | R1~R10 | R11 |

---

## 2. 규정 생태계 지도

```
IMO 결의서 MSC.428(98) (2017)
  └─ "사이버 리스크를 ISM Code SMS에서 다루라"는 의무 부과 (강제, 그러나 방법은 지정 안 함)
       │
       ├─ IMO Guidelines MSC-FAL.1/Circ.3/Rev.2 (비강제 권고)
       ├─ BIMCO 등 5개 단체 공동, The Guidelines on Cyber Security Onboard Ships (비강제, 업계 자율지침)
       │
       └─ IACS(국제선급연합회, 각국 선급협회의 연합체)가 강제 기술기준으로 구체화
            │
            ├─ UR E22 — Computer Based Systems (CBS 일반 요구사항 + Category 정의)
            │     "이 UR의 요구사항이 적용되는 CBS"의 범위와 등급(고장 결과 기준)을 정의
            │
            ├─ UR E26 — Cyber resilience of ships (선박 수준 복원력) ← 이 논문의 주 대상
            │     식별·보호·탐지·대응·복구 5대 기능요소, 전 생애주기 문서제출·실증 요구
            │     Rev.1(2023.11)이 2024.7.1 이후 건조계약 선박에 강제 적용
            │     └─ 초판(2022.4)은 발효(2024.1.1) 전 철회됨 — 시행된 적 없음, "완화"라고 쓰면 안 됨
            │
            ├─ UR E27 — Cyber resilience of on-board systems and equipment (장비 수준 보안능력)
            │     적용대상 = "UR E26에 명시된 CBS" → E26에서 제외되면 E27 요구도 함께 벗어남
            │
            └─ 비강제 권고(Recommendation) — UR보다 하위, 상충 시 UR 우선(1.3.4)
                  ├─ Rec.166 — Cyber Resilience 일반 권고 (기능 요구, 전이 억제 등)
                  ├─ Rec.171 — 위험평가 방법론 (BIMCO와 공동, 정성적)
                  └─ Rec.190 — Vessel Asset Inventory 권고 (자산 목록에 무엇을 담을지, 제외 CBS 표기 "recommended")

병행 규격 (강제/보안 요구는 add-on):
  IEC 61162-450/460 — 선박 데이터 네트워크(NMEA 기반) 표준. 보안 요구는 기본 규격이 아니라
                       -460이라는 별도 add-on 표준에만 있음 ("higher safety and security
                       standards are needed"일 때 선택 적용)

법정 요건과의 관계:
  UR E22 1.2 — "법정 규정이 적용되는 CBS는 이 UR의 요구에서 제외된다" (예: SOLAS 제V·IV장의
               항해·무선통신 시스템). 그런데 UR E26 1.3.2는 바로 이 법정 시스템들을 자신의
               적용범위에 다시 포함시킨다 → 이 시스템들은 E26 대상이면서 E22 Category 체계
               밖에 있는 특이 위치에 놓인다 (본 논문 4.5의 핵심 논거 중 하나)
```

**왜 이 지도가 필요한가**: 질문에서 "Rec.166은 왜 안 썼냐" "BIMCO 지침은 뭐냐" "MASS Code는 어디 갔냐" 같은 게 나올 수 있다. 답변 원칙 — 강제 문서(UR)와 비강제 권고(Rec.)는 규범적 무게가 다르고, 1.3.4가 상충 시 UR 우선을 명시하므로, 본 논문의 핵심 주장은 강제 문서(UR E26 6.4, 1.3.2)에만 둔다. 비강제 권고는 "요구가 이 형태로 존재할 수 있다"는 보조 근거로만 쓴다.

---

## 3. 핵심 조문 원문 사전

빠른 참조용. 논문에서 반복 인용되는 조문을 원문 그대로 모았다.

### UR E26 6장 (제외)

**6.1** (요지): 적용 대상 CBS를 요구사항 적용에서 제외하려면 위험평가를 수행하고 위험수준이 수용 가능함을 입증하는 자료를 제시해야 한다.

**6.4 두문**: "...only if **assurance** is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk."

**6.4 필수 기준(shall be met)**:
- a) "The CBS shall be **isolated** (**i.e., have no IP-network connections** to other systems or networks)"
- b) "The CBS shall have no accessible physical interface ports. Unused interfaces shall be logically disabled. It shall not be possible to connect unauthorised devices to the CBS."
- c) "The CBS must be located in areas to which physical access is controlled."
- d) "The CBS shall not be an integrated control system serving multiple ship functions as specified in the scope of applicability of this UR (see section 1.3)"

**6.4 추가 기준(should be considered, "Additional Criteria")**:
- a) "The CBS should not serve ship functions of category III."
- b) "Known vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment."
- c) "The attack surface for the CBS is minimized, having considered its complexity, connectivity, physical and logical access points, including wireless access points."

**6.4 재량 조항**: 추가 기준을 완전히 충족하지 못해도 "provided with a rational explanation together with evidence and is found satisfactory by the Classification Society"이면 제외를 수용할 수 있다.

**6.3**: 위험평가의 고려 요소로 "Possible effects related to integration of systems, or interfaces among systems, including systems not onboard"를 요구. (이 문구는 초판·Rev.1에 동일하게 존재 — "전이 검증 절차가 없다"고 쓰면 안 되는 이유)

### UR E26 1.3 (적용 범위)

**1.3.2 a)**: 추진·조타·계류·발전 및 배전·화재탐지 등 OT 시스템과 법정 요건이 요구하는 항해·통신 시스템을 적용 대상으로 열거.

**1.3.2 b)**: "Any Internet Protocol (IP)-based communication interface **from CBSs in scope of this UR to other systems**" — 인터페이스가 향하는 상대편으로 여객 서비스 시스템, 여객용 네트워크, 관리 네트워크, 승무원 복지 시스템, 그리고 "any other systems connected to OT systems, either permanently or temporarily (e.g. during maintenance)".

**1.3.3**: "System categories are defined in IACS UR E22 **on the basis of the consequences of a system failure** to human safety, safety of the vessel and/or threat to the environment." (Category가 안전/고장 척도이지 공격 척도가 아니라는 근거)

### UR E26 4장 (보안 구역·경계·이행실증)

**4.2.1.1**: "Security zones shall either be **isolated (i.e. air gapped)** or connected to other security zones or networks..." 경계 수단 예시로 "firewalls/routers, **simplex serial links**, TCP/IP diodes, dry contacts"를 명시.

**4.2.1.2** (표제 Rationale): "While networks may be protected by firewall perimeter and include Intrusion Detection Systems (IDS) or Intrusion Prevention Systems (IPS) to monitor traffic coming in, **breaching that perimeter is always possible**."

**4.2.1.3**: 적용 범위 밖의 시스템·네트워크·CBS를 비신뢰 네트워크로 간주하고 보안 구역으로부터의 물리적 분할("physically segmented")을 요구. 곧바로 단서: "**Alternatively, it is accepted that such systems are part of a security zone if these OT-systems meet the same requirements as demanded by the zone.**" (이 단서를 자르고 인용하면 안 됨 — 본 논문 3.3·4.5의 순환논증 지적이 여기서 나옴)

**4.2.1.4.1**: Zones and conduit diagram과 Cyber security design description이 비신뢰 네트워크와의 통신 기술을 "**discrete signals, serial communication**"까지 포함하도록 강제.

**4.2.2.4** (경계 보호 이행실증): 4.2.2.4.1(설계)·4.2.2.4.2(건조) 모두 "No requirements". 4.2.2.4.3(시운전)에서만 세 가지 — ① 구역 경계 보호장치 대상 서비스거부 시험, ② 각 네트워크 세그먼트 내부 발신 과도 트래픽에 대한 서비스거부 시험, ③ 불필요한 기능·포트·프로토콜·서비스 제거 여부를 분석적 평가+포트스캔으로 확인. **경계가 우회될 수 있는지 자체를 확인하는 시험은 없음.**

**4.3.1.3**: 감시 능력 목록 — 과다 트래픽 감시·보호, 네트워크 연결 감시, 기기 관리 활동 감시·기록, 미승인 기기 접속 보호, 대역폭 임계 초과 경보. **전부 패킷 네트워크를 전제** — 시리얼 링크 감시는 다루지 않음.

**5.1.4 / Appendix I**: "Risk assessment for the exclusion of CBSs"를 제출 문서로 규정, Appendix I은 이를 설계승인 이후 연차·정기검사 단계까지 유지(Maintain)하도록 요구.

### UR E22 (Category 관련)

**1.2**: "Computer-based systems that are covered by statutory regulations are excluded from the requirements of this UR." (Guidance 예시: SOLAS 제V·IV장 항해·무선통신 시스템)

**3.2**: Category I 시스템은 통상 선급 검증 대상이 아니지만, 정보가 "shall be required **upon request** to determine the correct category or ensure that they do not influence the operation of systems in category II and category III."

**4.3.3 / 4.3.4**: 시스템별 범주 결정 요구(4.3.3, upon request 제출), 범주 결정을 위한 위험평가(4.3.4, 선급 요구 시). 둘 다 **조건부 절차**이며 고장 영향 기준이지 사이버 사고 전이 기준이 아님.

### 초판(Apr 2022) 관련 — Rev.1과 다른 부분만

- 초판 6.4는 a)~l) **12개 항목**, 전부 "shall be considered"(재량)
- 초판 c): "The CBS, considered in its function and role in the integrated system it is part of, **cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices**" → **Rev.1에 미반영** (전이 관련 판정 기준 소멸의 핵심 증거)
- 초판 f) 앞 문장: "**The connections of CBS to other CBSs have been duly investigated, understood and documented.**" → Rev.1 필수 a)는 이 문장의 뒷부분(IP 연결 부재)만 승계, 앞 문장(연결관계 조사·문서화)은 미반영
- 초판 d): "must not serve **essential services or multiple ship services**" → Rev.1 필수 d): "**an integrated control system serving multiple ship functions**"로 축소(단일 필수용도 CBS도 제외 후보가 됨)
- 초판 6.4 두문: "only if **evidence** is given" → Rev.1: "**assurance**"(입증 수준의 미묘한 하향)
- 초판 6.1·6.3: 제외 목록의 선내 유지 요구, 선급의 수락·거부 권한 명문 → **미반영**

---

## 4. 용어 사전

| 용어 | 뜻 |
|---|---|
| CBS | Computer Based System, 컴퓨터기반시스템 |
| UR | Unified Requirement, IACS의 통합규정(강제). "규칙"으로 부르지 않는다 — 선급규칙·IMO 규칙과 혼동됨 |
| IACS | International Association of Classification Societies, 국제선급연합회(각국 선급협회들의 연합체) |
| 선급 (Classification Society) | 선박의 설계·건조·운항이 규정을 충족하는지 심사·인증하는 기관(KR, ABS, DNV, LR 등) |
| Category I/II/III | UR E22가 정의하는 CBS 등급. **고장(failure)의 안전 결과** 기준(인명·선박·환경 위협 정도)이며 공격자를 상정하지 않음. I(낮음)~III(높음, 필수 기능) |
| Critical Criteria | 본 논문이 6.4의 "shall be met" 기준 4개(필수 a~d)를 부르는 이름(원문에는 이 명칭이 없음, 논문 편의상 명명) |
| Additional Criteria | 6.4의 "should be considered" 기준 3개(추가 a~c). 원문 명칭 그대로 |
| isolated | **규칙 안에서 정의가 둘이다.** 6.4 a)는 "IP-network connections 없음"으로, 4.2.1.1은 "air gapped"로 정의 — 두 정의 사이에 시리얼 전용 CBS가 놓인다 |
| physically segmented | 4.2.1.3의 요구 문구. "물리적 분할" — isolated와 다른 개념이므로 번역 시 구분 유지 |
| assurance / evidence | 6.4 두문의 입증 수준을 가리키는 두 단어. Rev.1은 evidence(초판)에서 assurance로 바꿈. 번역하면 이 차이가 사라짐 |
| ICMS | Integrated Control and Monitoring System, 통합제어감시시스템. 선내 여러 OT 기능(항해·기관·화재탐지 등)을 하나의 백본으로 묶는 시스템 |
| IBS | Integrated Bridge System, 통합선교시스템 |
| MASS | Maritime Autonomous Surface Ship, 자율운항선박. IMO가 별도 MASS Code를 개발 중. 이 논문의 로드맵 2단계·박사후속연구 대상이며 현재 논문 본문에서는 자율운항 구성의 "영향 확대" 맥락에서만 짧게 언급 |
| RCC | Remote Control Centre, 육상 원격운용센터(MASS 관련 개념) |
| ISM Code | International Safety Management Code, IMO의 안전관리 규정. MSC.428(98)가 사이버리스크를 이 틀 안에서 다루도록 요구 |
| NMEA 0183 | 선박용 데이터 프로토콜(계측기↔항해장비 통신에 널리 쓰임). ASCII 문장 기반 시리얼 통신 |
| talker / listener | NMEA/IEC 61162-1의 역할 구분. talker=회선을 구동하며 데이터를 송출하는 기기(계측기), listener=수신만 하는 기기. simplex 구조에서 listener는 회선을 구동할 수 없음 |
| STRIDE | Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege — Microsoft가 제안한 위협분류 프레임워크 |
| STRIDE-per-interaction | 시스템 전체가 아니라 **개별 인터페이스(신뢰경계를 넘는 지점) 단위로** STRIDE를 적용하는 방식. 본 논문의 방법론 |
| ATT&CK for ICS | MITRE의 산업제어시스템(ICS) 대상 공격기법 매트릭스. Tactic(전술, 예: Initial Access)과 Technique(기법, 예: T0819)의 2계층 구조 |
| Kill-chain | 공격이 초기접근→내부이동→목표달성으로 이어지는 단계적 사슬 모델 |
| 신뢰경계 (Trust boundary) | 서로 다른 신뢰수준(권한·검증수준)을 가진 두 영역의 경계. 본 논문은 "E26 4장 요구사항이 적용되는 CBS/시스템" vs "그렇지 않은 CBS/영역"으로 정의 |
| DFA | Data Flow Analysis, 데이터 흐름 분석. **2nd_research(paper2_threat-modeling)에서 쓰는 개념이며 이 논문(R5)에서는 사용하지 않는다** — 혼동 주의. R5의 방법론은 STRIDE-per-interaction + ATT&CK for ICS이지 DFA가 아니다 |
| VSAT | Very Small Aperture Terminal, 선박의 위성통신 단말 |
| ECDIS | Electronic Chart Display and Information System, 전자해도표시시스템 |
| ARPA | Automatic Radar Plotting Aid, 자동레이더플로팅장치(타선 진침로·진속력 산출) |
| NFU | Non-Follow-Up, 조타장치의 수동 대체 조작 모드(자동조타 계통과 물리적으로 분리된 백업 경로) |
| 트립 인터록 (trip interlock) | 기관 등에서 위험 상태 시 하드와이어드로 강제 정지시키는 안전장치 |

---

## 5. 선박 시스템·설비 배경지식

### 5.1 선내망의 전형적 구성 (본 논문 4.1이 상정하는 아키텍처)

`experiment/기본 아키텍쳐.drawio`에 기반한 구성:

- **IP 기반 LAN (선내 업무망)**: 선내 업무용 PC, CCTV, 승무원 복지용 네트워크, 스마트십 솔루션(원격 모니터링·최적화 서비스 등). VSAT(위성통신)나 무선망을 통해 육상과 상시 연결 — **이 영역이 경로 B(1.3.2)의 대상**
- **경계 (방화벽)**: 두 세그먼트 사이에 위치. 4.2.1.1이 예시하는 firewalls/routers/simplex serial links/TCP-IP diodes/dry contacts 중 하나
- **시리얼 기반 OT 세그먼트**: ICMS 하위에 항해(Navigation System), 제어(Control System), 안전(Safety System), 기관(M/E 주기관, G/E 발전기), 화재탐지(FDS), 화물(Cargo System) 등이 물림 — **이 영역이 경로 A(6.4)의 무대**

### 5.2 선교 계측기 (4.5 대비 사례의 주인공)

- **음향측심기(echo sounder)**: 수심을 측정해 ECDIS의 좌초 회피 기능·천수 경보에 입력
- **선속계(speed log)**: 대수속력(water-referenced speed)을 측정해 ECDIS 표시뿐 아니라 **레이더·ARPA의 sea-stabilized 연산**(타선의 진침로·진속력 산출)에도 입력됨. 이 값이 변조되면 최근접점(CPA)·최근접시간(TCPA) 판단이 왜곡되어 충돌회피 판단 자체가 오염됨
- **풍향풍속계**: 유사한 talker 계측기(논문 초안 단계에서 언급되었으나 이후 미등장 — round-03 리뷰에서 지적된 정리 대상)
- 실선 계측기는 순수 talker인 경우가 드물고, 시각동기·위치문장 **수신** 포트나 설정·교정용 **양방향 서비스 포트**를 함께 갖는 것이 일반적 — 이 역방향 경로가 4.5의 초기 접근 논거

### 5.3 제어 계통 (4.4 심층 시나리오의 표적)

- **자동조타장치(autopilot)**: 침로 유지를 자동 제어. 법정 백업으로 수동/NFU 전환 경로 존재
- **주기관 원격제어(main engine remote control)**: 기관 출력을 원격 제어. 백업으로 기관실 국소 제어반, 하드와이어드 트립 인터록 존재
- 두 계통은 통상 **서로 다른 보안 구역**에 속하므로, 공격자가 둘 다에 도달하려면 원칙적으로 서로 다른 두 차례 이상의 경계 통과가 필요 — 본 논문 4.4는 **ICMS/IBS와 같은 공통 백본**이 있는 구성을 전제로 하나의 경계 통과로 양쪽에 이르는 시나리오를 상정하며, 그런 통합이 없으면 난이도가 올라간다는 점을 명시함

---

## 6. 통신 프로토콜 배경지식 (시리얼 vs IP)

### 6.1 IEC 61162-1과 NMEA 0183

- 선박 항해장비 간 통신 표준. **단방향(simplex) single-talker/multiple-listener** 구조 — 한 기기(talker)가 회선을 구동하고 여러 listener가 수신만 함
- 문장(sentence)에 체크섬과 유효성 플래그가 있어 **전송 오류·기기 고장은 검출**되지만, 문장 출처를 **암호학적으로 인증하는 수단은 없음** — "수신 측이 검증을 전혀 안 한다"는 서술은 틀렸고, 정확히는 "암호학적 출처 인증이 없다"

### 6.2 IEC 61162-450/460

- 61162-450: 선박 데이터 네트워크의 **기본** 규격
- 61162-460: 위 규격에 대한 **add-on 보안 표준**. 스스로를 "an add-on to IEC 61162-450 where higher safety and security standards are needed"로 정의 — **보안이 기본 내장이 아니라 선택적 추가 계층**이라는 점이 핵심
- UR E26 1.3.2는 법정 항해·통신 시스템에 대해 IEC 61162-460(또는 동등 표준)을 UR E27 4장 요구 대신 수용 가능하게 하되 "on the condition that requirements in UR E26 are complied with"라는 단서를 둠

### 6.3 시리얼-IP 변환장치 (Serial-to-IP converter)

- RS-232/422/485 등 시리얼 신호를 TCP/IP 패킷으로(또는 역방향으로) 변환하는 장치. 선내에서 레거시 시리얼 장비를 IP 네트워크에 연결할 때 흔히 쓰임
- 이 장치의 취약점이 뚫리면 시리얼 구간(격리로 간주되던 영역)이 IP 영역과 사실상 연결됨 — 4.5·4.1 논증의 핵심 소재
- 관련 문헌: [17] 장지웅·김휘강(DNP3 시리얼, 육상 전력망 사례), [19] Forescout(선박용 변환장치 직접 언급), [20] Munro(2018, 선박 시리얼망 해킹 시연), [25] Hui et al.(S7 PLC)

### 6.4 시리얼 vs IP의 규정상 취급 차이 (핵심 논지 중 하나)

- **6.4 필수 a)는 "IP-network connections"만 본다** — 시리얼 연결은 판정 대상이 아님
- 그런데 **4.2.1.1은 같은 규칙 안에서 simplex serial links를 zone 간 통제 수단(conduit)으로 명시 허용**하고, **4.2.1.4.1은 discrete signals·serial communication을 기술서에 포함하도록 요구** — 규정은 시리얼의 존재를 인지하면서도 제외 판정 단계에서는 IP만 본다는 비일관성이 R1의 핵심 근거
- **4.3.1.3의 감시 능력 목록은 전부 패킷 네트워크 전제** — 시리얼 구간 자체는 감시 요구의 사각지대(제외 여부와 무관하게 존재하는 별도 공백)

---

## 7. 방법론 배경지식

### 7.1 STRIDE와 STRIDE-per-interaction

- **STRIDE**: Microsoft가 제안한 위협 분류 6범주 — Spoofing(위장), Tampering(변조), Repudiation(부인), Information disclosure(정보노출), Denial of service(서비스거부), Elevation of privilege(권한상승)
- 통상은 시스템 전체의 데이터흐름도(DFD)에 대해 적용(예: [1] 조용현·차영균이 206건 도출)
- **본 논문의 STRIDE-per-interaction**: 시스템 전체가 아니라 **신뢰경계를 넘나드는 개별 인터페이스**(시리얼 문장, 물리 포트, 원격 접속, IP 인터페이스) 단위로 "무엇이 가능한가"를 도출. 규정이 통과시키는 CBS/영역의 성질로부터 연역하므로 그 자체로는 발생 여부를 주장하지 않음 — **가능성 도출 단계**

### 7.2 MITRE ATT&CK for ICS

- 산업제어시스템(ICS) 환경에서 실제 관측되거나 검증된 공격 기법을 정리한 매트릭스(MITRE 운영, 육상 ICS 사고 사례에서 축적)
- **Tactic**(전술, 상위 목적. 예: Initial Access, Lateral Movement, Impair Process Control) 아래 **Technique**(구체적 기법, T-번호)가 있고, 하위 세분화는 T####.### 형태(sub-technique)
- 본 논문은 STRIDE 단계의 산출 중 **대응하는 ATT&CK 기법이나 선행 사례가 있는 것만** 남기고 나머지는 사변으로 배제 — **관측 여부 검증 단계**. 이 2단 결합(가능성→관측여부)이 방법론의 핵심이며, 단독 STRIDE나 단독 ATT&CK 매핑은 이미 선행연구([1],[9])가 했으므로 이 결합 자체는 신규성의 근거가 아니라 **적용 대상**(규정이 비운 자리)이 신규성의 근거임을 항상 함께 말해야 함

### 7.3 신뢰경계의 정의 (이 논문 고유)

- 선행연구는 대체로 "육상-선박" 또는 "선박-외부"를 신뢰경계로 삼음([1],[9])
- 본 논문은 **"UR E26 4장 요구사항이 적용되는 CBS" vs "그렇지 않은 CBS/영역"**을 신뢰경계로 삼음. 후자는 다시 경로 A(제외된 CBS)와 경로 B(범위 정의로 애초에 빠진 IT 영역) 둘로 나뉨

### 7.4 잔여 위협(residual threat)의 조작적 정의

두 조건 중 하나:
(a) **경로 A**: 6.4의 필수 기준 4개와 추가 기준 3개를 **모두 충족한 상태에서도** 성립하는 위협 (어느 하나라도 미충족이면 제외 자체가 성립하지 않으므로 분석대상 아님)
(b) **경로 B**: 1.3.2가 정의하는 범위 밖 IT 영역, 즉 판정 자체가 없는 영역에서 성립하는 위협

### 7.5 이 논문이 명시적으로 다루지 않는 것 (범위 경계)

- IMO FSA 방식의 **정량적 위험도 산정**(SI/FI 등)
- 기존에 설치된 **방벽의 목록화·분석**
- **완화 방안(mitigation)**의 구체적 제시
- **실선 환경에서의 실증**(2단계 testbed 몫)
- **AI 적대자 증폭·DFA**(2nd_research paper2의 별개 RQ — AI가 공격을 어떻게 자동화·정교화하는지는 이 논문의 범위 밖)
- 특정 선박에서 경계 통과가 **어떤 조건으로 성립하는지**(문헌에 보고된 경로임을 보이는 데까지가 범위)

---

## 8. 이 논문이 쓰는 ATT&CK for ICS 기법 전체 목록

용도별로 묶었다. Tactic 분류는 개략적 참고용이다.

**초기 접근(Initial Access) 계열**
- **T0819 Exploit Public-Facing Application** — 외부에 노출된 애플리케이션의 취약점 이용 (4.4: 위성단말 웹 인터페이스 등)
- **T0822 External Remote Services** — 외부 원격접속 서비스(VPN 등) 경유 (4.4)
- **T0862 Supply Chain Compromise** — 공급망(벤더 장비·소프트웨어) 경유 침해 (4.2 R3/R7, 4.5)
- **T0864 Transient Cyber Asset** — 일시적으로 연결되는 자산(정비용 노트북 등) 이용 (4.2 R2/R4, 4.5 — round-03 리뷰 반영으로 T0847 대신 채택)

**측면 이동·원격 서비스 악용(Lateral Movement) 계열**
- **T0866 Exploitation of Remote Services** — 원격 서비스의 취약점을 이용한 이동 (4.3 R11, 4.4)
- **T0886 Remote Services** — 정상 원격 서비스 경로를 이용한 이동 (4.3 R11, 4.4)
- **T0867 Lateral Tool Transfer** — 도구를 다른 시스템으로 이전 (4.2 R6)
- **T0859 Valid Accounts** — 정상 계정 탈취·사용 (4.2 R6, 4.3 R11)

**수집·도청(Collection/Discovery) 계열**
- **T0842 Network Sniffing** — 네트워크 트래픽 도청 (4.2 R1)
- **T0887 Wireless Sniffing** — 무선 트래픽 도청 (4.2 R2)
- **T0830 Adversary-in-the-Middle (AiTM)** — 중간자 위치에서 트래픽 가로채기·조작 (4.2 R1, 4.5)

**메시지 위조·변조(Command and Control / Impair Process Control) 계열**
- **T1692.001 Unauthorized Message: Command Message** — 정규 형식의 제어 명령 위조 발행 (4.4, 최종 제어개입 단계)
- **T1692.002 Unauthorized Message: Reporting Message** — 정규 형식의 보고/측정값 문장 위조 (4.2 R1, 4.5 회선조작 단계)
- **T1695.001 Block Communications: Serial COM** — 시리얼 통신 차단(회선 절단 등과 결합) (4.2 R1 대안, 4.5)
- **T1693 Modify Firmware** — 펌웨어 변조(비활성화된 인터페이스의 논리적 복구 등) (4.2 R3)

**접근·이동식 매체 계열**
- **T0847 Replication Through Removable Media** — 이동식 매체(USB 등)를 통한 침투/복제 (4.2 R2 — 4.2 R4에서는 round-03 지적 이후 이 위치 유지, 단 4.5 초기접근에서는 T0864로 교체됨. 이동식 매체 슬롯이 실제로 있는 경로에만 한정해서 쓴다는 점 주의)
- **T0860 Wireless Compromise** — 무선 경로 침해 (4.2 R2)

**영향(Impact) 계열**
- **T0829 Loss of View** — 상황 인식 상실 (4.2 R5)
- **T0832 Manipulation of View** — 표시값 조작으로 상황 인식 왜곡 (4.2 R5, 4.5 전이 단계)
- **T0882 Theft of Operational Information** — 운영 정보 탈취 (4.2 R5)
- **T0831 Manipulation of Control** — 제어 자체의 조작 (4.4 제어개입 단계)
- **T0880 Loss of Safety** — 안전 기능 상실(자동 제어 기능 상실, "조종 불능"이 아님에 주의 — 4.4는 이를 명확히 "자동 제어 기능의 상실"로 하향해서 씀) (4.4)
- **T0872 Indicator Removal on Host** — 침해 흔적 제거 (4.2 R9)
- **T0878 Alarm Suppression** — 경보 억제 (4.2 R9)

**주의할 매핑 이슈(round-03 리뷰에서 지적됨, R5에서 수정)**:
- ~~T0847을 계측기 서비스포트 접근(정비 인력의 노트북 연결)에 매핑한 것~~ → **부정합**. T0847은 이동식 매체(USB 등) 슬롯을 전제하는데 서비스포트 접근은 그와 다름 → **T0864 Transient Cyber Asset로 교체 완료**
- T08xx 계열(구형 ATT&CK for ICS 번호 체계)과 T1692.xxx/T1695.xxx/T1693(신형, sub-technique 포함 번호 체계)이 혼재되어 있음 — 이는 실제 MITRE ATT&CK for ICS v19.2 매트릭스 자체의 번호 체계 변천을 반영한 것이며 오류가 아니다. 다만 질문이 나오면 "매트릭스 개정에 따라 두 세대의 ID 체계가 공존한다"고 설명할 것

---

## 9. 논문 구조 지도 (R5.md 장절 요약)

| 장 | 절 | 핵심 내용 |
|---|---|---|
| 요약/ABSTRACT | | 국/영문 초록. RQ→두 경로 분석→체계적 도출(R1~R10, R11)→두 심층 경로→차이 |
| Ⅰ. 서론 | | 배경(연결성→전이 가능성)→제도적 대응 연혁(BIMCO/IMO/IACS)→UR 체계 소개→두 이탈 방식 제시→RQ→장 구성 |
| Ⅱ. 관련 연구 | | 선박 위협모델링 선행연구([1],[9]) + E26 자체 연구([10]~[13]) 정리 → 갭: "무엇이 적용대상에서 빠지는가"를 다룬 연구 없음 |
| Ⅲ. 제외 규정과 범위 정의 분석 | 3.1 | 6.4 필수/추가 기준, 판정 불확정성(3가지 재량요소), isolated의 이중정의, 문언기준/경로기준 미결정 |
| | 3.2 | 제외의 실질적 효과 — 4장 17개 요구사항 전체 면제, 감시공백(4.3.1.3은 패킷망 전제) |
| | 3.3 | 초판-Rev.1 조문 대조(표2), 전이 관련 판정기준 소멸, 잔존 5개 조항이 대신하지 못하는 이유(표3), Rec.166 검토 |
| | 3.4 | 1.3.2 범위정의(경로 B), 경계방어 위임, 4.2.1.2 자기진술, 이행실증 공백(표4) |
| Ⅳ. 잔여 위협의 체계적 모델링 | 4.1 | 신뢰경계 정의 + STRIDE-per-interaction/ATT&CK for ICS 방법론 + 잔여위협 조작적 정의 |
| | 4.2 | 경로 A 잔여위협 R1~R10 매핑표(표5) |
| | 4.3 | 경로 B 잔여위협 R11 매핑표(표6) |
| | 4.4 | 심층 시나리오 — IT→경계통과→OT 제어(주축, kill-chain, 표7) |
| | 4.5 | 대비 사례 — 제외된 계측기 경로(축소, kill-chain, 표8) |
| Ⅴ. 결론 | | RQ에 대한 답(불충분) 재확인 → 체계적 도출 결과 요약 → 두 경로 차이(성립조건 폭) → 기여 2가지 → 제언(전이 판정항목 복원, 판정경계 명시, 경계통제 유효성 확인절차) → 범위 한계 |

---

## 10. R1~R11 잔여위협 매핑 요약표

원 출처: `llm_wiki/2026-08-13_e26-exclusion-residual-threat_mapping.md` (본 논문 IV장 표5·표6의 기반)

| # | 경로 | 통과되는 기준 | 잔여 위협 한 줄 요약 | 근거 상태 |
|---|---|---|---|---|
| R1 | A | 필수 a) | 시리얼 연결은 IP가 아니므로 제한 안 됨 → 물리접속만으로 문장 변조 가능 | 문헌 확보([17],[23],[24]) |
| R2 | A | 필수 a) | 격리 정의가 IP 한정 → USB/무선/위성백채널 등 비IP 경로 전체가 사각 | 문헌 확보([21],[25]) |
| R3 | A | 필수 b) | "accessible"·"logically disabled" 판정기준 부재 → 디버그 포트, 펌웨어 레벨 복구 가능 | 문헌 확보([29]) |
| R4 | A | 필수 c) | 구역지정 근거·검증방법 없음 → 정박 중 상시출입 인력 | **[확인필요]** — 항만 정박 중 승선인원 통계 미확보 |
| R5 | A | 필수 d) | 다기능 통합시스템만 배제 → 단일기능 CBS도 상위시스템에 데이터 중계 시 무결성 원천 | 문헌 확보([19],[26]) |
| R6 | A | 추가 a) | Category는 고장기준, 공격기준 아님 → Cat I→Cat II/III 피벗 가능, 전이검증 없음 | 문헌 확보([21],[27]) |
| R7 | A | 추가 b) | "Known"으로 한정 → 미공개·독자 프로토콜 취약점 배제 | 문헌 확보([29], R3와 공유) |
| R8 | A | 추가 c) | 공격면 최소화에 정량기준 없음 | **[확인필요]** — 1차자료 미확보. rules/의 관련 자료는 업체 해설본이라 인용 금지 |
| R9 | A | 전체 | 제외 CBS는 자산목록·감시·IR계획에서 함께 배제 → 탐지·대응 불가 | 문헌 확보([28]) |
| R10 | A | 전체 | 6.4는 개별 CBS 단위 심사만 → 다수 CBS 누적 시 결합 공격면 미평가 | **[추론]** — 선행문헌 미확인 |
| R11 | B | 1.3.2 b) | IT는 시스템 아닌 인터페이스로만 범위 진입 → 방어가 경계(4.2.1.1/.3)에 위임, 경계돌파 가능성 인정하면서도 이행실증은 DoS+포트스캔뿐 | 문헌 확보([19],[20],[21],[27]) |

**질문 대비 메모**: R4·R8·R10은 "지어내지 않고 정직하게 확인필요로 남긴" 항목이다. 리뷰나 발표에서 "이 세 항목은 왜 근거가 약하냐"는 질문이 나오면 회피하지 말고 "1차 문헌을 확보하지 못해 확인필요로 표기했고, 이는 후속 검토 대상"이라고 정직하게 답한다 — 이것이 이 프로젝트의 검증 규칙이다.

---

## 11. 참고문헌 해제 — 각 인용이 무엇을 말하고 왜 쓰였는지

| # | 문헌 | 무엇을 말하는가 | 이 논문에서의 쓰임 | 한계/주의 |
|---|---|---|---|---|
| [1] | 조용현·차영균, 2019 | IEC 61162-450/460 기기목록에서 대상 선정, DFD 수립, STRIDE+Attack Tree로 206건 위협 도출 | II장 선행연구, 신뢰경계 비교 대상(4.1) | 선박 시스템 일반을 다룸 — "규정이 비운 자리"는 다루지 않음(본 논문과의 차별점) |
| [9] | Jo et al., Sensors 2022 | MITRE ATT&CK을 선박 장비에 적용한 공격모델 | II장, 4.1 방법론 비교 대상 | 동일 — ATT&CK 매핑 자체는 선행연구가 이미 함 |
| [10] | 김진·이삼열, 2024 | UR E26을 NIST CSF·사이버복원력 체계와 비교 | II장 | 준수 관점, 제외/범위이탈은 안 다룸 |
| [11] | 손금준 외, 2024 | UR E26+IEC 62443 고려 선박 네트워크 토폴로지 설계 | II장 | 동일 |
| [12] | 강남선 외, 2024 | UR E26 요구조건·제출문서 정리, 전주기 대응기술 제안 | II장 | 제외를 "제출문서의 하나"로만 언급 |
| [13] | Kayışoğlu et al., 2024 | UR E26 요구사항→선박 OT 점검항목 변환 체크리스트 | II장 | 제외를 "부속 절차"로만 소개 |
| [17] | 장지웅·김휘강, 2013 | 시리얼 기반 DNP3.0 통신의 "내재적 보안성" 통념을 탭핑 실험으로 반박(C/I/A 전부 취약) | 4.5(시리얼 통념 반박), R1 근거 | **대상이 육상 전력망**이므로 "선행 사례"로만 인용, 선박 실증 아님 |
| [18] | IEC 61162-460, 2024 | 61162-450의 보안 add-on 표준. 스스로를 add-on으로 정의 | 4.5 | — |
| [19] | Forescout, 2026 | 시리얼-IP 변환장치 3개 제품(Lantronix EDS3000PS/EDS5000, Silex SD330-AC) 분석, 신규 취약점 20건(8+12), "Critical shipboard systems...propulsion and steering...ECDIS" 명시. 자체 타임라인에 "2018 Munro가 선박망 해킹 시연"도 기록 | 4.1(3개 제품/20건 언급), 4.4(초기접근 VPN/워크스테이션 사례) | **직접 검증 완료** — 로컬 PDF 전문 대조로 "3개 제품군/20건" 수치가 원문과 정확히 일치함을 확인(round-03 리뷰의 "2벤더/22건" 지적은 press release 반올림으로 보이며 원본 기준 논문이 맞음) |
| [20] | Munro, 2018, Pen Test Partners 블로그 | 시리얼-IP 변환장치로 선내망 침해 시연 | 4.4 경계통과 사례 | 벤더/보안업체 블로그(회색문헌) — "시연된 바 있다"까지만 주장, "실증하였다"로 승격 안 함 |
| [21] | TRITON, Black Hat 2018 | 페트로케미컬 플랜트에서 IT 침투→양쪽 접근 가능 시스템 경유→OT 이동→엔지니어링 워크스테이션 감염→SIS 컨트롤러 도달 사례(Triconex) | 4.4 경계통과 사례, R6/R2 근거 | **직접 검증 완료** — 로컬 PDF 전문(6,264단어) 검색 결과 ship/vessel/maritime/converter 언급 전무. 선박 관련 주장의 근거로 쓰지 않는다(R4-short 시절 이 문헌에 선박 서술을 잘못 귀속시킨 오류가 있었으나 R4/R5는 이미 [20]으로 정확히 분리되어 있음) |
| [22] | CVE-2023-44857 | 위성통신 단말 웹 관리 구성요소의 원격코드실행 취약점(CVSS 8.1) | 4.4 초기접근 | 인증을 전제하므로 그 자체로 경계를 열지는 않음 — "공격표면이 존재한다"까지만 주장 |
| [23] | 홍봉조 외, 2018 | RS-485 통신보안 실증연구 | 4.2 R1 근거 | 신규 추가(2026-08-26) |
| [24] | 최동준·이재우, 2020 | 제어네트워크 프로토콜 보안위협 연구 | 4.2 R1 근거 | 신규 추가 |
| [25] | Hui et al., IJCIP 2021 | S7 PLC 보안 메커니즘 조작 취약점 분석 | 4.2 R2 근거 | 신규 추가 |
| [26] | 유예지 외, 2024(ACK) | VSAT/위성통신 취약점 분석·대응전략 | 4.2 R5 근거 | 신규 추가, 국내 학부생 학술발표대회 논문 — 권위 수준 낮음을 인지하고 보조 근거로만 사용 |
| [27] | Arkin, 2006 | NAC(Network Access Control) 우회기법 백서 | 4.2 R6 근거 | 신규 추가. **2006년으로 다소 오래됨** — 원 매핑문서도 "다소 오래됨" 주석을 달아둠. 질문 시 "당시부터 알려진 기법 부류를 보여주는 근거"로 방어 |
| [28] | McFail, MITRE MTR210688, 2022 | Detection Engineering in ICS — 2016 우크라이나 정전 사고 사례 분석 | 4.2 R9, 4.4 잠복 서술 근거 | 신규 추가 |
| [29] | Keliris & Maniatakos, NDSS 2019 | ICSREF — ICS 바이너리 자동 리버스엔지니어링 프레임워크 | 4.2 R3/R7 근거 | 신규 추가 |

**질문 대비**: "왜 [26]처럼 학회발표 수준 논문을 인용하냐" → 답변 방향: R5·R8·R10처럼 근거가 약한 항목은 애초에 [확인필요]로 남겼고, [26]은 보조 근거([19]가 주 근거)로만 쓰였으며 인용 자체를 감추지 않고 투명하게 밝혔다는 점을 강조.

---

## 12. 의사결정 히스토리 타임라인

프로젝트 진행 중 방향이 여러 번 바뀌었다. 질문에서 "왜 처음과 다르냐"는 지적이 나올 수 있으므로 정리해 둔다.

| 날짜 | 결정 | 계기 |
|---|---|---|
| 2026-08-13 | 로드맵 확정: 학술대회 원고 먼저, 정식논문은 확장판. IV장(위협모델링) 전체를 정식논문 몫으로 남기고 학술대회는 R1·R6·R9만 예시 | 최초 기획 |
| 2026-08-14 | 후속연구 방향 메모(위협모델링 체계화 + testbed 실증 2단계) | — |
| 2026-08-19 | 1st_research를 2nd_research로 통합, 위협모델링을 2nd_research paper2로 이관 계획 | AI 적대자 트랙과의 병합 논의 |
| 2026-08-20 | 적용범위 이탈 경로 2개(경로 A/B) 공식 확정. 위협모델링·위험평가를 **이번 논문에서 제외**하기로 확정 | 원문 대조 심화, 학술대회 3쪽 제약 인식 |
| 2026-08-24 | 정식논문(R3→R4) 승격. 경로 B는 학술대회 원고로 귀속(정식논문 R3는 경로 A만). 문서부담(Appendix I) 논거 폐기 확정. IV장을 "4.1/4.2 두 예시" 구성으로 신설 | 두 트랙 병행 재개, R2 리뷰 반영 |
| 2026-08-24(같은 날 재개정) | R4를 6쪽 목표로 축약(R4-short) 시도 | JKIICE 게재료 구간 확인(6쪽 = 게재료 문턱으로 추정, 미확인 상태였음) |
| 2026-08-26 | round-03 리뷰(R4-short 대상, Major×2/Minor×2) → **6쪽 목표 폐기, Full Paper 확정, 위협모델링 재도입, 경로 B를 정식논문 IV장 주축으로 재배치, IV장을 R1~R10/R11 체계적 매핑 + 심층 시나리오 2개로 전면 재구성(R5)** | round-03 리뷰가 "6쪽 제약과 IV장 두 예시 구성의 구조적 충돌"을 지적, paper2_threat-modeling이 미착수 계획서에 불과함을 재확인 |

**핵심 반전 지점**: 2026-08-20에 "위협모델링 제외"를 결정했다가 2026-08-26에 재도입한 것, 2026-08-24에 "경로 B는 학술대회 전용"이라 정했다가 2026-08-26에 정식논문에도 포함시킨 것. 두 반전 모두 **"두 원고가 다루는 층위가 달라 겹치지 않는다"**(학술대회=조문분석만, 정식논문=위협모델링 포함)는 재확인이 근거다.

---

## 13. 예상 질문과 답변 (Q&A)

### 연구 설계 전반

**Q. 이 논문의 핵심 기여가 정확히 무엇인가?**
A. 두 가지다. ① 강제 규정을 분석할 때 "요구사항의 강도"뿐 아니라 "적용 범위에서 벗어나는 방식" 자체를 분석 단위로 삼을 수 있음을 보이고, 판정을 거치는 이탈(경로 A)과 판정 자체가 없는 이탈(경로 B)을 구분했다. ② 그 분석 단위 위에서 STRIDE-per-interaction+ATT&CK for ICS를 결합해 규정이 스스로 비운 자리에 한정된 잔여 위협 목록(R1~R11)을 체계적으로 구성했다.

**Q. 기술적 취약점을 나열한 논문 아닌가? 신규성이 뭔가?**
A. 아니다. 개별 취약점 자체는 선행연구(TRITON, Forescout 등)에 이미 보고돼 있다. 신규성은 "그 취약점들이 **왜 규정상 남는가**"를 조문 단위로 증명한 데 있다 — 즉 규정을 준수해도(모든 필수·추가 기준을 충족해도) 왜 이 위협이 남는지를 조문 자체에서 연역한다.

**Q. 왜 6.4와 1.3.2 두 가지만 다루나? 다른 이탈 경로는 없나?**
A. 본 논문이 확인한 범위에서는 이 둘이 UR E26이 명시적으로 두고 있는 적용범위 이탈 방식의 전부다. 다른 경로(예: 선급의 재량적 예외 승인 관행 등)는 조문에 근거가 없거나 조사되지 않아 범위 밖으로 뒀다.

**Q. 왜 하필 이 두 가지 심층 시나리오(계측기 경로 vs IT→OT 경로)를 골랐나?**
A. 각각 경로 A와 경로 B를 대표하는 사례이면서, 두 경로가 성립 조건의 폭에서 대조적이기 때문이다. 계측기 경로(4.5)는 물리적 회선 조작(절단, in-line 장치 삽입)을 전제해 성립 문턱이 상대적으로 높고, IT→OT 경로(4.4)는 IT 영역이 애초에 판정을 거치지 않고 경계가 논리적 수단(방화벽)에만 의존해 문턱이 낮다. 후자를 주축으로 다룬 것은 이 판단 때문이다.

**Q. 실제로 이런 공격이 일어난다는 증거가 있나? 실증했나?**
A. 실증하지 않았다. 이 논문은 "조문 해석상 이 경로가 배제되지 않는다"는 것을 보이는 것이지 "실선에서 성립함을 입증"하는 것이 아니다. 문헌에 유사 경로가 보고된 바 있음(TRITON, Forescout, Munro 등)을 근거 문헌으로 배치했지만, 그것이 선박 환경에서 그대로 재현됨을 실증한 것은 아니다. 실증은 2단계 후속연구(testbed)의 몫이다.

**Q. 왜 정량적 위험도(예: FI/SI, 위험 매트릭스)를 안 썼나?**
A. 의도적 범위 제한이다. 정량적 위험도 산정은 방벽 목록화·발생확률 추정 등 이 논문이 다루지 않기로 한 실증적 요소를 전제한다. 이 논문은 정성적 매핑과 서사적 kill-chain으로 "가능성이 배제되지 않음"을 보이는 데 그친다.

**Q. AI 기반 공격은 왜 안 다루나? 요즘 트렌드 아닌가?**
A. 별도 연구질문이기 때문이다. AI 적대자가 이 잔여위협들을 어떻게 증폭시키는지는 2nd_research의 별개 프로젝트(paper2_threat-modeling)가 다룰 몫으로 명확히 구분해 두었다. 이 논문의 RQ는 "규정의 이탈 경로 설계 자체가 충분한가"이지 "AI가 공격을 얼마나 쉽게 만드는가"가 아니다.

### 규정 해석 관련

**Q. 철회된 초판(2022)을 왜 인용하나? 규범력이 없지 않나?**
A. 초판을 규범적 근거로 쓰지 않는다. 초판은 "어떤 조건을 제외 판정 기준의 한 항목으로 규칙 안에 둘 수 있다"는 **존재 가능성의 증명**으로만 쓴다 — 실제로 초판이 전이 관련 항목(c, f)을 판정 기준에 뒀었다는 사실 자체가, 그런 설계가 불가능한 게 아니라 최종안에서 반영되지 않은 선택이었음을 보여준다.

**Q. "Rev.1이 완화됐다"는 것 아닌가?**
A. 아니다. 초판은 발효 전(2024.1.1) 철회되어 시행된 적이 없으므로 "완화"는 부정확한 서술이다. 정확히는 "제정 과정에서 최종안에 반영되지 않았다"이다. 또한 변경이 일방적이지도 않다 — 초판의 4개 항목이 재량(should)에서 필수(shall)로 승격됐고, 다른 일부는 삭제·약화됐다(assurance/evidence, Known/Foreseeable). "일부 강화, 일부 삭제"가 정확한 서술이다.

**Q. "전이 검증 절차가 아예 없다"는 주장 아닌가?**
A. 아니다. 6.3(위험평가 고려요소), 4.1.1.1(자산목록), 4.2.1.4.1(통신기술서), 5.1.4+Appendix I(제출·유지문서), 4.2.1.3(물리적 분할)까지 전이 관련 조항 5개가 잔존한다. 본 논문의 정확한 주장은 "이 5개는 모두 잔존 적용범위 측에 부과된 설계·관리 의무이거나 비강제 권고이며, **제외 판정 단계(6.4)에서 전이를 확인하도록 지시하는 항목이 없다**"는 것이다.

**Q. 4.2.1.3이 "물리적 분할"을 요구하는데 왜 그게 소용없다고 하나?**
A. 두 가지 이유다. 첫째, 4.2.1.3 자체에 단서가 있다 — "이 OT 시스템이 구역이 요구하는 것과 같은 요구사항을 충족하면 물리적 분할 없이도 구역의 일부로 인정된다"는 대안 조항이 바로 이어진다. 이는 4장 적용을 면제받은 CBS가 구역의 요구사항을 충족하는지 판정하는 순환 구조를 만든다. 둘째, simplex serial link 자체가 4.2.1.1에서 zone 간 통제 수단(conduit)으로 명시 허용되므로, 시리얼로 배선된 것을 "분할 위반"으로 보기 애매하다.

**Q. 문언 기준(당해 CBS 자체 인터페이스)과 경로 기준(변환장치 포함) 중 왜 문언 기준을 택했나? 자의적이지 않나?**
A. 조문의 문법적 주어("The CBS shall be isolated")가 당해 CBS 자신에 있다는 점을 근거로 잠정 채택했다. 다만 이것이 유일하게 옳은 해석이라고 주장하지 않는다 — 규칙이 어느 쪽도 명시적으로 지시하지 않는다는 사실 자체가 논문의 핵심 주장(제외 판정이 불확정적이다)을 이미 뒷받침하므로, 어느 해석을 택해도 결론은 성립한다. 경로 기준을 취하면 4.5가 예시하는 CBS는 애초에 제외 후보조차 되지 않는다는 점을 본문에 명시했다.

**Q. Category(UR E22)를 공격 척도로 쓰는 게 맞나?**
A. 쓰지 않는다. 오히려 그 반대를 논증한다 — Category는 "시스템 고장의 안전 결과"를 재는 척도(UR E26 1.3.3에 규정)이지 사이버 공격을 상정한 척도가 아니다. 그런데 6.4 추가기준 a)는 이 고장기준(Category III 여부)을 제외 판정의 척도로 재사용한다. 이 범주 전용(category borrowing)이 R6·R5의 핵심 문제의식이다.

**Q. 법정 항해시스템(ECDIS 등)은 원래 제외 대상이 아니지 않나?**
A. 6.4 조문 전문 어디에도 "법정 시스템은 제외될 수 없다"는 문언이 없다. 오히려 UR E22 1.2(법정규정 적용 CBS는 E22 요구 제외)와 UR E26 1.3.2(그 법정 시스템을 다시 E26 범위에 포함)가 충돌해, 법정 항해·통신 시스템은 E26 대상이면서 E22 Category 체계 밖에 있는 특이 위치에 놓인다 — 이는 오히려 추가기준 a)의 판정척도가 아예 없다는 근거로 쓰인다.

### 방법론 관련

**Q. STRIDE와 ATT&CK을 결합한 게 이 논문의 신규성인가?**
A. 아니다. 이 결합 방법론 자체는 [1],[9]가 이미 각각 STRIDE(+Attack Tree)와 ATT&CK 매핑을 선박 장비에 적용했다. 신규성은 방법론이 아니라 **적용 대상**에 있다 — 선박 시스템 일반이 아니라 "규정이 스스로 제외를 허용하거나 범위에서 비운 자리"에 한정해서 이 방법론을 적용했다는 점이다.

**Q. STRIDE-per-interaction이 정확히 뭔가? 일반 STRIDE와 어떻게 다른가?**
A. 일반 STRIDE는 시스템 전체의 데이터흐름도에 적용해 광범위한 위협을 도출한다(예: [1]의 206건). 본 논문은 시스템 전체가 아니라 신뢹경계를 넘는 **개별 인터페이스**(시리얼 문장, 물리 포트, 원격접속, IP 인터페이스) 단위로만 좁혀서 적용한다 — 규정이 판정하는 단위(CBS의 인터페이스 성질)와 분석 단위를 일치시키기 위함이다.

**Q. 이 논문에서 "신뢰경계"를 다른 연구와 다르게 잡은 이유는?**
A. 선행연구는 육상-선박 또는 선박-외부 경계를 신뢰경계로 잡는다. 본 논문의 문제의식이 "무엇이 E26 적용대상에서 빠지는가"이므로, 신뢰경계도 "E26 4장 요구사항이 적용되는 CBS" vs "그렇지 않은 CBS/영역"으로 재정의했다 — 연구질문과 분석단위를 일치시킨 것이다.

**Q. 매핑표에서 R4, R8, R10은 왜 근거가 부실한가?**
A. 해당 항목을 뒷받침할 1차 문헌을 확보하지 못했다. 지어내는 대신 [확인필요]/[추론]으로 정직하게 표기했다 — 이는 감추기보다 본 논문이 스스로 인정하는 한계이며, 결론에도 명시해 두었다.

**Q. ATT&CK 기법 ID가 T08xx와 T1692.xxx처럼 형식이 다른데 실수 아닌가?**
A. 아니다. MITRE ATT&CK for ICS 매트릭스 자체가 개정을 거치며 두 세대의 ID 체계(구형 T0xxx, 신형 sub-technique 포함 T1xxx.xxx)를 함께 쓰고 있다. 본 논문은 v19.2 매트릭스 현행판을 기준으로 확인했다.

### 게재 전략·트랙 관련

**Q. 학술대회 원고와 정식논문이 자기표절 아닌가?**
A. 아니다. 학술대회 원고(3쪽)는 조문 분석(1.3.2 범위정의, 경계방어 실증요구)만 다루고 위협모델링·ATT&CK 매핑을 다루지 않는다. 정식논문(Full Paper)은 그 조문분석을 포함해 위협모델링까지 확장한 것으로, 학술대회 발표논문의 확장 투고는 통상 인정되는 형태다. 문장 단위 중복을 피하기 위해 같은 소재라도 문장을 새로 쓰는 원칙을 지켰다.

**Q. 왜 6쪽 제약을 처음엔 지키려다 나중에 포기했나?**
A. 6쪽 축약본(R4-short) 작업 결과, 남은 감축 수단이 모두 핵심 논거(초판 대조표, 두 심층 경로 중 하나)의 손실을 수반한다는 것이 확인됐다. round-03 리뷰의 세 명이 독립적으로 "이는 편집 문제가 아니라 연구설계 판단이 필요한 사안"이라 지적했고, 저자는 논거 완결성을 지키는 쪽(Full Paper)을 택했다.

**Q. 왜 위협모델링을 뺐다가 다시 넣었나?**
A. 애초에 별도 프로젝트(2nd_research paper2)로 이관할 계획이었으나, 그 프로젝트가 실제로는 착수되지 않은 계획 문서에 불과함을 확인했다. AI 적대자 증폭이라는 그 프로젝트만의 고유 기여(이 논문의 RQ 밖)만 남기고, 규정 기반 위협모델링 자체는 이 논문에서 직접 수행하는 것이 더 정합적이라 판단했다.

---

## 14. 프로젝트 파일 지도

```
1st_research/
├── CLAUDE.md                          # 프로젝트 전체 지침 — 항상 먼저 확인
├── reference/                         # ← 이 문서가 있는 곳
│   └── 2026-08-26_paper-background_reference.md
├── outputs/
│   ├── 2026-08-26_journal-paper_R5.md # ★ 현재 작업본(정식논문)
│   ├── 2026-08-24_journal-paper_R4.md # R5의 베이스, 동결
│   ├── 2026-08-24_journal-paper_R4-short.md # 6쪽 축약본, 목적 상실, 참고용 보관
│   └── 2026-08-13_paper-outline_draft.md # 최초 6장 뼈대
├── conference/
│   ├── CLAUDE.md                      # 학술대회 트랙 지침
│   ├── 2026-08-24_conference-paper_draft.md # 학술대회 현행 원고(3쪽)
│   └── 2026-08-24_source-verification_note.md # 조문 대조표
├── llm_wiki/
│   ├── 2026-08-13_e26-exclusion-residual-threat_mapping.md # R1~R11 원 매핑표(IV장 근거)
│   ├── 2026-08-13_research-framing_compliance-vs-security.md # 논증전략(P1/P2/P3)
│   └── 2026-08-14_e26-2022-vs-rev1_verification.md # 초판-Rev.1 대조 원자료
├── reviews/
│   ├── round1/, round2/, round-03/    # 리뷰 4인+synthesis. round-03이 최신, 오늘 전환의 계기
├── notes/
│   ├── 2026-08-26_threat-modeling-revival_note.md # ★ 최신 진행상황
│   ├── 2026-08-24_track-split_note.md
│   └── 2026-08-20_research-note.md
├── rules/                             # 규정 원문 PDF (UR E22/E26/E27, Rec.166/171/190 등)
└── papers/                            # 인용 논문 원문 PDF([1],[9],[17],[19],[21],[23]~[29] 등)
```

**질문이 왔을 때 확인 순서**: ① 이 문서(reference/)에서 빠른 답 찾기 → ② 없으면 `outputs/2026-08-26_journal-paper_R5.md` 본문·수정로그 확인 → ③ 조문 원문 자체 확인이 필요하면 `rules/`의 PDF 원문 대조 → ④ 방향성/이력 질문이면 `notes/`와 `CLAUDE.md`의 날짜별 결정사항 확인.
