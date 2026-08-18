---
type: standard
tags:
  - standard
  - nist
  - framework
---

# NIST CSF 2.0

NIST Cybersecurity Framework 2.0 — NIST CSWP 29, **2024년 2월 26일**. 무료 공개.

## Version

[SOURCE] 32쪽. DOI `10.6028/NIST.CSWP.29`.

⚠️ **CSF 1.1과 구조가 다르다.** 1.1은 기능 5개이며 거버넌스가 `ID.GV`(Identify 하위 카테고리)였다. 2.0은 이를 **`GOVERN` 최상위 기능으로 승격**했다.

→ [[NIST SP 800-82r3]]는 2023년 9월 발행이므로 **CSF 1.1 구조를 쓴다.**

## Overview

[SOURCE] Abstract — CSF 2.0은 산업·정부기관·기타 조직이 사이버보안 리스크를 관리하도록 지침을 제공한다. 규모·부문·성숙도와 무관하게 어떤 조직도 쓸 수 있는 **고위 수준 사이버보안 결과의 분류체계(taxonomy)**를 제공한다.

⚠️ [SOURCE] **CSF는 결과를 어떻게 달성할지 규정하지 않는다.** 대신 그 결과 달성에 쓸 수 있는 관행·통제에 관한 추가 지침을 제공하는 온라인 자료로 연결한다.

## Structure

| 절 | 내용 |
| --- | --- |
| 1 | Cybersecurity Framework (CSF) Overview |
| **2** | **Introduction to the CSF Core — 6개 Function** |
| 3 | Introduction to CSF Profiles and Tiers (3.1 Profiles, 3.2 Tiers) |
| 4 | CSF를 보완하는 온라인 자료 |
| 5 | 리스크 커뮤니케이션 및 통합 개선 (5.1 소통, 5.2 타 리스크관리 프로그램과의 통합) |

## Key Content

### §2 Core — 6개 Function

[SOURCE]

| Function | 정의 |
| --- | --- |
| **GOVERN (GV)** | 조직의 사이버보안 리스크 관리 전략·기대·정책이 수립·전달·감시된다 |
| **IDENTIFY (ID)** | 조직의 현재 사이버보안 리스크가 이해된다 |
| **PROTECT (PR)** | 조직의 사이버보안 리스크를 관리하기 위한 안전장치가 사용된다 |
| **DETECT (DE)** | 가능한 사이버보안 공격과 침해가 발견·분석된다 |
| **RESPOND (RS)** | 탐지된 사이버보안 사고에 대한 조치가 취해진다 |
| **RECOVER (RC)** | 사이버보안 사고의 영향을 받은 자산과 운영이 복구된다 |

### §3.1 Organizational Profile

[SOURCE] Current Profile은 조직이 **현재 달성하고 있는** Core 결과를, Target Profile은 **달성하고자 선정한** 결과를 명시한다.

작성 5단계: Scope → Gather → Create → **Analyze gaps** → Implement
→ **[[CSF Profile and Tier]]**

## Practical Implications — 해양 규정과의 연결

[SOURCE] **IMO MSC-FAL.1/Circ.3/Rev.3 §4.3.3이 "the NIST 2.0 Framework"를 산업 모범사례로 명시 참조한다.**

[SOURCE] MSC-FAL Rev.3 §3.5의 기능요소 6개가 CSF 2.0과 같은 구성이며, Govern 문언이 거의 일치한다.

| CSF 2.0 §2 | MSC-FAL Rev.3 §3.5.1 |
| --- | --- |
| `risk management strategy, expectations, and policies are established, communicated, and monitored` | `Establish and monitor risk management strategy, expectations and policies` |

⚠️ [SOURCE] 반면 [[UR E26]]·[[IACS Rec 166]]·[[BIMCO Guidelines on Cyber Security Onboard Ships]]는 **5개 구조**이므로 기능이 1:1 대응하지 않는다.

→ [[Database Inventory#3.1 기능요소 개수: IMO Rev.3(6개) vs IACS·BIMCO(5개)]]

## Limitations

- [SOURCE] 결과의 분류체계일 뿐 달성 방법을 규정하지 않는다.
- [INFERENCE] 일반 조직용이며 **선박·OT 특화 내용이 없다.** OT 특화는 [[NIST SP 800-82r3]], 해양 특화는 [[IACS Rec 171]]을 함께 볼 것.

## Related Standards

- [[MSC-FAL.1-Circ.3]] — §4.3.3이 참조
- [[NIST SP 800-82r3]] — ⚠️ CSF **1.1** 기준
- [[UR E26]] · [[IACS Rec 166]] · [[BIMCO Guidelines on Cyber Security Onboard Ships]] — 5개 구조

## Related Methods / Concepts

[[CSF Profile and Tier]] · [[Cyber Risk Management]]

## Sources

- `Database/NIST-CSWP-29-Cybersecurity-Framework-2.0-Feb-2024.pdf`
- 조항 위치: [[Regulation Locator#19. NIST CSF 2.0]]
