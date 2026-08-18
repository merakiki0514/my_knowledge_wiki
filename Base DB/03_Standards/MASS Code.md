---
type: standard
tags:
  - standard
  - imo
  - mass
---

# MASS Code

IMO **Maritime Autonomous Surface Ships Code**. 현재 **초안 단계**. 다른 자료와 주제 축이 다르다.

## Status

[SOURCE] `IMO-MASS-Code-개발현황-MSC-108-outcome.pdf` (IMO 사무국 Ricardo Batista, Maritime Safety Division 발표자료):

| 항목 | 내용 |
| --- | --- |
| 성격 | **Goal-based, non-mandatory Code** |
| 비강제 Code 채택 목표 | **MSC 110** (2025-05, 개정 로드맵 기준) |
| 강제 Code | SOLAS 개정 형태. **2032-01-01 발효 예정** (4년 SOLAS 개정 주기) |
| 적용 | 화물선 (고속선 제외) |
| 협력 | ILO, ISO, IHO, IALA, IMSO 등 |

[SOURCE] 배경 — MSC.1/Circ.1638 규제 범위 검토(RSE)가 MASS Code 초안 작성의 기반이 되었다. MSC 101(2019-06)이 MASS 시험 잠정 지침(MSC.1/Circ.1604)을 승인했다.

[SOURCE] MSC 107 — **운항 모드와 무관하게 선장이 항상 책임을 진다.**
[SOURCE] 미해결 사항 — 기국 밖의 ROC, MASS 선장·승무원 책임, 당국과의 통신.

## Overview

[SOURCE] `IMO-MSC-109-5-ISWG-MASS-3차-결과보고서(영문).pdf` = **MSC 109/5** (2024-09-16). 제3차 Intersessional MASS Working Group 보고서. 의장 Henrik Tunfors(스웨덴), 2024년 9월 9~13일 개최.

Annex에 **draft MASS Code 전문**이 실려 있다.

[SOURCE] Preamble — 기존 IMO 문서들은 선박에 **최소한의 승무원이 승선해 각종 임무를 수행한다는 전제** 위에 개발되어 왔다. 자동화 증가와 원격제어·자율운항 확대는 다른 접근을 요구하며, SOLAS 등에 담긴 선상 수동 개입·통제에 관한 통념의 조정이 필요하다.

## Structure — draft MASS Code

| Part | 장 |
| --- | --- |
| **Part 1** Introduction | 1 목적·원칙·목표 / 2 적용 / 3 코드 구조 / 4 용어·정의 |
| **Part 2** MASS 및 MASS 기능·원격운용 주요 원칙 | 5 증서·검사 / 6 승인절차 / **7 리스크 평가** / 8 운용 맥락 / **9 시스템 설계** / **10 소프트웨어 원칙** / 11 안전운항 관리 / **12 연결성(Connectivity)** / 13 무선통신 / 14 경보 관리 / 15 인적 요소 / 16 유지보수·수리 |
| **Part 3** 목표·기능요건·기대성능 | 17 항행 안전 / **18 원격 운용** / 19 구조·구획·복원성·수밀 / 20 소방 / 21 구명설비 / **22 해상보안 강화 특별조치** / 23 수색구조 / 24 화물 취급 / XX 인원 안전·쾌적 / 25 예인·계류 / 26 기관 설비 / 27 전기 설비 / 28 비상 대응 |

## Key Content — 사이버 관련

⚠️ [SOURCE] **§9.7 Security and Cybersecurity — 사이버보안 조항은 단 두 문장이다.**

> Security measures to protect the systems on the MASS and the ROC should be incorporated to prevent unauthorized access and cyber threats.

인접 조항: §9.8 데이터 관리·품질 / §9.9 상호운용성 / §9.10 시험·검증

[SOURCE] 그 밖의 사이버 언급:

- MSC-FAL.1/Circ.3/**Rev.2** 참조 (⚠️ 현행은 Rev.3)
- 위험요소로 `cyber attacks` 열거 (loss of function, component damage, fire, explosion, electric shock 등과 함께)
- 위협 요소에 `cyber-threats` 포함
- `EP 2 The communication should consider cybersecurity.`
- 보고 대상에 `a detected or suspected cybersecurity breach` 포함
- 안전 보호가 의존하는 `Cybersecurity related features` 언급

## Practical Implications

[INFERENCE] MASS Code의 사이버 조항은 **매우 얇다.** §9.7 두 문장이 전부이고, [[UR E26]] §4처럼 요건을 세분하지 않는다.

[INFERENCE] 무인·원격 운항에서 [[UR E26]] §4.4.2 *Local, independent and/or manual operation*(로컬·독립·수동 운전) 같은 요건이 어떻게 성립하는지는 **draft Code에서 다뤄지지 않은 것으로 보인다.** [확인 필요]

## Limitations

- **초안이다.** 조문 번호·문구가 확정되지 않았다. 원문에 `[ ]` 대괄호와 색상 음영으로 표시된 미확정 부분이 있다.
- [SOURCE] MSC 109/5 Annex 각주 — 색상 음영은 이번 회기 제출문서와 사무국 제안에서 비롯된 특정 주의사항 및 추가 수정 제안을 표시한다.
- ⚠️ MSC-FAL.1/Circ.3 **Rev.2**를 인용한다. 현행은 Rev.3(2025-04). → [[Database Inventory#3.2 인용되는 MSC-FAL 판본이 문서마다 다르다]]
- [확인 필요] MSC 110에서 실제로 채택되었는지, 채택본이 이 초안과 어떻게 다른지 확인하지 않았다. 보유 자료는 2024년 9월 시점이다.

## Related Standards

- [[MSC-FAL.1-Circ.3]] — draft가 Rev.2를 참조
- [[ISM Code]] · [[UR E26]] · [[UR E27]]

## Related Concepts

[[Cyber Risk Management]] · [[Untrusted Network]] · [[Essential Services]]

## Sources

- `Database/IMO-MSC-109-5-ISWG-MASS-3차-결과보고서(영문).pdf` (MSC 109/5, 2024-09-16)
- `Database/IMO-MASS-Code-개발현황-MSC-108-outcome.pdf`
- 조항 위치: [[Regulation Locator#16. MASS (자율운항선박)]]

## Notes

[INFERENCE] 이 두 문서는 나머지 자료와 주제 축이 다르다. 사이버보안이 주제가 아니라 **자율운항 규제**가 주제이고, 사이버는 그 안의 한 항목이다. 연구 목적에 따라 핵심이 될 수도, 곁가지가 될 수도 있다.
