---
type: concept
tags:
  - concept
  - cybersecurity
---

# Cyber Resilience

## Definition

[SOURCE] IACS UR E26 §2 / UR E27 §1.4 — 두 문서의 정의가 거의 동일하다.

> The capability to reduce the occurrence and mitigating the effects of cyber incidents arising from the disruption or impairment of operational technology (OT) used for the safe operation of a ship
> — UR E26 §2

- E26은 `cyber incidents`, E27은 `incidents`로 표기가 다르나 나머지 문언은 같다.
- IACS Rec 166 §4.1.10에도 정의가 있다. 문언 대조는 [확인 필요]

## Why it matters

[SOURCE] 이 정의의 핵심은 **"막는 것"이 아니라 "줄이고 완화하는 것"**이다. 침해가 발생하지 않는 상태를 전제하지 않는다.

E26 §4.2.1.3의 서술이 이 전제를 명시한다 — 방화벽·IDS로 경계를 보호해도 `breaching that perimeter is always possible`. 그래서 [[Security Zone]] 분할로 공격자의 횡적 이동을 어렵게 만드는 구조를 요구한다.

[INFERENCE] 따라서 E26의 요건 체계가 `Identify → Protect → Detect → Respond → Recover` 5단계로 짜인 것은 이 정의의 직접적 귀결로 볼 수 있다. 방어(Protect)만으로 목표를 달성할 수 없다고 전제하기 때문에 탐지·대응·복구가 동등한 비중으로 들어간다.

## Key Characteristics

| 특징 | 근거 |
| --- | --- |
| 대상이 **OT**로 한정된다 | E26 §2 — `operational technology (OT) used for the safe operation of a ship` |
| 목표가 **인명·선박 안전·환경**이다 | E26 §2 — `dangerous situations for human safety, safety of the vessel and/or threat to the environment` |
| 기밀성이 아니라 **안전**이 기준이다 | [INFERENCE] 정의문에 정보 유출·기밀성 언급이 없다 |
| 시스템 고장은 제외된다 | E27 §1.4 [[Cyber Incident]] — `Cyber incidents do not include system failures` |

## Related Concepts

- [[Cyber Incident]] — 이 정의가 줄이고자 하는 대상
- [[IT and OT]] — 정의가 OT로 한정되는 이유
- [[Essential Services]] — 무엇이 "선박의 안전한 운항"인가
- [[Security Zone]] — 침해를 전제한 구조적 대응
- [[Defence in Depth]] — 동일 전제에서 나오는 설계 원칙
- [[Compensating Countermeasure]] — 요건 충족이 불가능할 때의 경로
- [[Cyber Risk Management]] — 상위 관리 개념

## Applications

| 문서 | 적용 방식 |
| --- | --- |
| UR E26 | **선박 단위** 사이버 복원성 요건. §4.1~§4.5 |
| UR E27 | **시스템·장비 단위** 요건. §4.1의 보안능력 30개 |
| IACS Rec 166 | 비강제 기술 권고. E26과 충돌 시 E26 우선 (E26 §1.3.4) |

## Limitations

- [SOURCE] E26 §1.3.2의 적용 대상 시스템에 한정된다. 범위 밖 시스템은 [[Untrusted Network]]로 취급된다.
- [확인 필요] 정의문의 `reduce the occurrence`가 어느 수준까지를 요구하는지는 정의만으로 판단할 수 없다. 실제 기준은 §4의 개별 요건과 §5의 입증 절차에 있다.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §4.2.1.3
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.10
- 조항 위치: [[Term Locator]]

## Notes

E26 2022년판(철회)과 Rev.1의 정의문이 같은지는 대조하지 않았다. [확인 필요]
