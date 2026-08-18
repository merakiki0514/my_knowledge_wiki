---
type: concept
tags:
  - concept
  - cbs
---

# Computer Based System

CBS. 이 프로젝트에서 **규정의 적용 단위**가 되는 개념.

## Definition

[SOURCE] IMO MSC-FAL.1/Circ.3/Rev.3 §2.1, IACS UR E26 §2, UR E27 §1.4, UR E22 §1.5.2 Table 2 — **네 문서의 정의문이 사실상 동일하다.**

> A programmable electronic device, or interoperable set of programmable electronic devices, organized to achieve one or more specified purposes such as collection, processing, maintenance, use, sharing, dissemination, or disposition of information.
> — MSC-FAL.1/Circ.3/Rev.3 §2.1

공통으로 따라붙는 서술:

- 선내 CBS는 **IT와 OT를 모두 포함한다.**
- CBS는 네트워크로 연결된 하위 시스템의 조합일 수 있다.
- 선내 CBS는 육상 CBS·타 선박 CBS·기타 시설과 직접 또는 공중망(인터넷)을 통해 연결될 수 있다.

[INFERENCE] 문언이 일치하는 것으로 보아 IMO 정의를 IACS가 그대로 채택한 것으로 보인다. 다만 어느 쪽이 먼저인지는 확인하지 않았다. [확인 필요]

## Why it matters

[SOURCE] **CBS는 규정이 무엇에 적용되는가를 정하는 단위다.**

- UR E26 §4.1.1 — 선박 자산 목록의 등재 단위가 CBS다.
- UR E27 §3.1.1 / §4.1 — 보안능력 30개가 요구되는 대상이 CBS다.
- UR E22 §3.1 — 시스템 카테고리가 부여되는 대상이 CBS다. → [[System Category]]
- MSC-FAL §1.1 — `maritime cyber risk`의 정의 자체가 `the extent to which Computer Based Systems (CBS) are threatened by...`로 CBS를 기준 삼는다.

[INFERENCE] 즉 어떤 장비가 CBS인지 아닌지의 판단이 곧 규정 적용 여부의 판단이 된다. [[Onboard System Index]]의 110종 중 무엇이 CBS인지 확정하는 작업이 자산 목록 작성의 첫 단계가 된다.

## Key Characteristics

| 요소 | 내용 |
| --- | --- |
| 최소 단위 | 프로그래머블 전자 장치 1개 |
| 최대 단위 | 상호 운용되는 장치 집합 (네트워크로 연결된 하위 시스템 조합 가능) |
| 포함 범위 | IT + OT 양쪽 |
| 외부 연결 | 육상·타 선박·기타 시설과 직접 또는 공중망 경유 |

[SOURCE] 관련 구분 개념:

- **Integrated system** (E26 §2, E27 §1.4) — 다수의 상호작용 하위 시스템·장비를 결합해 하나 이상의 목적을 달성하는 시스템
- **Programmable device** (R166 §4.1.41) — 소프트웨어가 설치되는 물리 구성요소

## Related Concepts

- [[IT and OT]] — CBS는 양쪽을 모두 포함한다
- [[System Category]] — CBS에 부여되는 위험도 분류 (E22 §3.1)
- [[Essential Services]] — 어떤 CBS가 필수 서비스에 기여하는가
- [[Security Zone]] — CBS를 묶는 단위
- [[Attack Surface]] — CBS의 연결점이 공격면을 만든다
- [[Cyber Resilience]]

## Applications

| 작업 | CBS가 쓰이는 지점 |
| --- | --- |
| 자산 목록 작성 | E26 §4.1.1, Rec 190 §6.1 컬럼 A~T |
| 보안능력 검증 | E27 §4.1 (#1~#30), §4.2 (#31~) |
| 존 배치 | E26 §4.2.1.3 — CBS를 위험 프로파일에 따라 존으로 그룹핑 |
| 적용 제외 | E26 §6 — CBS를 요건 적용에서 제외하려면 리스크 평가 필요 |

## Limitations

- [SOURCE] E22 §1.2 — 법정 규정이 적용되는 CBS는 E22 요건에서 제외된다 (SOLAS Ch.IV·V의 항해·무선 시스템, 적하계산기 등).
- [SOURCE] E26 §1.3.2는 CBS 여부와 별개로 **선박 기능** 기준으로 적용 범위를 정한다. CBS라고 해서 모두 E26 대상은 아니다.
- [확인 필요] "programmable"의 경계. 단순 센서·액추에이터가 CBS인지는 정의만으로 판단되지 않는다.

## Sources

- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §2.1, §1.1
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §1.3.2, §4.1.1
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4, §3.1.1, §4.1
- `Database/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` §1.2, §1.5.2, §3.1
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.5, §4.1.41
- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` §6.1

## Notes

R166 §4.1.5의 정의문이 위 네 문서와 동일한지는 대조하지 않았다. [확인 필요]
