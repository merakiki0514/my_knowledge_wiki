---
type: standard
tags:
  - standard
  - iacs
  - recommendation
---

# IACS Rec 166

IACS Recommendation No.166 — **Recommendation on Cyber Resilience**. 비강제 기술 권고.

## Version

| 판본 | 발행 |
| --- | --- |
| No.166 | 2020-04 |
| Corr.1 | 2020-07 |
| **Corr.2** | **2022-04** (보유본) |

## Overview

[SOURCE] §1.1.5 — IMO Resolution MSC.428(98) (2017-06)을 지원하고자 한다.
[SOURCE] §1.1.6 — **IACS UR E26 "Cyber resilience of ships"를 지원하고자 한다.**

[SOURCE] §1.1.2 — 여기서 resilience는 승무원과 선박에게 어떤 특성을 제공하는 것으로 정의된다.

⚠️ **우선순위** [SOURCE] [[UR E26]] §1.3.4:

> For ships to which this UR applies as mandatory instrument, when both this UR and Recommendation 166 are used, should any difference in requirements addressing the same topic be found between the two instruments, **the requirements in this UR shall prevail.**

## Scope

[SOURCE] §2.2 — 선내 OT 시스템, 그리고 그 운영에 영향을 줄 수 있는 방식으로 선내 OT에 연결된 기타 시스템을 다룬다(리스크 평가로 식별). 또한 SOLAS·MARPOL 요구가 식별하는, 인명 안전·선박 안전·해양환경에 영향을 줄 수 있는 장비를 다룬다.

[SOURCE] §2.3 — **발행 이후 건조계약** 선박을 대상으로 하며, 발행 이전 취항 선박에는 참고로 사용할 수 있다.
[SOURCE] §2.4 — 기술적 설계·건조·시험 측면을 다룬다.
[SOURCE] §2.5 — Annex A의 운영·관리 항목은 별도 성격이다.

## Structure

[SOURCE] §1.2.1 — 8개 절 + 3개 부속서(Appendix) + 1개 Annex.

| 절 | 내용 |
| --- | --- |
| 1 | Introduction (1.3 사용법) |
| 2 | Scope |
| 3 | Reference Guidelines and Standards (§3.1 참조 표준 목록) |
| **4** | **Terms and definitions (§4.1 — 60개 용어. `Database/` 내 최대 용어집)** |
| 5 | Goals for design and construction (§5.1 목표, §5.2 Sub-goals) |
| 6 | Functional Requirements (§6.2 Identify ~ §6.6 Recover) |
| **7** | **Technical Considerations** |
| **8** | **Verification Testing** |
| Appendix A | 표준 상세 목록 |
| Appendix B | 권고에서 참조하는 문서 |
| Appendix C | Sub-goal ↔ 기술·검증 항목 매핑 |
| Annex A | 운영 측면 지침 |

## Key Requirements

### §7 기술 고려사항 ↔ §8 검증 시험 — 같은 주제로 짝을 이룬다

| 주제 | 기술 (§7) | 검증 (§8) |
| --- | --- | --- |
| 자산 식별 | §7.1 | §8.1 |
| 통신·인터페이스 | §7.2 | §8.2 |
| 네트워크 | §7.3 | §8.3 |
| CBS 물리적 접근통제 | §7.4 | §8.4 |
| 소프트웨어 보증 | §7.5 | §8.5 |
| 원격 접속 (선외 위치로부터) | §7.6 | §8.6 |
| **데이터 품질** | §7.7 | §8.7 |
| 시스템 복구 | §7.8 | §8.8 |

[INFERENCE] **Data Quality(§7.7)는 [[UR E26]]에 대응 요건이 없는 Rec 166 고유 항목으로 보인다.** §4.1.13~§4.1.14에 `Data Quality`, `Data Provider` 정의도 별도로 있다. [확인 필요]

### §6 기능 요구

[SOURCE] §6.2 Identify(I) / §6.3 Protect(P) / §6.4 Detect(D) / §6.5 Respond(R) / §6.6 Recover(RC) — **5개 구조. Govern 없음.**

## Practical Implications

[SOURCE] §1.3.1 — 이 권고는 **프로그램 개발을 위한 로드맵**으로 볼 수 있다.
[SOURCE] §1.3.5 — §8은 인도 시점에 검토·입회·확인할 요소를 식별한다.
[SOURCE] Appendix B에 설계자·OEM별 제출 문서 목록이 있다 (설계 철학서, 네트워크 논리도, 소프트웨어 인벤토리, 리스크 평가, 네트워크 설계 FMEA, 설치 계획, 네트워크 보호수단, 보안 경계, 소프트웨어 유지보수 계획, 데이터 보안·분류·저장 등).

[INFERENCE] E26이 강제 요건의 **뼈대**라면, Rec 166은 그것을 어떻게 구현·검증할지에 대한 **살**에 가깝다. 다만 E26과 다르면 E26이 우선한다.

## Related Standards

- [[UR E26]] — §1.3.4가 우선순위 명시. Rec 166은 E26을 지원
- [[UR E27]] · [[UR E22]]
- [[MSC-FAL.1-Circ.3]] — §4.3.2가 Rec 166을 산업 모범사례로 열거
- [[IACS Rec 171]] · [[IACS Rec 190]]

## Related Concepts

[[Cyber Resilience]] · [[Attack Surface]] · [[Defence in Depth]] · [[Security Zone]] · [[Essential Services]]

## Sources

- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf`
- 조항 위치: [[Regulation Locator]]

## Notes

⚠️ **정의가 [[UR E26]]·[[UR E27]]과 다른 용어가 있다.** [[Attack Surface]](§4.1.2)는 범위가 좁고, [[Defence in Depth]](§4.1.16)는 강조점이 다르다. → [[Term Locator#문서 간 정의 차이 (확인된 것)]]
