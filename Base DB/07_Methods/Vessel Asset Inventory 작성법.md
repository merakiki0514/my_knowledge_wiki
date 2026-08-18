---
type: method
tags:
  - method
  - asset-inventory
---

# Vessel Asset Inventory 작성법

UR E26 §4.1.1이 요구하고, Rec 190이 템플릿을 제공한다. **다른 거의 모든 작업의 입력이 되는 산출물.**

## Overview

[SOURCE] UR E26 §4.1.1.2 Rationale — 선내 CBS와 OT 시스템에서 사용되는 소프트웨어의 목록은 선박 사이버 복원성의 효과적 관리에 필수적이다. **모든 CBS가 잠재적 취약점이 되기 때문**이다. 파악되지 않았거나 구식인 하드웨어·소프트웨어를 공격자가 악용할 수 있다.

[SOURCE] Rec 190 §3 — 자산을 관리하면 회사가 **각 시스템이 선박 안전 목표에 대해 갖는 중요도**를 이해할 수 있게 된다.

## Procedure

### Step 1. 템플릿 컬럼 확정 (Rec 190 §6.1)

[SOURCE] 컬럼 A~T. 괄호 안은 근거 조항.

| 컬럼 | 항목 | 근거 |
| --- | --- | --- |
| A | 항목 번호 | — |
| **B** | **선박 기능·시스템** | E26 §4.1.1.3 |
| C | 시스템명 | E26 §4.1.1.3.1 |
| D | 장비명 | E26 §4.1.1.3.1 |
| **E** | **시스템 카테고리** | E22 §3.1 |
| F | 브랜드·제조사 | E26 §4.1.1.3.1 |
| G | 모델·형식 | E26 §4.1.1.3.1 |
| H | 고유 식별자 | E22 §4.2.2, §7.1.1 |
| I | OS — 버전 및 패치 수준 | E26 §4.1.1.3.1 |
| J | 펌웨어 — 버전 및 패치 수준 | E26 §4.1.1.3.1 |
| K | 소프트웨어 및 버전 | E26 §4.1.1.3.2 |
| L | 선내 위치 (+ 물리적 접근 제한) | E26 §4.2.4.3.1 |
| **M** | **보안 존** | E26 §4.1.1.3.1 |
| N | 기능·목적 요약 | E26 §4.1.1.3.1 |
| **O** | **범위 내 구성요소·시스템과의 연결** | 권고 |
| **P** | **비신뢰망과의 연결** | 권고 |
| Q | 물리 인터페이스 (USB×2, RJ45×1, serial 등) | E26 §4.1.1.3.1 |
| R | 지원 통신 프로토콜 (HTTP, SSH, NMEA 0183, MODBUS-TCP 등) | E26 §4.1.1.3.1 |
| S | 연결 노드의 IP 대역·MAC | 권고 (선주 보안정책이 허용하는 경우에만) |
| T | 인증서 (형식승인·선박별 승인 등) | 권고 |

[SOURCE] Rec 190 §6 — 형식은 워드 표, 엑셀, 유사 파일 모두 가능. 데이터베이스 등 다른 형식도 가능하나 **동등하거나 그 이상의 정보 수준**을 제공해야 한다.

### Step 2. 컬럼 B 값 선택

[SOURCE] Rec 190 §6.1 — 대부분의 장비는 아래 목록 중 하나에 해당한다. 목록은 **UR E26 §1.3.2.a의 "systems in scope"**에서 온 것이다.

```text
Propulsion
Steering
Anchoring and mooring
Electrical power generation and distribution
Fire detection and extinguishing systems
Bilge and ballast systems, loading computer
Watertight integrity and flooding detection
Lighting (비상조명, 저위치 조명, 항해등 등)
중단·기능저하 시 운항에 위험을 초래할 수 있는 required safety system
  (비상정지, 화물안전, 압력용기안전, 가스탐지 등)
법정 규정이 요구하는 항해 시스템
선급 규칙·법정 규정이 요구하는 내부·외부 통신 시스템
```

