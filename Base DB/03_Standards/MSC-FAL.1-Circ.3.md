---
type: standard
tags:
  - standard
  - imo
---

# MSC-FAL.1-Circ.3

IMO **Guidelines on Maritime Cyber Risk Management**. 이 프로젝트 자료 계층의 **최상위 국제 지침**.

## Version

| 판본 | 승인 | 상태 |
| --- | --- | --- |
| 원판 | FAL 41 (2017-04) + MSC 98 (2017-06) | — |
| Rev.1 | MSC 104 (2021-10) + FAL 46 (2022-05), §4.2 갱신 | — |
| Rev.2 | — | `Database/`에 **없음** |
| **Rev.3 (2025-04-04)** | MSC 108 (2024-05) + FAL 49 (2025-03) | **현행 · 보유** |

[SOURCE] 표지 §6 — 이 회람문과 그 개정판은 **MSC.1/Circ.1526(잠정 지침)을 대체한다.**

⚠️ **다른 문서들이 인용한 것은 Rev.3 이전 판이다.** Rec 166·Rec 171·BIMCO v5는 판본 미표기, MSC 109/5는 Rev.2를 인용한다. → [[Database Inventory#3.2 인용되는 MSC-FAL 판본이 문서마다 다르다]]

[SOURCE] §4.4 — `Reference should be made to the most current version of any guidance or standards utilized.`

## Overview

[SOURCE] §1.1 — 이 지침은 해양 사이버 리스크 관리에 대한 **고위 수준 권고**를 제공한다. `maritime cyber risk`는 [[Computer Based System]]이 잠재적 상황·사건에 의해 위협받는 정도로서, 정보나 시스템의 손상·손실·훼손 결과로 해운 관련 운항·안전·보안 실패를 초래할 수 있는 것을 말한다.

[SOURCE] §2.2.7 — **급변하는 기술과 위협 때문에 기술 표준만으로는 리스크를 다루기 어렵다.** 그래서 기존 안전·보안 관리 관행의 자연스러운 연장으로서 리스크 관리 접근을 권고한다.

## Scope

[SOURCE] §2.3.1 — 주로 **선박**을 대상으로 하며, 사이버 영역에서의 안전·보안 관리 관행을 장려하도록 설계되었다.

[SOURCE] §2.3.2 — 어떤 두 ISM 회사도 같지 않으므로 지침은 **넓은 용어로 표현**되었다. 디지털 시스템이 제한적인 선박은 단순 적용으로 충분할 수 있고, 복잡한 선박은 더 높은 수준의 주의가 필요하며 추가 자원을 구해야 한다.

[SOURCE] §2.2.1 — 관련될 수 있는 시스템 (비망라):

```text
.1 선교 시스템 (항해, 선박안전, 통신 등)
.2 화물·급유·윤활·밸러스트 등 펌핑 취급·관리 시스템
.3 추진·연료·기계 관리 및 동력 제어 시스템
.4 보안·출입통제·감시 시스템
.5 여객·승무원 서비스 및 관리 시스템
.6 여객·승무원·하도급 인력 대상 공중망
.7 행정 및 승무원 복지 시스템
.8 선박-항만 인터페이스
.9 선박-육상 통합 시스템 (원격제어 시스템 / MASS 등)
```

## Key Requirements

### §3.5 기능요소 6개 — Rev.3의 핵심 변화

⚠️ [SOURCE] **`Govern`이 포함된 6개 구조다.** [[UR E26]]·[[IACS Rec 166]]·[[BIMCO Guidelines on Cyber Security Onboard Ships]]는 5개다.

[SOURCE] §3.5 — 기능요소는 **순차적이지 않으며 모두 동시·연속적**이어야 한다. 각 요소 아래 열거된 통제항목은 **구현되어야 할 최소 통제(minimum controls that should be implemented)**다.

| 요소 | 주요 통제 |
| --- | --- |
| **Govern** (§3.5.1) | 리스크 관리 전략·기대·정책 수립·감시, 역할·책임 정의, 업무연속성(백업·재해복구·위기관리). **책임자 지정**과 그에 대한 권한·지원·전문성 확보 |
| **Identify** (§3.5.2) | 시스템·자산·서비스·데이터·능력 및 안전필수 시스템 간 상호의존성(정보 흐름 포함) 식별 — **소프트웨어·하드웨어 공급망 포함**. **선내 디지털 시스템 인벤토리** 수립·유지. 리스크 평가 |
| **Protect** (§3.5.3) | 고유 자격증명·계정 분리·퇴사자 계정 해지 / 기본 암호 변경·강한 암호 정책·**MFA** / 인터넷 노출 서비스 제한·HW·SW 승인 절차·**침입탐지용 로그 수집 보관**·**OT망과 IT망 분리** / 방화벽·백신·암호기술 정책 / **비인가 이동식 매체 통제** / **연간 사이버보안 교육 의무** / 정기 백업·SW 업데이트·IR 계획 / 공급망 보안 정책 / 효과성 평가(감사) |
| **Detect** (§3.5.4) | 관련 위협·위협행위자 TTP 목록 유지 및 능동 모니터링. 교육에 사고 인지·탐지 포함 |
| **Respond** (§3.5.5) | 주관청이 정한 기한 내 보고. **사고 기록 보관**. 교육에 대응 포함 |
| **Recover** (§3.5.6) | 핵심 자산·시스템 복구·복원 전략 수립·유지·이행. **근본원인 분석**으로 재발 방지 |

### §3.5.3.6 교육 요구 — 구체적이다

[SOURCE] **전 직원 연간 기초 사이버보안 교육**, **OT 사용자 대상 OT 특화 교육**, **승선 시 전 승무원 친숙화**를 의무화한다. 교육에는 사이버 위생, 진행 중인 사고의 인지·탐지, 대응·복구가 포함되어야 한다. **훈련·연습 등을 통해 지식을 때때로 시험**해야 한다.

## Practical Implications

[SOURCE] §4.2 추가 표준 (비망라):

1. ISO/IEC 27001
2. **IACS UR E26**
3. **IACS UR E27**

[SOURCE] §4.3 추가 지침·산업 모범사례 (비망라):

1. BIMCO 등이 제작·지원하는 The Guidelines on Cyber Security Onboard Ships
2. **IACS Rec 166** (Consolidated IACS Recommendation on cyber resilience)
3. **NIST 2.0 Framework**
4. IAPH Cybersecurity Guidelines for Ports and Port Facilities

[INFERENCE] IMO 지침이 IACS UR을 직접 참조 표준으로 지목한다는 점에서, **IMO → IACS 계층 구조가 문서상 확인된다.**

[SOURCE] §4.2·§4.3 각주 — 열거된 지침·표준은 **본 기구가 발행한 것이 아니며 사용은 이용자의 재량**이다.

## Related Standards

- [[UR E26]] · [[UR E27]] — §4.2가 참조 표준으로 열거
- [[IACS Rec 166]] · [[BIMCO Guidelines on Cyber Security Onboard Ships]] · [[NIST CSF 2.0]] — §4.3이 열거
- [[IACS Rec 171]] — ISM/SMS 통합
- [[ISM Code]]
- [[MASS Code]] — draft §9.7이 사이버보안 언급

## Related Concepts

[[Cyber Risk Management]] · [[Computer Based System]] · [[IT and OT]] · [[Cyber Incident]] · [[Attack Surface]]

## Sources

- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf`
- 조항 위치: [[Regulation Locator#3. 목표 · 요건 체계]]

## Notes

[INFERENCE] Rev.3의 `Govern`은 **NIST CSF 2.0에서 온 것으로 보인다.** §4.3.3이 CSF 2.0을 참조하고, Govern의 문언이 CSF 2.0 §2와 거의 일치한다. → [[Database Inventory#거버넌스 위치의 변천 (보유 원본만으로 재구성)]]
