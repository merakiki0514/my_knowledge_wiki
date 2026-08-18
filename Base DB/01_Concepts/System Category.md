---
type: concept
tags:
  - concept
---

# System Category

Cat I / II / III. **정의 원문은 UR E22 §3.1이다.** E26·E27·Rec 166·Rec 171은 이를 참조한다.

## Definition

[SOURCE] IACS UR E22 §3.1 Table 3 — 분류 기준은 **시스템이 담당하는 기능이 고장났을 때 결과의 심각도**다.

| Cat | 고장의 영향 | 전형적 기능 |
| --- | --- | --- |
| **I** | 인명 안전·선박 안전·환경에 위험한 상황을 **초래하지 않음** | 감시, 정보 제공, 관리 기능 |
| **II** | 위험한 상황을 **결국(eventually) 초래할 수 있음** | 선박을 정상 운항·거주 조건으로 유지하는 데 필요한 경보·감시·제어 기능 |
| **III** | 위험하거나 파국적인 상황을 **즉시(immediately) 초래할 수 있음** | 추진·조타 유지를 위한 제어 기능, 선박 안전 기능 |

핵심 구분어는 `eventually`(II)와 `immediately`(III)다.

## Why it matters

[SOURCE] 카테고리에 따라 적용되는 요구가 달라진다.

- **UR E22 §3.2** — Cat I 시스템은 통상 선급 검증 대상이 아니다. 다만 카테고리 판정이 올바른지, Cat II·III 운영에 영향을 주지 않는지 확인하기 위해 요청 시 정보를 제출해야 한다.
- **UR E22 §4.2.2, §7.1.1** — 고유 식별자 요구는 Cat II·III에 적용된다. Cat I은 해당 없음. (Rec 190 §6.1 컬럼 H)
- **UR E26 §4.2.4.3.1** — 물리적 접근 제한은 Cat II·III에 요구된다. (Rec 190 §6.1 컬럼 L)
- **Rec 190 §6.1 컬럼 E** — 자산 목록에 카테고리를 기재한다. 대부분 II 또는 III이며 일부가 I이다.

## Key Characteristics

[SOURCE] **카테고리는 선박마다 달라질 수 있다.**

> The category of a system shall always be evaluated in the context of the specific vessel in question; thus, the categorization of a system may vary from one vessel to the next.
> — UR E22 §3.3

따라서 §3.3의 예시는 **참고용**이며, 특정 선박의 판정은 §4.3.3(통합자의 카테고리 결정) 절차를 따른다.

[SOURCE] IACS Rec 171 §5의 예시:

| Cat | 예시 |
| --- | --- |
| **II** | 액체화물 이송 제어, 빌지 수위 탐지 및 펌프 제어, 연료유 처리, 밸러스트 이송 밸브 원격 제어, 안정화·승선감 제어, 추진 계통 경보·감시 |
| **III** | 추진 계통(기계적 추력 생성·제어 — 선수 스러스터 등 조종 전용 장치는 제외), 조타 제어, 전력 계통(전력관리 포함), 선박 안전 계통(화재 탐지·소화, 침수 탐지·방지, 퇴선 단계 선내 통신, 구명설비 운용 관련), DP 등급 2·3 (IMO MSC/Circ.645) |

## Related Concepts

- [[Computer Based System]] — 카테고리가 부여되는 대상
- [[Essential Services]] — Cat III의 내용과 상당 부분 겹친다
- [[Compensating Countermeasure]] — 카테고리별 요구 수준과 연동
- [[Security Zone]] — 위험 프로파일에 따른 존 그룹핑의 근거
- [[Cyber Risk Management]] — Rec 171이 카테고리를 리스크 평가 입력으로 사용

## Applications

| 문서 | 위치 |
| --- | --- |
| **UR E22** | **§3.1 정의(Table 3)** / §3.2 선급 검증 범위 / §3.3 예시 / §4.3.3 결정 절차 |
| UR E26 | §1.3.3 시스템 카테고리 참조 / §4.2.4.3.1 물리 접근통제 |
| UR E27 | §1.4 정의 (E22 참조) |
| Rec 190 | §6.1 컬럼 E, H, L |
| Rec 171 | §5 핵심 장비 식별 / Table 3 카테고리 부여 |
| Rec 166 | §4.1.53 정의 |

## Limitations

- [SOURCE] E22 §1.2 — 법정 규정 적용 CBS는 E22 대상에서 제외된다. Rec 190 §6.1 컬럼 E 설명에 따르면 **항해 장비는 E22 범위 밖이라 카테고리가 "not applicable"일 수 있으나, E26 범위에는 들어가므로 자산 목록에는 등재된다.**
- [SOURCE] E22 §3.3 — 선박별로 달라지므로 예시를 그대로 옮겨 쓸 수 없다.
- [INFERENCE] 이 때문에 [[Onboard System Index]]에서는 110종에 카테고리를 부여하지 않았다. 선박 컨텍스트 없이 부여하면 §3.3에 어긋난다.

## Sources

- `Database/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` §1.2, §3.1, §3.2, §3.3, §4.2.2, §4.3.3
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §1.3.3, §4.2.4.3.1
- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` §6.1
- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` §5
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.53

## Notes

인용 시 **출처는 항상 UR E22 §3.1**로 쓴다. 다른 문서의 서술은 참조이지 정의가 아니다. → [[Term Locator]]
