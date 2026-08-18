---
type: standard
tags:
  - standard
  - iacs
---

# UR E22

IACS Unified Requirement E22 — **Computer-based systems**. [[System Category]] 정의의 **원문 출처**.

## Version

| 판본 | 발행 | 적용 |
| --- | --- | --- |
| E22 (Dec 2006) | 2006-12 | 2008-01-01 이후 건조계약 |
| Corr.1 (Oct 2007) / Rev.1 (Sept 2010) | | Rev.1은 2012-01-01 이후 |
| Rev.2 (June 2016) | | 2017-07-01 이후 |
| **Rev.3 (June 2023) + Corr.1 (Sep 2025)** | | **2024-07-01 이후 건조계약** (Note 4) |

## Overview

[SOURCE] §1.1 Scope

> These requirements apply to design, construction, commissioning and maintenance of computer-based systems where they depend on software for the proper achievement of their functions.
> These requirements apply to systems which provide control, alarm, monitoring, safety, or internal vessel communication functions that are subject to classification requirements.

[SOURCE] §1.2 Exclusion — **법정 규정이 적용되는 CBS는 이 UR에서 제외된다.**

Guidance에 예시가 있다 — SOLAS Ch.V·IV가 요구하는 항해 시스템과 무선통신 시스템, 적하계산기·복원성 컴퓨터. 적하계산기·복원성 컴퓨터는 IACS Rec No.48을 고려할 수 있다.

⚠️ [INFERENCE] 이 제외 조항 때문에 **항해 장비는 E22 카테고리가 `not applicable`일 수 있으나, [[UR E26]] 범위에는 들어가므로 자산 목록에는 등재된다.** ([[IACS Rec 190]] §6.1 컬럼 E)

## Key Requirements

### §3.1 System category definitions — **이 UR의 핵심**

[SOURCE] Table 3. 분류 기준은 **기능이 고장났을 때 결과의 심각도**다.

| Cat | 고장의 영향 | 전형적 기능 |
| --- | --- | --- |
| **I** | 인명·선박 안전·환경에 위험한 상황을 **초래하지 않음** | 감시·정보·관리 기능 |
| **II** | 위험한 상황을 **결국(eventually) 초래할 수 있음** | 선박을 정상 운항·거주 조건으로 유지하는 데 필요한 경보·감시·제어 |
| **III** | 위험·파국적 상황을 **즉시(immediately) 초래할 수 있음** | 추진·조타 유지 제어, 선박 안전 기능 |

[SOURCE] §3.2 — Cat I은 통상 선급 검증 대상이 아니다. 다만 카테고리 판정 확인 및 Cat II·III 운영에 영향을 주지 않음을 확인하기 위해 요청 시 정보 제출.

[SOURCE] §3.3 — **카테고리는 항상 해당 선박의 맥락에서 평가하며, 선박마다 달라질 수 있다.** §3.3의 예시는 지침일 뿐이다.

### 그 밖의 구조

| 절 | 내용 |
| --- | --- |
| 2 | 시스템·구성요소 승인 (2.2 형식승인) |
| 4.1 | 일반 요건 (4.1.1 생명주기 접근, 4.1.2 품질경영시스템) |
| **4.2** | **시스템 공급자 요건** — 4.2.2 고유 식별, 4.2.3 시스템 기술서, 4.2.5 코드 작성·파라미터화·시험, 4.2.7 **FAT**, 4.2.8 선상 보안 설치 |
| **4.3** | **시스템 통합자 요건** — 4.3.3 **카테고리 결정**, 4.3.4 리스크 평가, 4.3.5 선박 시스템 아키텍처 정의, 4.3.6 **SAT**, 4.3.7 **통합시험(SOST)**, 4.3.8 변경관리 |
| 5 | 유지보수 요건 (선주 / 통합자 / 공급자) |
| 6 | 변경 관리 (6.1 일반, 6.2 문서화된 절차, 6.3 이해관계자 합의) |

### 약어 (§1.5.1)

[SOURCE] Cat I/II/III, COTS, FAT(Factory acceptance test), FMEA, IT, OT, PMS(Planned maintenance system), SAT(System acceptance test), **SOST(System of systems test)**, **SSLS(Ship software logging system)**, UR

## Practical Implications

[INFERENCE] 사이버보안 작업에서 E22가 쓰이는 지점은 두 가지다.

1. **카테고리 판정** — [[IACS Rec 190]] 자산 목록 컬럼 E, [[IACS Rec 171 Cyber Risk Assessment]]의 `RL = 2 × (Cat + L + P − 4)` 수식 입력값
2. **고유 식별자** — §4.2.2·§7.1.1이 Cat II·III에 요구. 자산 목록 컬럼 H

[SOURCE] [[UR E26]] §4.3.1.3이 대역폭 임계 초과 알람과 관련해 **UR E22 §7.2.1**을 참조한다.

## Related Standards

- [[UR E26]] · [[UR E27]] — 사이버 복원성. E22는 소프트웨어 기능성 담당
- [[UR E10]] — 하드웨어 환경 성능
- [[IACS Rec 190]] — 컬럼 E·H가 E22 근거
- [[IACS Rec 171]] — §5가 E22 카테고리로 핵심 장비 식별

## Related Concepts

[[System Category]] · [[Computer Based System]] · [[Essential Services]]

## Sources

- `Database/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf`
- 조항 위치: [[Regulation Locator#13. 시스템 분류 · 보완대책]]

## Notes

[SOURCE] 카테고리를 인용할 때 **출처는 항상 UR E22 §3.1**로 쓴다. E26·E27·Rec 166의 서술은 참조이지 정의가 아니다.
