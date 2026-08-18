---
type: method
tags:
  - method
  - framework
---

# CSF Profile and Tier

NIST CSF 2.0 §3 — 현재 상태와 목표 상태를 비교해 격차를 도출하는 방법.

## Overview

[SOURCE] NIST CSF 2.0 §2 — CSF Core는 **6개 기능**으로 구성된다.

| 기능 | 정의 (§2) |
| --- | --- |
| **GOVERN (GV)** | 조직의 사이버보안 리스크 관리 전략·기대·정책이 수립·전달·감시된다 |
| **IDENTIFY (ID)** | 조직의 현재 사이버보안 리스크가 이해된다 |
| **PROTECT (PR)** | 조직의 사이버보안 리스크를 관리하기 위한 안전장치가 사용된다 |
| **DETECT (DE)** | 가능한 사이버보안 공격과 침해가 발견·분석된다 |
| **RESPOND (RS)** | 탐지된 사이버보안 사고에 대한 조치가 취해진다 |
| **RECOVER (RC)** | 사이버보안 사고의 영향을 받은 자산과 운영이 복구된다 |

[SOURCE] CSF는 **결과(outcome)의 분류체계**를 제공할 뿐, 그 결과를 어떻게 달성할지는 규정하지 않는다.

## Procedure — Organizational Profile 작성 (§3.1)

[SOURCE] CSF 2.0 §3.1 — 5단계.

| 단계 | 내용 |
| --- | --- |
| 1. **Scope** | 조직 프로파일의 범위를 정한다. 상위 수준의 사실과 가정을 문서화한다 |
| 2. **Gather** | 프로파일 작성에 필요한 정보를 수집한다 |
| 3. **Create** | 조직 프로파일을 작성한다. 프로파일에 담을 정보 유형을 결정한다 |
| 4. **Analyze gaps** | Current Profile과 Target Profile 간 격차를 분석하고 **실행 계획을 수립**한다 |
| 5. **Implement** | 실행 계획을 이행하고 조직 프로파일을 갱신한다 |

[SOURCE] 두 프로파일의 정의:

- **Current Profile** — 조직이 **현재 달성하고 있는** Core 결과
- **Target Profile** — 조직이 선정한 **달성하고자 하는** 결과

## CSF Tier (§3.2)

[SOURCE] CSF 2.0 §3.2에 계층(Tier) 개념이 있다. 세부 내용은 원문 참조.

## 해양 규정과의 연결

[SOURCE] **IMO MSC-FAL.1/Circ.3/Rev.3 §4.3.3이 NIST CSF 2.0을 산업 모범사례로 명시 참조한다.**

[SOURCE] MSC-FAL Rev.3 §3.5의 기능요소 6개가 CSF 2.0의 6개 기능과 같은 구성이며, Govern의 문언이 거의 일치한다.

| CSF 2.0 §2 | MSC-FAL Rev.3 §3.5 |
| --- | --- |
| `risk management strategy, expectations, and policies are established, communicated, and monitored` | `Establish and monitor risk management strategy, expectations and policies` |

[INFERENCE] 따라서 CSF 2.0 프로파일 방식으로 현재/목표 상태를 정리하면 MSC-FAL Rev.3 §3.5 대응 자료로 쓸 수 있다. 다만 IMO가 프로파일 형식을 요구하는 것은 아니다.

⚠️ [SOURCE] **IACS UR E26·Rec 166·BIMCO v5는 5개 구조**이므로 CSF 2.0과 기능이 1:1 대응하지 않는다. → [[Database Inventory#3.1 기능요소 개수: IMO Rev.3(6개) vs IACS·BIMCO(5개)]]

## Limitations

- [SOURCE] CSF는 결과의 분류체계이며 달성 방법을 규정하지 않는다. 구체적 통제는 외부 자료(Informative References, §4)에 연결된다.
- [SOURCE] MSC-FAL §4.4 — 어떤 지침·표준이든 **최신판을 참조**해야 한다.
- [확인 필요] CSF 2.0의 Category·Subcategory 전체 목록은 이 문서에 옮기지 않았다. 원문 Core 표를 볼 것.
- [INFERENCE] CSF는 일반 조직용이며 선박 환경 특화 내용이 없다. OT 특화는 [[NIST RMF for OT]], 해양 특화는 [[IACS Rec 171 Cyber Risk Assessment]]를 함께 볼 것.

## Related

- [[Cyber Risk Management]] — MSC-FAL 기능요소 6개
- [[NIST RMF for OT]] — ⚠️ CSF **1.1** 기준
- [[IACS Rec 171 Cyber Risk Assessment]]
- [[BIMCO Risk Assessment]]

## Sources

- `Database/NIST-CSWP-29-Cybersecurity-Framework-2.0-Feb-2024.pdf` §2, §3.1, §3.2, §4, §5
- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §3.5, §4.3, §4.4
- 조항 위치: [[Regulation Locator#19. NIST CSF 2.0]]
