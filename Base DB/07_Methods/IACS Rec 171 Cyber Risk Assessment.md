---
type: method
tags:
  - method
  - risk
---

# IACS Rec 171 Cyber Risk Assessment

`Database/` 안에서 **가장 구체적인 정량 리스크 평가 절차**. 수식과 임계값까지 명시되어 있다.

## Overview

[SOURCE] IACS Rec 171 §7 — 리스크 평가의 두 축은 **영향(impact)**과 **발생가능성(likelihood)**이며, 여기에 **UR E22 카테고리**를 결합해 시스템별 리스크 수준을 산출한다.

> Combination of impact, likelihood and UR E22 category will provide a Risk Level for a system/equipment.
> — Rec 171 §7

⚠️ [SOURCE] Rec 171 §2.1.2 — **이 방법의 사용은 의무가 아니다.** 다른 방법을 쓸 수 있다.

## Procedure

### Step 1. 평가 대상 확정

[SOURCE] Rec 171 §4 Table 1 — 시스템 레퍼런스 테이블. 기관 / 밸러스트·빌지 / 화물관리 / 무선통신 / 선교 / 안전 계통으로 그룹핑되어 있다.
§4는 이 표를 **해당 선박의 OT/IT 구성에 맞게 수정·보완해야 한다**고 명시한다.

→ 실제 선박 목록은 [[Onboard System Index]]

### Step 2. 영향 등급 (P1~P4)

[SOURCE] Rec 171 §7.1 — 가용성·기밀성·무결성·추적성 관점에서 위협의 결과를 본다.

| 등급 | 기준 (요약) |
| --- | --- |
| **P1 Negligible** | 시스템을 정지해도 유의미한 영향 없음. 인적·환경 영향 없음 |
| **P2 Acceptable** | 정지 시 서비스가 국부적으로 중단. 환경 영향은 통상 범위 내로 당국 신고 수준. 부상·치료로 인한 작업 차질 가능 |
| **P3 Moderate** | 활동 손실이 유의미. 제3자 조사 요청, 기밀정보 유출, 선주가 수용 불가한 재정 손실, 사기·금전 절취, 화물 절도, 평판 훼손, 제한적 환경 영향, **영구 장애로 이어지는 인적 피해** |
| **P4 High** | 물리적 시스템 손상, 표준 복구 절차로 회복 불가한 영구적 시스템 손실(예: 랜섬웨어), 규제기관 조사, 불법 거래, 주민 대피를 초래하는 심각한 오염, 장기적 경쟁력 상실, **사망에 이르는 인적 피해** |

⚠️ [SOURCE] §7.1 — Table 3은 **예시일 뿐이며 모든 경우의 진리로 간주될 수 없다.** 사용자가 자기 선박 환경에 맞는지 검증해야 한다.

### Step 3. 발생가능성 등급 (L1~L9)

[SOURCE] 6개 파라미터를 3단계로 결합한다.

```text
복잡도(CX) ─┐
            ├─→ 공격면(AS) ─┐
연결성(CY) ─┘                │
                             ├─→ 발생가능성(L)
사용자(US) ─┐                │
            ├─→ 인적요인(H) ─┘
공격자(AT) ─┘
```

**3-1. 복잡도 CX** (§7.2.1)

| 등급 | 정의 |
| --- | --- |
| CX1 | 저유지보수 시스템 — 운영에 설정 변경이 거의 불필요 (예: 워크스테이션) |
| CX2 | 상시 변경 시스템 — SW·설정·OS가 일 단위로 수정·갱신 (인증 서버, DBMS, 네트워크 장비, VM 모니터, 운항에 직접 영향을 주는 스마트 장비) |
| CX3 | 분산 시스템 — 원격·분산 아키텍처가 필요 (무인선박, 군집 로보틱스) |

**3-2. 연결성 CY** (§7.2.2) — CY1 격리 ~ CY5 개방(공중망 외부 링크 또는 특수 보호 미상)

⚠️ [SOURCE] §7.2.2 — 여기의 연결성 등급은 **IACS UR의 "connectivity grades"와 일치하지 않는다.**

**3-3. 공격면 AS** (§7.2.3) — CX × CY 조합표

| | CY1 | CY2 | CY3 | CY4 | CY5 |
| --- | --- | --- | --- | --- | --- |
| **CX3** | AS3 | AS3 | AS4 | AS4 | AS5 |
| **CX2** | AS2 | AS2 | AS3 | AS4 | AS5 |
| **CX1** | AS1 | AS2 | AS3 | AS4 | AS5 |

**3-4. 사용자 US** (§7.2.4) — 교육·인식 수준 + 물리 접근통제 + 논리 접근통제의 조합

| 등급 | 교육·인식 | 물리 접근 | 논리 접근 |
| --- | --- | --- | --- |
| US1 Aware | 인식·훈련 충분 | 물리적 잠금 + 승인 필요 | 전용 계정 + 개인 비밀번호 |
| US2 Controlled | 인식은 있으나 조치 이행 훈련 부족 | 물리적 잠금 + 승인 필요 | 직능별 공용 계정·공용 비밀번호 |
| US3 Accredited | 매우 부족 | 승인만 필요 | 없음 |
| US4 Any | 회사 차원의 교육·인식 계획 없음 | 없음 | 없음 |

