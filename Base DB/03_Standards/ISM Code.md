---
type: standard
tags:
  - standard
  - imo
---

# ISM Code

International Safety Management Code. **IMO가 사이버 리스크를 다루기로 한 그릇.**

⚠️ **본체(Resolution A.741(18))가 `Database/`에 없다.** 보유본은 개정 결의 5건과 이행 지침 1건뿐이다.

## 왜 중요한가

[SOURCE] [[IACS Rec 171]] §1 Foreword

> IMO has decided that cyber security shall be handled in accordance with the existing objectives and functional requirements of the ISM Code. Companies (DOC holders) should use their existing Safety Management Systems (and SMS measures) to assess risks and implement safeguards and otherwise handle cyber security.

[INFERENCE] 즉 해양 사이버보안은 **새로운 별도 체계가 아니라 기존 SMS에 통합되는 것**이 IMO의 방향이다. 이것이 [[IACS Rec 171]]과 [[BIMCO Guidelines on Cyber Security Onboard Ships]] ANNEX 2가 존재하는 이유다.

[SOURCE] ISM Code는 **SOLAS 제IX장에 따라 강제**가 되었다. (개정 결의들의 전문에서 반복 확인)

## 보유 자료

### 개정 결의 5건 [SOURCE]

| 결의 | 채택일 | 개정 대상 조항 (확인된 범위) |
| --- | --- | --- |
| **MSC.104(73)** | 2000-12-05 | 증서 유효기간·중간증서·증서 양식 관련 (전문에 명시) |
| **MSC.179(79)** | 2004-12-10 | [확인 필요] |
| **MSC.195(80)** | 2005-05-20 | [확인 필요] |
| **MSC.273(85)** | 2008-12-04 | §1.1.10, §1.2.2, §5.1.5, §7, §8.1, §9.2, §10.3, §12.1, §13.11, §14.4.3 |
| **MSC.353(92)** | 2013-06-21 | §1.1.10, §1.2.3.2, §3, §4, §6.2, §8, §9, §11, §12.1, §12.2 |

⚠️ **개정 결의는 "무엇을 무엇으로 바꾼다"만 담는다.** 원 조문 없이는 개정 전후를 재구성할 수 없다.

[SOURCE] MSC.104(73)의 전문 — A.741(18)로 총회가 ISM Code를 채택했고, A.788(19)로 주관청의 이행 지침을 채택했음을 상기한다. 증서 유효기간·중간증서·증서 양식 관련 지침 조항을 ISM Code에 반영할 필요를 인식해 개정했다.

### 이행 지침 [SOURCE]

**Resolution A.1118(30)** (2017-12-06 채택, A 30/Res.1118) — *Revised Guidelines on the implementation of the ISM Code by Administrations*. A.788(19)를 승계하며 A.1071(28)을 폐지한다.

| 절 | 내용 |
| --- | --- |
| 1 | Introduction (1.1 ISM Code, 1.2 강제 적용, 1.3 검증·인증 책임) |
| 2 | Scope and application (2.1 정의, 2.2 범위) |
| 3 | **ISM Code 준수 검증** (3.1 일반, 3.2 SMS의 일반 안전목표 충족 능력) |
| **4** | **인증·검증 절차** (4.2 잠정 / 4.3 최초 / 4.4 DOC 연차 / 4.5 SMC 중간 / 4.6 갱신 / 4.7 추가 / 4.8 안전관리 감사 / 4.9~4.17 신청·준비·실행·보고·시정조치·책임) |

[SOURCE] A.1118(30)은 ISM Code를 **81회 인용**한다.

### SOLAS

⚠️ `Database/SOLAS-1974-Original-Convention-Text-UNTS-Vol.1184.pdf`는 **1974년 원 협약문**(UN 조약집 Vol.1184, 1980-06-30 등록)이다.

[SOURCE] 파일 전체에서 `safety management`, `chapter IX` 검색 결과 **0건**. Chapter IX(ISM Code 강제화)는 1994년 개정으로 추가된 것이라 이 판본에 없다.

→ **ISM·사이버 목적으로 사용할 수 없다. 통합본(consolidated edition)이 필요하다.**

## 없어도 되는가 — 우회 경로

[INFERENCE] 목적이 **사이버 리스크의 SMS 통합**이라면 보유 자료로 대부분 커버된다.

| 필요한 것 | 대체 근거 |
| --- | --- |
| SMS에 사이버 리스크를 넣는 방법론 | [[IACS Rec 171]] §7 평가, §8 완화 → [[IACS Rec 171 Cyber Risk Assessment]] |
| ISM 기능요소 ↔ 사이버 조치 매핑 | [[BIMCO Guidelines on Cyber Security Onboard Ships]] ANNEX 2 |
| ISM §6.2·6.3·6.5 인식·교육 요구 | [[IACS Rec 171]] §8.1.1이 해당 조항을 직접 인용 |
| 심사·인증 절차 | A.1118(30) §3, §4 |
| IMO의 사이버 리스크 관리 요구 | [[MSC-FAL.1-Circ.3]] §3.5 |

**부족해질 때만 구매를 검토한다.** ISM Code 본문은 IMO 유료 간행물이다.

## Limitations

- 본체 부재로 조문 직접 인용 불가.
- [확인 필요] MSC.179(79)·MSC.195(80)의 개정 대상 조항을 확인하지 않았다.
- [확인 필요] 개정 결의 5건이 ISM Code의 모든 개정을 망라하는지 확인하지 않았다.
- SOLAS Chapter V(항해 안전)도 현행 개정판이 아니다.

## Related Standards

- [[IACS Rec 171]] — SMS 통합 방법론
- [[BIMCO Guidelines on Cyber Security Onboard Ships]] — ANNEX 2
- [[MSC-FAL.1-Circ.3]] — IMO 사이버 지침
- [[MASS Code]] — 자율운항 맥락

## Related Concepts

[[Cyber Risk Management]]

## Sources

- `Database/MSC.104(73)-ISM-Code-Amendments-2000.pdf` ~ `MSC.353(92)-ISM-Code-Amendments-2013.pdf` (5건)
- `Database/A.1118(30)-Revised-Guidelines-ISM-Code-Implementation-2017.pdf`
- `Database/SOLAS-1974-Original-Convention-Text-UNTS-Vol.1184.pdf` (원 협약문, 제약 있음)
- 조항 위치: [[Regulation Locator#20. ISM Code · SOLAS]]

## Notes

MSC.104(73) 파일은 **스캔본이라 텍스트 레이어가 없다.** 검색이 되지 않으므로 내용 확인 시 페이지를 이미지로 봐야 한다.