[SOURCE] E26 §1.3.2.b에 해당하는 인터페이스(여객·방문자 관리 시스템, 여객용 네트워크, 행정망, 승무원 복지 시스템, OT에 상시·일시 연결되는 기타 시스템)의 경우 `other`를 기입하고 설명을 덧붙인다. 예: `other – administrative network`.

### Step 3. 컬럼 E 카테고리

[SOURCE] Rec 190 §6.1 — 대부분 Cat II 또는 III이고 일부가 Cat I이다.

**항해 장비는 UR E22 범위 밖이므로 `not applicable`이 들어갈 수 있다. 다만 UR E26 범위에는 들어가므로 목록에는 등재한다.**

→ [[System Category]]

### Step 4. 생애주기별 갱신

[SOURCE] UR E26은 자산 목록을 **선박의 전 생애에 걸쳐** 갱신할 것을 요구한다. 새로운 취약점을 유발하거나 기능적 의존성·시스템 간 연결을 변경하는 하드웨어·소프트웨어 변경은 목록에 기록한다.

| 단계 | 조항 |
| --- | --- |
| 설계 | E26 §4.1.1.4.1 |
| 건조 | E26 §4.1.1.4.2 |
| 시운전 | E26 §4.1.1.4.3 |
| 운항 (연차검사·정기검사) | E26 §4.1.1.4.4 |

[SOURCE] Rec 190 §5.3 — 컴퓨터 응용프로그램으로 관리하지 않는 한, **날짜 또는 버전을 표시**해 이해관계자가 최신본인지 알 수 있게 한다.

[SOURCE] Rec 190 §5.2 — 사용 주체: 설계자, 시스템 통합자, 선주, 제3자 장비·시스템 공급자, 선급 설계검토 엔지니어, 선급 검사원.

### Step 5. 기밀정보 보호

[SOURCE] Rec 190 §5 — 자산 목록에 기밀정보(**IP 주소, 프로토콜, 포트 번호**)가 포함되는 경우, 인가된 인원만 접근할 수 있도록 특별한 조치를 취해야 한다.

## Current State

[SOURCE] 현재 `Database/선내 시스템 목록 110종.csv`에 채워져 있는 것은 **컬럼 C(시스템명)와 N(기능 요약)**뿐이다.

| 상태 | 컬럼 |
| --- | --- |
| ✔ 있음 | C, N (일부 R에 해당하는 "주요 data" 서술 있으나 프로토콜명은 아님) |
| ✘ 비어 있음 | B, E, F, G, H, I, J, K, L, M, O, P, Q, R, S, T |

→ [[Onboard System Index]]

[INFERENCE] O·P 컬럼(연결 관계)을 채우면 그대로 E26 §5.1.1이 요구하는 **Zones and conduit diagram**의 입력이 된다. → [[Security Zone]]

## Limitations

- [SOURCE] E22 §3.3 — 카테고리는 선박별로 달라진다. 다른 선박의 목록을 복사할 수 없다.
- [SOURCE] Rec 190 §6.1 — 컬럼 O·P·S·T는 **권고(recommended)**이며 E26의 명시적 요건이 아니다. S는 선주 보안정책이 허용하는 경우에만.
- [확인 필요] 컬럼 H(고유 식별자)는 Cat II·III에만 요구된다. Cat I은 `not applicable` 가능.

## Related

- [[Computer Based System]] — 등재 단위
- [[System Category]] — 컬럼 E
- [[Security Zone]] — 컬럼 M
- [[Untrusted Network]] — 컬럼 P
- [[Attack Surface]] — 컬럼 P·Q·R이 사실상 공격면 목록
- [[IACS Rec 171 Cyber Risk Assessment]] — 이 목록을 입력으로 사용
- [[Ship Cyber Resilience Test]] — 시운전 단계 갱신

## Sources

- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` §3, §5, §5.2, §5.3, §6, §6.1, Appendix 1·2
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §1.3.2, §4.1.1, §5.1.3
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §3.1.1
- `Database/UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` §3.1, §4.2.2, §7.1.1
- 조항 위치: [[Regulation Locator#4. 자산 목록 (Asset Inventory)]]

## Notes

[SOURCE] Rec 190 Appendix 1이 템플릿, Appendix 2가 작성 샘플이다. 실제 작성 시 원문의 두 부속서를 직접 볼 것.