**3-5. 공격자 AT** (§7.2.5)

| 등급 | 정의 |
| --- | --- |
| AT1 Unintentional | 승무원이 비의도적으로 반입한 비표적 악성코드 |
| AT2 Insider | 악의 없이 보안을 우회하려는 승무원 (장비 튜닝, 땜질, 윤리적 해커) |
| AT3 Standard | **기본값으로 적용** |
| AT4 Criminal | 시간·자금을 투입해 선사·선대·선박을 정찰하고 APT 설치를 위한 전용 시나리오 구성 |
| AT5 Cyber warfare | 국가 지원 공격. **군함에만 적용** |

**3-6. 인적요인 H** (§7.2.6) — US × AT 조합표

| | US1 | US2 | US3 | US4 |
| --- | --- | --- | --- | --- |
| **AT5** | H2 | H3 | H3 | H4 |
| **AT4** | H2 | H2 | H3 | H3 |
| **AT3** | H1 | H2 | H2 | H3 |
| **AT2** | H1 | H1 | H2 | H2 |
| **AT1** | H0 | H1 | H1 | H2 |

**3-7. 발생가능성 L** (§7.3) — AS × H 조합표

| | H0 | H1 | H2 | H3 | H4 |
| --- | --- | --- | --- | --- | --- |
| **AS5** | L5 | L6 | L7 | L8 | L9 |
| **AS4** | L4 | L5 | L6 | L7 | L8 |
| **AS3** | L3 | L4 | L5 | L6 | L7 |
| **AS2** | L2 | L3 | L4 | L5 | L6 |
| **AS1** | L1 | L2 | L3 | L4 | L5 |

[SOURCE] L1~L4 = Low / L5~L7 = Medium / L8 이상 = High

### Step 4. 리스크 수준 RL (§7.4)

[SOURCE] 수식이 명시되어 있다.

```text
RL = 2 × (Cat + L + P − 4)
```

- **Cat** — UR E22 정의에 따라 해당 시스템에 부여된 카테고리 번호 → [[System Category]]
- **L** — 발생가능성 등급
- **P** — 영향 등급

[SOURCE] 결과가 1 미만(음수 포함)이면 **RL = 1**로 둔다. `zero risk does not exist`.

### Step 5. 리스크 처리 (§7.5)

| RL | 처리 |
| --- | --- |
| RL < 4 | 선택(optional) |
| 4 ≤ RL ≤ 12 | 적절(appropriate) |
| RL > 12 | **필수(required)** |

[SOURCE] 처리 여부는 사이버보안 책임자와 그 상위 조직의 판단에 따른다.

### Step 6. 잔여 리스크 RRL (§7.6)

처리가 "appropriate" 또는 "required"인 경우 완화 조치를 적용해, 선주가 수용하는 수준(**Residual Risk Level**)까지 리스크를 낮춘다.

완화 조치는 §8에 있다 — §8.1 비기술적(인적 관련 포함), §8.2 기술적.

## Inputs

| 필요한 정보 | 어디서 |
| --- | --- |
| 대상 시스템 목록 | Rec 171 §4 Table 1 + [[Onboard System Index]] |
| UR E22 카테고리 | [[System Category]] — 선박별 판정 필요 |
| 연결성·인터페이스 | Rec 190 §6.1 컬럼 O·P·Q·R → [[Vessel Asset Inventory 작성법]] |
| 위협 목록 | Rec 171 §6, Table 2 (Appendix 1) |
| 승무원 교육 수준·접근통제 현황 | 현장 확인 |

## Limitations

- [SOURCE] §2.1.2 — 의무가 아니다. 다른 방법 사용 가능.
- [SOURCE] §7.1 — Table 3의 영향 예시는 검증 없이 그대로 쓸 수 없다.
- [SOURCE] §7.2.2 — 연결성 등급이 IACS UR의 동명 개념과 다르다. 혼용 금지.
- [SOURCE] §5 — 카테고리는 모든 운항 시나리오에 대한 리스크 평가에 따라 달라질 수 있다.
- [확인 필요] 이 방법론이 UR E26 §6(적용 제외 리스크 평가)에서 인정되는지 확인하지 않았다. → [[CBS Exclusion Risk Assessment]]
- [INFERENCE] US·AT 등급은 정성 판단이 크게 작용한다. 같은 선박이라도 평가자에 따라 결과가 달라질 수 있다.

## Related

- [[Cyber Risk Management]] — 상위 개념
- [[System Category]] — RL 수식의 입력값
- [[Attack Surface]] — AS 등급의 대상 개념
- [[Vessel Asset Inventory 작성법]] — 입력 데이터 확보
- [[CBS Exclusion Risk Assessment]] — E26의 별도 리스크 평가
- [[BIMCO Risk Assessment]] — 정성적 대안
- [[NIST RMF for OT]]

## Sources

- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` §2.1.2, §4, §5, §6, §7.1~§7.6, §8
- 조항 위치: [[Regulation Locator#11. 리스크 평가]]
