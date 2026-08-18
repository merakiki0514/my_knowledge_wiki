---
type: concept
tags:
  - concept
  - network
---

# Security Zone

## Definition

[SOURCE] IACS UR E26 §2

> A collection of CBSs in the scope of applicability of this UR that meet the same security requirements. Each zone consists of a single interface or a group of interfaces, to which an access control policy is applied.

관련 정의 (모두 E26 §2):

| 용어 | 정의 |
| --- | --- |
| Network segment | OSI Layer-2 이더넷 세그먼트 (브로드캐스트 도메인) |
| Physical network segment | 물리 구성요소를 다른 세그먼트와 공유하지 않는 세그먼트 |
| Logical network segment | 둘 이상의 논리 세그먼트가 동일한 물리 구성요소를 공유하는 세그먼트 |

## Why it matters

[SOURCE] E26 §4.2.1.3 Rationale — 존 분할의 목적을 세 가지로 명시한다.

1. [[Attack Surface]]의 범위를 줄인다
2. 공격자의 **횡적 이동(lateral movement)**을 막는다
3. 네트워크 성능을 개선한다

같은 절에 전제가 명시되어 있다 — 방화벽·IDS/IPS로 경계를 보호해도 `breaching that perimeter is always possible`. 즉 존 분할은 **침해를 전제한 구조**다. → [[Cyber Resilience]]

## Key Characteristics

[SOURCE] UR E26 §4.2.1의 요건:

| 요건 | 조항 |
| --- | --- |
| 적용 범위 내 모든 CBS를 보안 존으로 그룹핑 | §4.2.1.1 |
| 존은 **격리(air gap)**되거나, 존 간 데이터 통신을 통제하는 수단으로 연결 (방화벽·라우터·단방향 시리얼 링크·TCP/IP 다이오드·건접점 등) | §4.2.1.1 |
| **명시적으로 허용된 트래픽만** 존 경계를 통과 | §4.2.1.1 |
| 존의 네트워크는 다른 존과 논리적 또는 물리적으로 분리 | §4.2.1.3 |
| **안전 기능 CBS는 별도 존 + 물리적 분리** | §4.2.1.3 |
| **항해·통신 시스템은 기관·화물 시스템과 같은 존에 두지 않음** | §4.2.1.3 |
| 무선 장비는 전용 존 | §4.2.1.3 |
| 적용 범위 밖 시스템은 [[Untrusted Network]]로 보고 물리적으로 분리 | §4.2.1.3 |
| 존 내 CBS의 주 기능에 영향 없이 존을 격리할 수 있어야 함 | §4.2.1.3 |

[SOURCE] `TCP/IP diodes`, `dry contacts`는 §4.2.1.1에 **예시**로 열거된 것이며 특정 방식을 강제하지 않는다.

## Related Concepts

- [[Untrusted Network]] — 존 경계 밖의 지위
- [[Computer Based System]] — 존에 묶이는 단위
- [[Defence in Depth]] — 존 분할이 구현하는 상위 원칙
- [[Attack Surface]] — 존 분할이 줄이려는 대상
- [[IT and OT]] — 분리의 1차 기준선
- [[System Category]] — 위험 프로파일에 따른 그룹핑의 근거
- [[Cyber Resilience]]

## Applications

| 문서 | 대응 개념 |
| --- | --- |
| **UR E26** | §4.2.1 보안 존 및 네트워크 분할 / §5.1.1 **Zones and conduit diagram** 제출 / §4.4.3 네트워크 격리 |
| **UR E27** | §3.1.2 토폴로지 다이어그램 (장비 단위) |
| **IEC 62443-2-1** | §8.2.1 비IACS 존과의 분리 / §8.2.2 존 및 존 간 연결 문서화 / §8.2.3 안전계통과의 분리 |
| **IACS Rec 166** | §7.3 Network (검증은 §8.3) |
| **NIST SP 800-82r3** | §5.2.3 Layer 3 – Network Security |
| **BIMCO v5** | ANNEX 3 Network segmentation |

[INFERENCE] E26이 요구하는 존 배치를 실제로 하려면 [[Onboard System Index]]의 110종을 항해·통신 / 기관 / 화물 / 안전 / 무선으로 나누고, 각 존 경계에 무엇을 둘지 정해야 한다. 이 인덱스의 도메인 그룹이 그 출발점이 될 수 있으나, **그룹과 존은 같은 것이 아니다.**

## Limitations

- [SOURCE] E26 §4.2.1.3 — 범위 밖 시스템이라도 **존과 동일한 요건을 충족하면 존의 일부가 될 수 있다.** 물리적 분리가 유일한 해법은 아니다.
- [확인 필요] "Conduit"는 §5.1.1의 문서 명칭(`Zones and conduit diagram`)에 등장하나, E26 §2 정의 목록에 **conduit 정의가 없다.** IEC 62443 계열 용어를 차용한 것으로 보이나 확인하지 않았다.
- [확인 필요] 존의 개수·입도(granularity)에 대한 기준은 E26에 없다.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §4.2.1, §4.4.3, §5.1.1
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §3.1.2
- `Database/IEC-62443-2-1-Ed2.0-2024-...pdf` §8.2 (조항 참조만 — 저작권 제약)
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §7.3, §8.3
- `Database/NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` §5.2.3
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` ANNEX 3

## Notes

Purdue Model은 강의 노트(2차 자료)와 파생 docx에만 나오며, `Database/` 내 규정 원문에서 확인되지 않는다. NIST SP 800-82r3 §5.3.6이 `Field I/O (Purdue Level 0)`를 언급하므로 1차 근거는 있으나, 모델 전체의 정의는 [확인 필요]
