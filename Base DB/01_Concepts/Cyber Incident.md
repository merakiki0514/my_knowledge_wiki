---
type: concept
tags:
  - concept
---

# Cyber Incident

## Definition

⚠️ **세 문서의 정의 범위가 다르다.** 특히 "공격에서 비롯된 것인가"와 "연쇄 사건을 포함하는가"에서 갈린다. [SOURCE]

### IACS UR E26 §2 — 공격적 기동에서 비롯된 사건

> An event resulting from any offensive manoeuvre, either intentional or unintentional, that targets or affects one or more CBS onboard, which actually or potentially results in adverse consequences...

### IACS UR E27 §1.4 — 거의 동일, 표현만 차이

E26의 `offensive manoeuvre`가 E27에서는 `offensive cyber manoeuvre`다. E27 §1.4는 `Offensive cyber manoeuvre`를 별도 용어로도 정의한다 — OT·IT 시스템의 거부·저하·중단·파괴·조작을 초래하는 행위.

### IMO MSC-FAL.1/Circ.3/Rev.3 §2.1 — 공격 전제 없음, 연쇄 포함

> An occurrence **or a sequence of occurrences**, which actually or potentially results in adverse consequences to a CBS or to the information that they process, store or transmit, and which may require a response action to mitigate the consequences.

[SOURCE] 차이 정리:

| 항목 | E26 / E27 | MSC-FAL |
| --- | --- | --- |
| 공격 기인 전제 | **있음** (`offensive manoeuvre`) | **없음** |
| 연쇄 사건 | 명시 없음 | `or a sequence of occurrences` 명시 |
| 의도성 | 의도적·비의도적 모두 포함 | 언급 없음 |

IACS Rec 166 §4.1.9에도 정의가 있다. 문언 대조는 [확인 필요]

## Why it matters

[SOURCE] **E26·E27은 시스템 고장을 명시적으로 제외한다.**

> Cyber incidents do not include system failures.
> — UR E26 §2 (E27 §1.4 동일)

[INFERENCE] 이 한 문장이 실무에서 경계선이 된다. 기관 제어 시스템이 멈췄을 때, 그것이 사이버 사고인지 단순 고장인지에 따라 [[Cyber Resilience]] 요건의 대응·복구 절차가 발동하는지가 갈린다. 다만 **초기에는 구분이 불가능한 경우가 많다.** MSC-FAL 정의가 공격 전제를 두지 않은 것은 이 점과 관련이 있어 보이나, 확인하지 않았다. [확인 필요]

## Key Characteristics

[SOURCE] E26 §2가 열거하는 사이버 사고의 유형:

- 인가되지 않은 접근
- 오용(misuse)
- 변조(modification)
- 파괴(destruction)
- 부적절한 공개(improper disclosure)

대상은 선내 CBS에서 생성·보관·사용되는 정보, 그리고 이들 시스템을 연결하는 네트워크에서 전송되는 정보다.

## Related Concepts

- [[Cyber Resilience]] — 이 사고의 발생과 영향을 줄이는 능력
- [[Computer Based System]] — 사고의 대상
- [[Cyber Risk Management]] — 상위 관리 개념
- [[Attack Surface]] — 사고가 발생하는 경로
- [[Essential Services]] — 사고의 영향이 안전으로 이어지는 지점

## Applications

| 문서 | 위치 |
| --- | --- |
| UR E26 | §4.4.1 사고 대응 계획 / §4.4.3 네트워크 격리 / §4.4.4 최소 위험 상태 fallback / §4.5 복구 |
| UR E27 | §3.1.8 사고 대응·복구 지원 정보 (제조사 → 선주) |
| MSC-FAL | §3.5.5 Respond (보고·기록·훈련) / §3.5.6.3 **근본원인 분석** |
| BIMCO v5 | §10.2 사고 대응 4단계 / §10.5 조사 / §10.7 보고 |
| IEC 62443-2-1 | §12.2 이벤트·사고 관리 (조항 참조만) |
| NIST SP 800-82r3 | §3.3.8 사고 대응 능력 개발 |

## Limitations

- [확인 필요] `offensive manoeuvre`에 "비의도적(unintentional)"이 포함된다는 E26 문언은 다소 모순적으로 읽힌다. 비의도적 공격 기동이 무엇을 가리키는지 원문만으로는 판단되지 않는다.
- [확인 필요] "system failure는 제외"와 "unintentional은 포함" 사이의 경계가 원문에 명확히 그어져 있지 않다.
- [SOURCE] MSC-FAL 정의를 쓰면 범위가 넓어지고, E26/E27 정의를 쓰면 좁아진다. 문서를 교차 인용할 때 주의할 것.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §4.4, §4.5
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4, §3.1.8
- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §2.1, §3.5.5, §3.5.6
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.9
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §10

## Notes

정의 차이는 [[Term Locator#문서 간 정의 차이 (확인된 것)]]에도 기록되어 있다.
