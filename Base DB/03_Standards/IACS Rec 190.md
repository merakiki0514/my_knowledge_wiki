---
type: standard
tags:
  - standard
  - iacs
  - recommendation
  - asset-inventory
---

# IACS Rec 190

IACS Recommendation No.190 — **Recommendation for Vessel Asset Inventory for Computer-based Systems**. 2025년 6월. `Database/`에서 **가장 최근 발행 IACS 문서**.

## Overview

[SOURCE] §1.1 — 이 권고는 CBS를 위한 Vessel Asset Inventory에 관한 **추가 정보를 제공**하려는 것이다.

> Please note that the Vessel Asset Inventory is **already required by IACS UR E26 and UR E27.** Please see paragraph 4.1.1 of UR E26 and paragraph 3.1.1 of UR E27.

즉 **요건은 UR에 있고, 이 권고는 그 작성 방법을 제공한다.**

[SOURCE] §2 참조 UR: E22, E26, E27.

## Scope

[SOURCE] §3 Rationale — 선내 CBS와 OT 시스템에 사용되는 소프트웨어의 목록은 선박 사이버 복원성의 효과적 관리에 필수적이다. 주된 이유는 **모든 CBS가 잠재적 취약점이 되기 때문**이다.

- 사이버 범죄자는 파악되지 않았거나 구식인 하드웨어·소프트웨어를 악용할 수 있다.
- CBS 자산 관리를 통해 회사는 **각 시스템이 선박 안전 목표에 대해 갖는 중요도**를 이해할 수 있다.

## Key Requirements

### §6.1 컬럼 A~T — 이 문서의 핵심

[SOURCE] 자산 목록에 담을 항목을 컬럼 단위로 정의하고, 각각의 근거 조항을 명시한다.

전체 컬럼 정의와 작성 절차는 → **[[Vessel Asset Inventory 작성법]]**

주요 컬럼:

| 컬럼 | 항목 | 근거 |
| --- | --- | --- |
| B | 선박 기능·시스템 (E26 §1.3.2.a 목록에서 선택) | E26 §4.1.1.3 |
| E | 시스템 카테고리 | E22 §3.1 |
| M | 보안 존 | E26 §4.1.1.3.1 |
| O / P | 범위 내 연결 / **비신뢰망 연결** | 권고 |
| Q / R | 물리 인터페이스 / 지원 프로토콜 | E26 §4.1.1.3.1 |
| S | IP 대역·MAC (선주 정책 허용 시) | 권고 |

### §5 생애주기 관리

[SOURCE] UR E26은 자산 목록을 **선박의 전 생애에 걸쳐 갱신**할 것을 요구한다. 새 취약점을 유발하거나 기능적 의존성·시스템 간 연결을 변경하는 하드웨어·소프트웨어 변경을 기록한다.

[SOURCE] §5.1 사용 시점: 설계(E26 §4.1.1.4.1) / 건조(§4.1.1.4.2) / 시운전(§4.1.1.4.3) / 운항 — 연차검사·정기검사(§4.1.1.4.4)

[SOURCE] §5.2 사용 주체: 설계자, 시스템 통합자, 선주, 제3자 장비·시스템 공급자, 선급 설계검토 엔지니어, 선급 검사원

[SOURCE] §5.3 — 컴퓨터 응용프로그램으로 관리하지 않는 한 **날짜 또는 버전을 표시**해 최신본 여부를 알 수 있게 한다.

### §5 기밀정보 취급

[SOURCE] 자산 목록에 기밀정보(**IP 주소, 프로토콜, 포트 번호** 등)가 포함되는 경우, **인가된 인원만 접근할 수 있도록 특별한 조치**를 취해야 한다.

## Practical Implications

[SOURCE] §6 — 형식은 워드 표·엑셀·유사 파일 모두 가능. 데이터베이스 등 다른 형식도 가능하나 **동등하거나 그 이상의 정보 수준**을 제공해야 한다.

[SOURCE] Appendix 1이 템플릿, Appendix 2가 작성 샘플이다.

[INFERENCE] 현재 `Database/선내 시스템 목록 110종.csv`에는 컬럼 C(시스템명)와 N(기능 요약)만 채워져 있다. **나머지 16개 컬럼이 비어 있다.** → [[Onboard System Index]]

O·P 컬럼(연결 관계)을 채우면 [[UR E26]] §5.1.1이 요구하는 Zones and conduit diagram의 입력이 된다. → [[Security Zone]]

## Related Standards

- [[UR E26]] §4.1.1 — 요건 원문
- [[UR E27]] §3.1.1 — 장비 단위 요건
- [[UR E22]] §3.1, §4.2.2, §7.1.1 — 컬럼 E·H 근거
- [[UR E10]] — 컬럼 T (형식승인)

## Related Methods / Concepts

[[Vessel Asset Inventory 작성법]] · [[Computer Based System]] · [[System Category]] · [[Security Zone]] · [[Untrusted Network]] · [[Attack Surface]]

## Sources

- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf`
- 조항 위치: [[Regulation Locator#4. 자산 목록 (Asset Inventory)]]

## Notes

[SOURCE] §6.1 컬럼 E 설명 — **항해 장비는 UR E22 범위 밖이라 카테고리가 "not applicable"일 수 있으나, UR E26 범위에는 들어가므로 목록에 등재해야 한다.**
