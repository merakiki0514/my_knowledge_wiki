---
type: concept
tags:
  - concept
---

# Compensating Countermeasure

레거시 장비가 규정 요건을 물리적으로 충족할 수 없을 때의 공식 경로.

## Definition

[SOURCE] IACS UR E26 §2 / UR E27 §1.4 — 정의문이 동일하다.

> An alternate solution to a countermeasure employed in lieu of or in addition to inherent security capabilities to satisfy one or more security requirements.

## Why it matters

[INFERENCE] UR E27 §4.1은 CBS가 갖춰야 할 보안능력 30개를 `shall`로 규정한다. 그런데 [[Onboard System Index]]에 있는 자이로컴퍼스, 음향측심기, 레거시 Modbus 기반 밸브 컨트롤러 같은 장비가 계정 관리·감사 로그·암호화 같은 능력을 자체적으로 갖추는 것은 현실적으로 어렵다.

보완대책은 이 간극을 다루는 **규정 내부의 공식 장치**다. 요건을 면제하는 것이 아니라 **다른 수단으로 같은 목적을 달성했음을 입증**하는 경로다.

## Key Characteristics

[SOURCE] UR E27 §2.4.1이 조건을 명시한다.

| 조건 | 내용 |
| --- | --- |
| 사용 방식 | 고유 보안능력을 **대체**하거나 **추가**하는 형태 모두 가능 |
| 충족 수준 | 원 요건의 **의도(intent)와 엄격성(rigor)**을 충족해야 한다 |
| 고려 사항 | 참조 표준, 그리고 각 요건과 표준의 관련 항목 간 차이를 고려 |
| 절차 | E27 §3.1.3의 원칙을 따를 것 |

[SOURCE] 문서화 요구:

- **UR E26 §5.1.5** — CBS가 UR E27 요건 대신 보완대책으로 승인된 경우, 다음을 명시한 문서를 제출한다.
  1. 해당 CBS
  2. **결여된 보안능력**
  3. 보완대책의 상세 기술
- **UR E27 §3.1.3** — 공급자가 시스템 문서에 보완대책을 기술할 것.

[INFERENCE] 즉 보완대책을 쓰려면 **어떤 능력이 없는지를 먼저 명시적으로 인정**해야 한다. 결여 사실을 문서에 남기는 구조다.

## Related Concepts

- [[Computer Based System]] — 보완대책이 적용되는 단위
- [[Essential Services]] — E27 §2.3의 가용성 제약이 보완대책을 필요하게 만드는 원인 중 하나
- [[System Category]] — 카테고리에 따라 요구 수준이 달라진다
- [[Security Zone]] — 대표적인 보완대책 형태 [INFERENCE]
- [[Cyber Resilience]]

## Applications

| 문서 | 위치 |
| --- | --- |
| UR E27 | §2.4 정의 및 조건 / §3.1.3 문서화 |
| UR E26 | §2 정의 / §5.1.5 설계 단계 제출 문서 |
| IACS Rec 166 | [확인 필요] — 대응 개념 존재 여부 미확인 |

[INFERENCE] 실무적으로 다음이 보완대책 후보가 될 수 있다. **원문에 열거된 목록이 아니라 추론이다.**

- 장비 자체에 접근통제가 없을 때 → 전용 [[Security Zone]] + 물리적 접근 통제
- 장비에 감사 로그가 없을 때 → 네트워크 측 모니터링 (E26 §4.3.1)
- 장비에 인증이 없을 때 → 상위 게이트웨이에서의 화이트리스트

## Limitations

- [SOURCE] `meet the intent and rigor of the original stated requirement` — 임의의 대체가 아니다. 원 요건과 동등한 수준임을 입증해야 한다.
- [확인 필요] "intent and rigor를 충족했다"를 선급이 어떤 기준으로 판단하는지는 E27 §2.4에 명시되어 있지 않다. §3.1.3의 원칙과 §3.1.4 시험 절차를 함께 봐야 한다.
- [확인 필요] 보완대책이 허용되지 않는 요건(즉 반드시 고유 능력으로 충족해야 하는 항목)이 있는지 확인하지 않았다.

## Sources

- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4, §2.3, §2.4, §3.1.3
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §5.1.5
- 조항 위치: [[Regulation Locator#13. 시스템 분류 · 보완대책]]

## Notes

[INFERENCE] 이 개념은 "규정 대 현장"의 간극을 정면으로 다루는 지점이다. E27 보안능력 30개 중 어떤 것이 [[Onboard System Index]]의 어떤 장비에서 충족 불가능하고, 무엇으로 대체할 것인가 — 이 매핑은 아직 작성되지 않았다.
