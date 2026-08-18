---
type: standard
tags:
  - standard
  - iacs
---

# UR E10

IACS Unified Requirement E10 — **Test Specification for Type Approval**. 형식승인 환경시험 규격.

## Version

[SOURCE] 1991년 최초 발행 이후 Rev.1(1993) → Rev.2(1997) → Rev.2.1(1999) → Rev.3(2001) → Corr.1(2003) → Rev.4(2004) → Rev.5 … → **Rev.10 (Aug 2024)**.

[SOURCE] Note 6 — "date of application for type approval"은 선급이 접수한 문서의 날짜다.

## Overview

[SOURCE] §E10.1 General

> This Test Specification is applicable, but not confined, to electrical, electronic and programmable equipment intended for control, monitoring, alarm and protection systems for use in ships.

[SOURCE] §E10.2 Testing — 시험은 **규정된 시험 조건 하에서 장비가 의도한 대로 기능함을 입증**하기 위한 것이다. 시험 범위(선정·순서·시험 개수)는 장비의 검사·평가를 통해 결정한다.

## Key Requirements

[SOURCE] 시험 항목이 번호가 붙은 표 형태로 제시된다. 각 항목마다 참조 표준·시험 조건·목적이 명시된다.

| # | 시험 | 참조 표준 (예) |
| --- | --- | --- |
| 1 | 육안 검사 | — (도면·설계자료 적합성) |
| 2 | 성능 시험 | 제조사 성능시험, 표준 대기 조건 |
| 4 | 전원 변동 (AC) | 기동(부팅 시퀀스 등) |
| 6 | 습열(Damp heat) | IEC 60068-2-30:2005 Test Db, 55°C |
| 7 | 진동 | IEC 60068-2-6:2007 Test Fc |
| 8 | 경사(Inclination) | IEC 60092-504:2016, 정적 22.5° |
| 9 | 절연 저항 | — |
| 10 | 고전압 | — |
| 11 | 저온(Cold) | IEC 60068-2-1:2007, +5°C ± 3°C |
| 12 | 염무(Salt mist) | IEC 60068-2-52:2017 Test Kb |
| 13 | 정전기 방전 | IEC 61000-4-2:2008, 접촉 방전 6 kV |
| 14 | 전자기장 | IEC 61000-4-3:2020 등 |
| 15 | 전도성 저주파 | — |
| 16 | 전도성 무선주파 | IEC 61000-4-6:2023 |
| 17 | 전기적 빠른 과도(EFT) | IEC 61000-4-4:2012 |
| 18 | 서지 | IEC 61000-4-5:2014+AMD1:2017 |

[확인 필요] 위는 원문 표의 일부를 옮긴 것이다. 전체 항목과 정확한 시험 조건은 원문을 볼 것.

## Practical Implications

[SOURCE] **[[UR E27]] §1.2가 이 UR의 병행 적용을 요구한다.**

> This UR does not cover environmental performance for the system hardware... In addition to this UR, following URs shall be applied: **UR E10 for environmental performance for the system hardware**, UR E22 for safety of equipment for the functionality of the software

[INFERENCE] 즉 선내 CBS의 승인은 세 축으로 나뉜다.

```text
UR E10  →  하드웨어 환경 성능 (진동·온도·EMC·염무 등)
UR E22  →  소프트웨어 기능성 및 시스템 카테고리
UR E27  →  사이버 보안능력
```

[SOURCE] [[IACS Rec 190]] §6.1 컬럼 T가 형식승인·선박별 승인 등 선급 인증 정보를 자산 목록에 기재하도록 한다.

## Related Standards

- [[UR E27]] — §1.2가 E10 병행 적용 요구
- [[UR E22]] — 소프트웨어 기능성. §2.2 형식승인
- [[IACS Rec 190]] — 컬럼 T

## Related Concepts

[[Computer Based System]] · [[System Category]]

## Sources

- `Database/UR-E10-Rev.10-Aug-2024-CLN.pdf`
- 조항 위치: [[Regulation Locator#21. 형식승인 · 환경시험]]

## Notes

[INFERENCE] 이 UR은 사이버보안 문서가 아니다. `Database/`에 있는 이유는 [[UR E27]] §1.2가 병행 적용을 명시하기 때문이다. 사이버 요건과 직접 겹치는 부분은 없다.
