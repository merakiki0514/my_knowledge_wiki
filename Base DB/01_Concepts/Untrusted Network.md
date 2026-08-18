---
type: concept
tags:
  - concept
  - network
---

# Untrusted Network

## Definition

[SOURCE] IACS UR E26 §2

> Any network outside the scope of applicability of this UR.

UR E27 §1.4에도 동일 용어가 정의되어 있다. 문언 대조는 [확인 필요]

## Why it matters

[INFERENCE] 이 정의는 **위협 수준이 아니라 규정 적용 범위로 신뢰를 정의한다.** 안전한 망인지 위험한 망인지를 따지지 않고, E26의 요건이 적용되지 않으면 신뢰하지 않는다.

[SOURCE] 그 결과 IACS Rec 190 §6.1 컬럼 P의 설명이 다음을 명시한다 — UR E26은 적용 범위 밖의 **모든** 네트워크를 untrusted network로 본다. 자산 목록에 "비신뢰망과의 연결"을 별도 컬럼으로 기록하게 한 이유다.

[INFERENCE] 실무적으로 선원 복지망·행정망·위성통신망처럼 선내에 있는 망도 E26 범위 밖이면 비신뢰망이 된다. 즉 "선내/선외"가 아니라 "규정 적용/미적용"이 경계다.

## Key Characteristics

[SOURCE] UR E26의 처리 방식:

| 요건 | 조항 |
| --- | --- |
| 비신뢰망은 [[Security Zone]]과 **물리적으로 분리** | §4.2.1.3 |
| 단, 해당 시스템이 **존과 동일한 요건을 충족하면 존의 일부가 될 수 있다** | §4.2.1.3 |
| 원격 접속 및 비신뢰망과의 통신에 대한 별도 요건 | §4.2.6 |
| 원격 유지보수 추가 요건 (인적 사용자 접근에 MFA 요구) | §4.2.6.3.2 |
| 원격 접속 이벤트 로깅 및 보관 | §4.2.6.3 |
| 자산 목록에 비신뢰망 연결 기록 | Rec 190 §6.1 컬럼 P |

## Related Concepts

- [[Security Zone]] — 비신뢰망과 분리되는 대상
- [[Attack Surface]] — 비신뢰망 연결점이 공격면을 만든다
- [[Computer Based System]] — 자산 목록의 연결 기록 단위
- [[IT and OT]] — 대표적인 비신뢰망 사례가 IT망이다
- [[Cyber Resilience]]

## Applications

| 문서 | 위치 |
| --- | --- |
| UR E26 | §2 정의, §4.2.1.3 분리, §4.2.6 원격 접속 |
| UR E27 | §1.4 정의, §4.2 |
| Rec 190 | §6.1 컬럼 O(범위 내 연결) / 컬럼 P(비신뢰망 연결) |
| IACS Rec 166 | §7.6 Remote Access (검증은 §8.6) |
| IEC 62443-2-1 | §8.2.5 외부망 차단 / §8.4 원격 접속 (조항 참조만) |
| MSC-FAL | §2.2.2 — OT를 인터넷 접점 시스템으로부터 보호 |

## Limitations

- [SOURCE] 정의가 순환적이다. 무엇이 비신뢰망인지 알려면 먼저 E26 §1.3의 적용 범위가 확정되어야 한다.
- [확인 필요] 범위 밖 시스템이 "존과 동일한 요건을 충족"했음을 어떻게 입증하는지에 대한 절차는 §4.2.1.3에 명시되어 있지 않다.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §1.3, §4.2.1.3, §4.2.6
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4, §4.2
- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` §6.1 (컬럼 O, P)
- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §2.2.2

## Notes

Rec 190 §5는 자산 목록에 기밀정보(IP 주소·프로토콜·포트 번호)가 포함될 경우 **접근을 인가된 인원으로 제한하는 조치**를 요구한다. 비신뢰망 연결 정보를 기록할 때 함께 고려할 것.
