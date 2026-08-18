---
type: standard
tags:
  - standard
  - iacs
---

# UR E26

IACS Unified Requirement E26 — **Cyber resilience of ships**. 선박을 하나의 집합체로 보는 강제 요건.

## Version

| 판본 | 발행 | 상태 |
| --- | --- | --- |
| E26 (Apr 2022) | 2022-04 | ⚠️ **철회.** 2024-01-01 발효 전 withdrawn (Note 1) |
| **E26 Rev.1 (Nov 2023)** | 2023-11, Complete Revision | **현행** |

[SOURCE] Note 2 — Rev.1은 **2024년 7월 1일 이후 건조계약** 선박에 IACS 선급이 통일 적용한다. 그 외 선박에는 비강제 지침으로 사용할 수 있다.

[SOURCE] Note 3 — "contracted for construction"은 선주와 조선소가 건조 계약에 서명한 날. 상세는 IACS PR No.29 참조.

⚠️ 두 판본이 모두 `Database/`에 있다. **혼용 금지.** 2022년판은 `UR-E26-Apr-2022-WITHDRAWN.pdf`다.

## Overview

[SOURCE] §1.2 Aim and purpose

> The aim of this UR is to provide a minimum set of requirements for cyber resilience of ships, with the purpose of providing technical means to stakeholders which would lead to cyber resilient ships.

[SOURCE] §1.2 — 이 UR은 **선박을 집합체(collective entity)로** 대상 삼으며, 선내 시스템·장비·구성요소의 사이버 복원성을 다루는 다른 UR 및 산업 표준의 **보완적 적용을 위한 기반**으로 의도되었다.

[SOURCE] §1 Introduction — IACS는 목표 기반 접근으로 **전체 위협면(full threat surface)**에 일관되게 적용되는 최소 요건이 필요하다고 본다.

## Scope

### 적용 선박 (§1.3.1)

[SOURCE] **강제 적용**:

- 국제항해 여객선 (여객용 고속선 포함)
- 국제항해 **500 GT 이상** 화물선
- 국제항해 500 GT 이상 고속선
- 500 GT 이상 이동식 해양 시추 유닛
- 건설에 종사하는 자항식 이동 해양 유닛 (풍력터빈 설치·유지·수리, 크레인 유닛, 시추 텐더, 숙소 등)

[SOURCE] **비강제 지침으로 사용 가능**: 군함·병력수송선, 500 GT 미만 화물선, 기계추진 아닌 선박, 원시 구조 목선, 여객 12명 이하 여객 요트, 상업에 종사하지 않는 유람 요트, 어선, 특정 해역 고정 해양 설비(FPSO, FSU 등)

### 적용 시스템 (§1.3.2)

[SOURCE] a) 추진, 조타, 앵커·계류, 발전·배전, 화재탐지·소화, 빌지·밸러스트·적하계산기, 수밀·침수탐지, 조명(비상·저위치·항해등 등), 운항 위험을 초래할 수 있는 required safety system(비상정지·화물안전·압력용기안전·가스탐지 등), 법정 항해 시스템, 선급·법정 요구 내외부 통신 시스템

[SOURCE] b) 위 CBS로부터 다른 시스템으로의 **모든 인터페이스**

⚠️ [SOURCE] §1.3.2 — **항해·무선 시스템은 IEC 61162-460 또는 동등 표준의 적용을 UR E27 §4 보안능력 대신 선급이 수용할 수 있다.** 단 UR E26 요건은 준수해야 한다. → [[IEC 61162 Series]]

## Structure

[SOURCE] §1.1 Table 1

| 구분 | 내용 |
| --- | --- |
| Introductory | 1 Introduction · 2 Definitions · 3 Goals and Organization of Requirements |
| **Main** | **4 Requirements** (4.1 Identify / 4.2 Protect / 4.3 Detect / 4.4 Respond / 4.5 Recover) · 5 Demonstration of compliance |
| Supplementary | 6 적용 제외를 위한 리스크 평가 (제외 시에만 필요) |
| 부속 | Appendix I 조치·문서 요약 · Appendix II 요건·문서 요약 |

⚠️ [SOURCE] 2022년판은 §5가 `Test plan for performance evaluation and testing`, Appendix가 1개였다. Rev.1에서 §5가 `Demonstration of compliance`로 바뀌고 Appendix가 2개가 되었다.

## Key Requirements

[SOURCE] §4 — 기능요소 5개 구조. **Govern은 없다.**

| 요소 | 요건 |
| --- | --- |
| **4.1 Identify** | 4.1.1 선박 자산 목록 |
| **4.2 Protect** | 4.2.1 보안 존·네트워크 분할 / 4.2.2 네트워크 보호수단 / 4.2.3 악성코드 방어 / 4.2.4 접근제어 / 4.2.5 무선통신 / 4.2.6 원격접속·비신뢰망 통신 / 4.2.7 모바일·휴대장치 |
| **4.3 Detect** | 4.3.1 네트워크 운영 모니터링 / 4.3.2 CBS·네트워크 검증·진단 |
| **4.4 Respond** | 4.4.1 사고대응계획 / 4.4.2 로컬·독립·수동 운전 / 4.4.3 네트워크 격리 / 4.4.4 최소위험상태 fallback |
| **4.5 Recover** | 4.5.1 복구계획 / 4.5.2 백업·복원 / 4.5.3 통제된 셧다운·리셋·롤백·재시작 |

각 요건은 `Requirement → Rationale → Requirement details → Demonstration of compliance(설계/건조/시운전/운항)` 구조로 반복된다.

## Practical Implications

[SOURCE] §5.1 설계·건조 단계 제출 문서 5종:

1. Zones and conduit diagram (§5.1.1)
2. Cyber security design description, CSDD (§5.1.2)
3. Vessel asset inventory (§5.1.3)
4. 적용 제외 리스크 평가 (§5.1.4)
5. 보완대책 기술서 (§5.1.5)

[SOURCE] §5.2.1 시운전 — Ship cyber resilience test procedure → [[Ship Cyber Resilience Test]]
[SOURCE] §5.3 운항 — 최초 연차검사(§5.3.1), 후속 연차검사(§5.3.2)

⚠️ **주의할 표현** [SOURCE]:

- §4.3.1.3 — IDS는 `**may** be implemented`. 의무가 아니며, 도입 시 passive여야 하고 CBS 성능에 영향을 주는 보호 기능을 작동시켜서는 안 된다.
- §4.2.6.3 — 원격접속 로그는 `retain for a period of time **sufficient for offline review**`. **구체적 일수 규정이 없다.**

## Related Standards

- [[UR E27]] — 시스템·장비 단위 요건. E26과 상호 보완
- [[UR E22]] — 소프트웨어 기능 및 [[System Category]] 정의
- [[IACS Rec 166]] — 비강제 권고. **충돌 시 E26 우선** (§1.3.4)
- [[IACS Rec 190]] — 자산 목록 템플릿
- [[MSC-FAL.1-Circ.3]] — §4.2가 E26을 참조 표준으로 열거
- [[IEC 61162 Series]] — §1.3.2의 대체 경로

## Related Concepts

[[Cyber Resilience]] · [[Security Zone]] · [[Untrusted Network]] · [[Computer Based System]] · [[Essential Services]] · [[Attack Surface]] · [[Compensating Countermeasure]]

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` (현행)
- `Database/UR-E26-Apr-2022-WITHDRAWN.pdf` (철회, 대조용)
- 조항 위치: [[Regulation Locator]]
