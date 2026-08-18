---
type: concept
tags:
  - concept
  - architecture
---

# Defence in Depth

표기 주의: IACS·IMO 문서는 `Defence`, NIST는 `Defense`를 쓴다.

## Definition

⚠️ **문서마다 정의가 다르다.** [SOURCE]

### 사람·기술·운영의 통합 전략 (E27 / NIST)

> Information Security strategy integrating people, technology, and operations capabilities to establish variable barriers across multiple layers and missions of the organization.
> — UR E27 §1.4

> Defense in depth is a multifaceted strategy that integrates people, technology, and operational capabilities to establish variable barriers across multiple layers and dimensions of the organization.
> — NIST SP 800-82r3 §5.1.2

두 문언이 거의 일치한다. [INFERENCE] IACS가 NIST 계열 정의를 채택한 것으로 보이나 확인하지 않았다. [확인 필요]

### 독립적 계층 접근법 (Rec 166)

IACS Rec 166 §4.1.16은 `An approach which uses layers of independent technical and...`으로 시작하는 별도 정의를 둔다. 강조점이 조직 전반이 아니라 **기술·절차 계층의 독립성**에 있다.

### Defence in breadth (Rec 166 §4.1.15)

[SOURCE] Rec 166은 `Defense in breadth`를 별도 용어로 정의한다 — 계획적·체계적 활동의 집합. BIMCO v5 §7.1도 `Defence in depth and in breadth`로 두 개념을 나란히 다룬다.

[확인 필요] depth와 breadth의 구분 기준을 원문에서 정확히 대조하지 않았다.

## Why it matters

[SOURCE] NIST SP 800-82r3 §5.1.2가 근거를 명시한다.

- 기본 개념은 **사이버보안 방어에 단일 실패 지점을 만들지 않는 것**, 그리고 **위협의 출처가 하나라고 가정하지 않는 것**이다.
- OT 환경에서 특히 유용한데, **핵심 기능에 방어 수단을 집중**시킬 수 있기 때문이다.
- ICS, SCADA, IoT, IIoT, 혼합 환경까지 유연하게 적용된다.
- 효과를 내려면 **사람·프로세스·기술의 통합**이 필요하다.

[INFERENCE] 이 원칙은 [[Cyber Resilience]] 정의와 같은 전제 위에 있다. 침해를 막을 수 있다고 보지 않기 때문에 계층을 둔다. E26 §4.2.1.3의 `breaching that perimeter is always possible`이 같은 전제다.

## Key Characteristics

[SOURCE] NIST SP 800-82r3 §5.2가 제시하는 **심층방어 아키텍처 5계층**:

| 계층 | 내용 | 조항 |
| --- | --- | --- |
| Layer 1 | Security Management | §5.2.1 |
| Layer 2 | Physical Security | §5.2.2 |
| Layer 3 | Network Security | §5.2.3 |
| Layer 4 | Hardware Security | §5.2.4 |
| Layer 5 | Software Security | §5.2.5 |

## Related Concepts

- [[Security Zone]] — 네트워크 계층에서 이 원칙을 구현하는 수단
- [[Cyber Resilience]] — 같은 전제를 공유하는 상위 개념
- [[Attack Surface]] — 계층화가 줄이려는 대상
- [[Untrusted Network]]
- [[IT and OT]] — OT에 적용할 때의 특수성
- [[Cyber Risk Management]]

## Applications

| 문서 | 위치 |
| --- | --- |
| **NIST SP 800-82r3** | §5.1.2 전략 / §5.2.1~§5.2.5 5계층 / §5.1.1 전략 선택의 영향 |
| **BIMCO v5** | §7.1 Defence in depth and in breadth → §7.2 기술적 조치 / §7.3 절차적 조치 |
| **UR E26** | 용어 자체는 정의하지 않으나 §4.2.1~§4.2.7이 계층 구조를 이룬다 [INFERENCE] |
| **UR E27** | §1.4 정의 |
| **IACS Rec 166** | §4.1.15 breadth / §4.1.16 depth |

## Limitations

- [SOURCE] UR E26 §2의 정의 목록에는 이 용어가 **없다.** E26은 심층방어를 명시적 요건으로 두지 않는다.
- [확인 필요] Rec 166의 정의와 E27/NIST 정의 중 어느 쪽을 기준으로 삼을지는 문맥에 따라 달라진다. 인용 시 출처를 반드시 명시할 것.
- [INFERENCE] "계층을 많이 두면 안전하다"로 읽히기 쉬우나, NIST §5.1.2는 사람·프로세스·기술의 **통합**을 조건으로 단다. 기술 계층만 쌓는 것은 이 정의를 만족하지 않는다.

## Sources

- `Database/NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` §5.1.2, §5.2.1~§5.2.5
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.15, §4.1.16
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §7.1, §7.2, §7.3
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §4.2.1.3

## Notes

파생 문서 `해양 사이버보안 IT-OT 모니터링 가이드` §5.1.1에도 6계층 심층방어 예시가 있으나, NIST의 5계층과 구성이 다르고 출처가 확인되지 않는다. 근거로 쓰지 않는다.
