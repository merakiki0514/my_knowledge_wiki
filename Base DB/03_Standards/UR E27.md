---
type: standard
tags:
  - standard
  - iacs
---

# UR E27

IACS Unified Requirement E27 — **Cyber resilience of on-board systems and equipment**. [[UR E26]]가 선박 단위라면 이쪽은 **시스템·장비 단위**.

## Version

| 판본 | 발행 | 상태 |
| --- | --- | --- |
| E27 (Apr 2022) | 2022-04 | ⚠️ 철회 (Note 1). `Database/`에 **없음** |
| **E27 Rev.1 (Sep 2023)** | 2023-09 | **현행** |

[SOURCE] Note 2 — **2024년 7월 1일 이후 건조계약** 선박에 통일 적용.

## Overview

[SOURCE] §1.1 — 선박·항만·컨테이너 터미널 등의 기술 발전과 OT·IT 의존 증가로 사이버 공격 가능성이 커졌다. 이에 대응하려면 **설계·제조 단계에서 장비와 시스템에 보안 기능을 통합**해야 하며, 따라서 사이버 복원성을 갖춘 시스템·장비를 인도하기 위한 최소 요건이 필요하다.

## Scope

### 적용 선박 (§1.3)

[SOURCE] **[[UR E26]] §1.3.1과 동일한 선박 목록**을 강제/비강제로 나눈다.

⚠️ [SOURCE] §1.3 — 항해·무선 시스템은 **IEC 61162-460 또는 동등 표준을 §4의 보안능력 대신** 선급이 수용할 수 있다. 단 UR E26 요건 준수가 조건이다. → [[IEC 61162 Series]]

### 다루지 않는 것 (§1.2 Limitations)

[SOURCE] 이 UR은 **시스템 하드웨어의 환경 성능과 소프트웨어의 기능성을 다루지 않는다.** 다음을 병행 적용해야 한다.

- **[[UR E10]]** — 하드웨어 환경 성능
- **[[UR E22]]** — 소프트웨어 기능성

## Structure

| 절 | 내용 |
| --- | --- |
| 1 | General (1.2 Limitations, 1.3 Scope, 1.3.1 ICT, 1.4 정의·약어) |
| 2 | 2.1 시스템·장비 / 2.2 사이버 복원성 / **2.3 필수 시스템 가용성** / **2.4 보완대책** |
| 3 | CBS Documentation — 제출 문서 10종 (§3.1.1~§3.1.10) |
| **4** | **System Requirements — §4.1 필수 보안능력 30개 / §4.2 추가 보안능력** |

## Key Requirements

### §4.1 필수 보안능력 (#1~#30)

[SOURCE] 모두 `The CBS shall...` 형태의 강제 요건이다.

| # | 항목 | # | 항목 |
| --- | --- | --- | --- |
| 1 | Human user 식별·인증 | 16 | Timestamps |
| 2 | Account management | 17 | Communication 무결성 |
| 3 | Identifier | 18 | Malicious code |
| 4 | Authenticator | 19 | Security 검증 지원 |
| 5 | Wireless access | 20 | Deterministic 출력 |
| 6 | Strength of authenticator | 21 | Information 보호 |
| 7 | Authenticator 피드백 은닉 | 22 | Use of cryptography |
| 8 | Authorization | 23 | Audit log 접근 |
| 9 | Wireless use | 24 | Denial of service 대응 |
| 10 | 휴대·모바일 장치 사용 통제 | 25 | Resource 제한 |
| 11 | Mobile code | 26 | System backup |
| 12 | Session lock | 27 | System recovery |
| 13 | Auditable events | 28 | **Alternative power** |
| 14 | Audit storage | 29 | Network·traffic 설정 |
| 15 | Response to audit 실패 | 30 | Least functionality |

### §4.2 추가 보안능력 (#31~)

[SOURCE] #31 **Multifactor authentication** — 인적 사용자에 대해 요구되는 조건이 있음. #32 Software process 식별·인증 등.

### §2.3 필수 시스템 가용성

[SOURCE] **보안 조치가 안전을 해쳐서는 안 된다는 제약.**

- §2.3.1 필수 시스템에 대한 보안 조치가 가용성을 저해해서는 안 된다
- §2.3.2 보안 조치 구현이 안전·제어·감시 기능의 상실을 초래해서는 안 된다
- §2.3.3 임무상 중요한 운항을 계속할 수 있도록 설계

→ [[Essential Services]]

### §2.4 보완대책

[SOURCE] 고유 보안능력 대신 또는 추가로 사용 가능. **원 요건의 의도(intent)와 엄격성(rigor)을 충족**해야 한다. → [[Compensating Countermeasure]]

## Practical Implications

[SOURCE] §3.1 — 선급에 제출·승인받아야 하는 문서 10종:

| 문서 | 조항 |
| --- | --- |
| CBS asset inventory | §3.1.1 |
| Topology diagrams | §3.1.2 |
| 보안능력 기술서 | §3.1.3 |
| 보안능력 시험 절차 | §3.1.4 |
| 보안 형상 지침 | §3.1.5 |
| 보안 개발 생명주기 문서 | §3.1.6 |
| CBS 유지보수·검증 계획 | §3.1.7 |
| 선주의 사고대응·복구계획 지원 정보 | §3.1.8 |
| 변경관리 계획 | §3.1.9 |
| 시험 보고서 | §3.1.10 |

[INFERENCE] 보안능력 30개는 **장비 공급자가 충족해야 하는 것**이다. [[Onboard System Index]]의 레거시 장비(자이로, 음향측심기, Modbus 밸브 컨트롤러 등)가 이를 자체적으로 갖추기 어려운 경우, §2.4 보완대책이나 §1.3의 IEC 61162-460 경로를 검토해야 한다. **어느 장비에 어느 능력이 결여되는지에 대한 매핑은 아직 작성되지 않았다.**

## Related Standards

- [[UR E26]] — 선박 단위. §5.1.5가 E27 보완대책 문서를 요구
- [[UR E22]] — 소프트웨어 기능성. 병행 적용
- [[UR E10]] — 하드웨어 환경 성능. 병행 적용
- [[IACS Rec 166]] · [[IACS Rec 190]]
- [[MSC-FAL.1-Circ.3]] — §4.2가 E27을 참조 표준으로 열거
- [[IEC 61162 Series]] — §1.3의 대체 경로

## Related Concepts

[[Cyber Resilience]] · [[Computer Based System]] · [[Essential Services]] · [[Compensating Countermeasure]] · [[Attack Surface]] · [[Untrusted Network]]

## Sources

- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf`
- 조항 위치: [[Regulation Locator]]

## Notes

[SOURCE] §1.4의 `Authentication` 정의는 `a claimed characteristic of an **identity**`인 반면, [[UR E26]] §2는 `of an **entity**`다. 문언이 다르다. → [[Term Locator#문서 간 정의 차이 (확인된 것)]]
