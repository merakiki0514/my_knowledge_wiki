---
type: concept
tags:
  - concept
---

# Essential Services

## Definition

[SOURCE] IACS UR E26 §2

> Services for propulsion and steering, and safety of the ship. Essential services comprise "Primary Essential Services" and "Secondary Essential Services"

| 구분 | 정의 (E26 §2) |
| --- | --- |
| **Primary Essential Services** | 추진과 조타를 유지하기 위해 **연속 운전이 필요한** 서비스 |
| **Secondary Essential Services** | 추진·조타 유지를 위해 반드시 연속 운전할 필요는 없으나, **선박의 안전 유지에 필요한** 서비스 |

[SOURCE] UR E27 §1.4는 `Essential Systems`로 정의한다 — `Computer Based System contributing to the provision of services essential for propulsion and steering, and safety of the ship`. 이후 1·2차 구분 서술은 E26과 동일하다.

즉 **E26은 서비스(service), E27은 시스템(system)**을 정의 대상으로 삼는다. IACS Rec 166 §4.1.19에도 `Essential Systems` 정의가 있다.

## Why it matters

[SOURCE] UR E27 §2.3 Essential Systems Availability가 **보안 조치에 제약을 건다.**

| 조항 | 내용 |
| --- | --- |
| §2.3.1 | 필수 시스템에 대한 보안 조치가 **시스템 가용성을 저해해서는 안 된다** |
| §2.3.2 | 보안 조치 구현이 안전 기능·제어 기능·감시 기능의 상실을 초래해서는 안 된다 |
| §2.3.3 | 선박이 임무상 중요한 운항을 계속할 수 있도록 설계되어야 한다 |

[INFERENCE] 이것이 해양 OT 보안이 일반 IT 보안과 갈라지는 핵심 지점이다. IT에서는 의심스러우면 차단하는 것이 기본이지만, 여기서는 **보안 조치가 안전을 해치면 안 된다**는 제약이 상위에 있다. → [[IT and OT]]

같은 이유로 E26 §4.3.1.3은 IDS를 `may be implemented`로 두고, 도입 시 **passive여야 하며 CBS 성능에 영향을 주는 보호 기능을 작동시켜서는 안 된다**고 조건을 단다.

## Key Characteristics

[INFERENCE] 이 개념은 두 방향으로 작용한다.

1. **보호 대상** — 필수 서비스에 기여하는 CBS가 우선 보호 대상이 된다.
2. **제약 조건** — 동시에 그 CBS에는 가용성을 해치는 보안 조치를 적용할 수 없다.

즉 가장 중요한 시스템일수록 적용 가능한 보안 조치의 폭이 좁아진다. [[Compensating Countermeasure]]가 필요해지는 구조적 이유로 보인다.

## Related Concepts

- [[IT and OT]] — 가용성 우선 원칙의 근거
- [[Compensating Countermeasure]] — 가용성 제약으로 요건 충족이 어려울 때
- [[System Category]] — 고장 결과의 심각도에 따른 분류. 필수 서비스와 밀접
- [[Computer Based System]]
- [[Cyber Resilience]] — 정의가 `safe operation of a ship`을 목표로 삼는다

## Applications

| 문서 | 위치 |
| --- | --- |
| UR E27 | §1.4 정의 / **§2.3 필수 시스템 가용성** |
| UR E26 | §2 정의 / §4.4.2 로컬·독립·수동 운전 / §4.4.4 최소 위험 상태로의 fallback |
| UR E22 | §3.1 시스템 카테고리 — 추진·조타 제어와 선박 안전 기능이 Cat III |
| IACS Rec 166 | §4.1.19 정의 / §4.1.7 Critical System |
| IACS Rec 171 | §5 핵심 장비 식별 — Cat III 예시에 추진·조타·전력·선박안전계통 열거 |
| BIMCO v5 | §5.3 "Critical" 장비·기술 시스템 |

## Limitations

- [SOURCE] E26은 `Essential services`, E27과 Rec 166은 `Essential Systems`, Rec 166 §4.1.7은 `Critical System`, BIMCO §5.3은 `"Critical" equipment`로 부른다. **용어가 통일되어 있지 않다.**
- [확인 필요] 네 용어가 같은 범위를 가리키는지 대조하지 않았다.
- [확인 필요] E26 §2 정의는 서비스 목록을 열거하지 않는다. 어떤 서비스가 Primary인지 Secondary인지는 선박별 판단이 필요해 보인다.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §4.3.1.3, §4.4.2, §4.4.4
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4, §2.3
- `Database/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` §3.1
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.7, §4.1.19
- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` §5
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §5.3

## Notes

용어 불일치 문제는 [[Term Locator#문서 간 정의 차이 (확인된 것)]]에 함께 기록할 것. [확인 필요] 항목이다.
