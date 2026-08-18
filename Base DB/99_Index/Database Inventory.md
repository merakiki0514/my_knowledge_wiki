---
type: index
tags:
  - index
  - database
---

# Database Inventory

Database/ 원본 자료의 전수 목록과 유형 분류. 작성일: 2026-08-18.
이 문서는 자료의 **존재와 성격**만 기록한다. 내용 요약은 각 Wiki 문서에서 다룬다.

## 1. 자료 전수 목록 (총 26개 단위)

### 1.1 Standard / Regulation — IACS Unified Requirements (원본, 1차 자료)

| 파일 | 문서 | 버전 | 상태 | 적용 기준 |
| --- | --- | --- | --- | --- |
| `UR-E26-Apr-2022-WITHDRAWN.pdf` | UR E26 Cyber resilience of ships | Apr 2022 (原) | **Withdrawn** — 2024-01-01 발효 전 철회 (UR E26 Note 1) | — |
| `UR-E26-Rev.1-Nov-2023-CR.pdf` | UR E26 Cyber resilience of ships | Rev.1 Nov 2023 (Complete Revision) | Current | 2024-07-01 이후 건조계약 선박 의무 (UR E26 Note 2) |
| `UR-E27-Rev.1-Sep-2023-CLN.pdf` | UR E27 Cyber resilience of on-board systems and equipment | Rev.1 Sep 2023 | Current | 2024-07-01 이후 건조계약 선박 의무 (UR E27 Note 2) |
| `UR-E22-Rev.3-Corr.1-Sep-2025-CLN.pdf` | UR E22 Computer-based systems | Rev.3 Jun 2023 + Corr.1 Sep 2025 | Current | Rev.3은 2024-07-01 이후 건조계약 선박 (UR E22 Note 4) |
| `UR-E10-Rev.10-Aug-2024-CLN.pdf` | UR E10 Test Specification for Type Approval | Rev.10 Aug 2024 | Current | 형식승인 환경시험 규격. UR E27 §1.2가 병행 적용을 요구 |

- E26은 선박(ship) 단위, E27은 시스템·장비(system/equipment) 단위, E22는 소프트웨어 기능·시스템 카테고리를 규정한다. (Source: UR E26 §1.3.4)
- E27은 UR E10(환경성능), UR E22(소프트웨어 기능)와 병행 적용된다. (Source: UR E27 §1.2)

### 1.2 Standard / Recommendation — IACS Recommendations (원본, 1차 자료)

| 파일 | 문서 | 버전 | 성격 |
| --- | --- | --- | --- |
| `IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` | Rec. No.166 Recommendation on Cyber Resilience | Apr 2020, Corr.1 Jul 2020, Corr.2 Apr 2022 | 비강제 권고. UR E26과 충돌 시 **UR E26이 우선** (Source: UR E26 §1.3.4) |
| `IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` | Rec. No.171 Incorporating cyber risk management into SMS | May 2022 | ISM Code / SMS 연계 리스크 관리 |
| `IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` | Rec. No.190 Vessel Asset Inventory for CBS | Jun 2025 | UR E26 §4.1.1 / UR E27 §3.1.1의 자산목록 템플릿(A~T 컬럼) 제공 |

### 1.3 Standard / Guideline — 산업계 가이드라인 (원본, 1차 자료)

| 파일 | 문서 | 발행 |
| --- | --- | --- |
| `BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` | The Guidelines on Cyber Security Onboard Ships v5 | BIMCO 외 19개 단체 공동 (Annex 5 참조) |

- 구성: 위험관리 → 위협 식별 → 취약점 식별 → 발생가능성 → 영향 평가 → 리스크 평가 → 보호/탐지/대응/복구 조치.

### 1.4 Standard — IEC (원본, 1차 자료 · 유료 구매본)

| 파일 | 문서 | 판본 |
| --- | --- | --- |
| `IEC-62443-2-1-Ed2.0-2024-Security-Program-Requirements-for-IACS-Asset-Owners.pdf` | IEC 62443-2-1 Security program requirements for IACS asset owners | **Ed. 2.0 (2024-08)** |
| `IEC-61162-1-Ed6.0-2024-PREVIEW-14p-Digital-Interfaces-Single-Talker.pdf` | IEC 61162-1 Digital interfaces, Part 1 | **Ed. 6.0 (2024-04) — ⚠️ 미리보기 14쪽** |

- **IEC 62443-2-1 Ed2.0 구조**: 8개 SPE(Security Program Element) — `ORG`(§6) / `CM`(§7) / `NET`(§8) / `COMP`(§9) / `DATA`(§10) / `USER`(§11) / `EVENT`(§12) / `AVAIL`(§13). 성숙도 레벨(ML) 1~4와 보안 레벨(SL) 개념 포함(§4.2, §4.3). ISO/IEC 27001 및 Ed1.0 대응표 부속.
- ⚠️ **IEC 61162-1 파일은 전문이 아니라 14쪽짜리 미리보기다.** 본문 전반에 `iTeh Standards / Document Preview` 워터마크가 있고, 목차상 §7~§8(문장 구조·승인 문장 목록)의 실제 내용은 잘려 있다.
  - **확인 가능한 것**: 목차(§5 하드웨어 / §7 문장 구조 / §8 데이터 내용), §1 Scope, §2 인용 표준.
  - §1 Scope에서 확인됨 — 단방향 시리얼, 1 talker → 다수 listener, 메시지 길이 약 11~79자, 전송 주기 대체로 초당 1회 이하. **"더 빠른 전송이 필요하면 IEC 61162-2를 적용한다"**고 명시.
  - **확인 불가**: 4 800 bps / 38 400 bps 같은 전송속도 수치가 미리보기 안에 **없다.** 파일 전체 검색 결과 해당 수치 0건.
- ⚠️ **라이선스 제약**: 두 파일 모두 IEC 저작물이며, 62443-2-1 파일에는 **단일 사용자 라이선스 워터마크**가 찍혀 있다. Wiki에 본문을 옮겨 적지 않고 **조항 번호만 인용**한다. Wiki를 외부에 공유할 경우 이 PDF는 포함하지 않는다.

### 1.5 Standard / Framework — NIST (원본, 1차 자료 · 무료 공개)

| 파일 | 문서 | 상태 |
| --- | --- | --- |
| `NIST-CSWP-29-Cybersecurity-Framework-2.0-Feb-2024.pdf` | NIST Cybersecurity Framework (CSF) 2.0 | **Final (2024-02-26)**, 32쪽 |
| `NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` | NIST SP 800-82r3 Guide to Operational Technology (OT) Security | **Final (2023-09)**, 316쪽 |

- **CSF 2.0은 기능이 6개다**: `GOVERN(GV)` / `IDENTIFY(ID)` / `PROTECT(PR)` / `DETECT(DE)` / `RESPOND(RS)` / `RECOVER(RC)`. (Source: CSF 2.0 §2)
- **SP 800-82r3 최종본 구조**: §2 OT 개요(SCADA/DCS/PLC/BAS/안전계통/IIoT) · §3 OT 보안 프로그램 수립 · §4 리스크 관리(RMF 7단계) · §5 보안 아키텍처(심층방어 5계층) · §6 CSF의 OT 적용 · 부록.
- ⚠️ **SP 800-82r3(2023-09)은 CSF 1.1 구조를 쓴다.** §6이 `Identify(ID) / Protect(PR) / Detect(DE) / Respond(RS) / Recover(RC)` 5개이며, 거버넌스는 **`ID.GV`(Identify 하위 카테고리)**다. 파일 전체에서 `GV.` 기능 카테고리 검색 결과 **0건**. (Source: SP 800-82r3 §6.1.2)
  → CSF 2.0(2024-02)이 거버넌스를 최상위 `GOVERN` 기능으로 승격한 것이므로, **두 NIST 문서 사이에도 구조 차이가 있다.** 아래 §3.1 참조.

### 1.6 Standard / Convention — IMO ISM Code 계열 (원본, 1차 자료)

| 파일 | 문서 | 채택일 |
| --- | --- | --- |
| `MSC.104(73)-ISM-Code-Amendments-2000.pdf` | Resolution MSC.104(73) ISM Code 개정 | 2000-12-05 |
| `MSC.179(79)-ISM-Code-Amendments-2004.pdf` | Resolution MSC.179(79) ISM Code 개정 | 2004-12-10 |
| `MSC.195(80)-ISM-Code-Amendments-2005.pdf` | Resolution MSC.195(80) ISM Code 개정 | 2005-05-20 |
| `MSC.273(85)-ISM-Code-Amendments-2008.pdf` | Resolution MSC.273(85) ISM Code 개정 | 2008-12-04 |
| `MSC.353(92)-ISM-Code-Amendments-2013.pdf` | Resolution MSC.353(92) ISM Code 개정 | 2013-06-21 |
| `A.1118(30)-Revised-Guidelines-ISM-Code-Implementation-2017.pdf` | Resolution A.1118(30) 주관청의 ISM Code 이행 지침(개정) | 2017-12-06 |
| `SOLAS-1974-Original-Convention-Text-UNTS-Vol.1184.pdf` | SOLAS 1974 협약 **원문** (UN Treaty Series Vol.1184, No.18961) | 1974-11-01 |

- ISM Code 본체(Resolution A.741(18))는 **없다.** 위 6건은 모두 **개정 결의**이므로 원 코드 없이는 개정 전후를 대조할 수 없다. [확인 필요]
- ⚠️ **SOLAS 파일은 1974년 원 협약문이다.** UN 조약집에 1980-06-30 등록된 판본으로, `Chapter IX`(안전관리, ISM Code 강제화)가 **존재하지 않는다.** 파일 전체에서 "safety management" / "chapter IX" 검색 결과 **0건**. (Chapter IX는 1994년 개정으로 추가) → ISM·사이버 목적으로는 사용할 수 없다. **통합본(consolidated edition)이 별도로 필요하다.**

### 1.7 Standard / Guideline — IMO 사이버 (원본, 1차 자료)

| 파일 | 문서 | 판본 | 승인 |
| --- | --- | --- | --- |
| `MSC-FAL.1-Circ.3-Rev.3.pdf` | Guidelines on Maritime Cyber Risk Management | **Rev.3 (2025-04-04)** | MSC 108 (2024-05) + FAL 49 (2025-03) 승인 |

- 최상위 국제 지침. MSC.1/Circ.1526(잠정 지침)을 대체한다. (Source: 표지 §6)
- **Rev.3에서 기능요소가 5개 → 6개로 바뀌었다.** `Govern`이 신설되어 `Govern / Identify / Protect / Detect / Respond / Recover` 구조다. (Source: §3.5) → 아래 §3.1 참조
- §4.2에서 **IACS UR E26·E27을 명시적으로 참조 표준으로 열거한다.** ISO/IEC 27001 포함.
- §4.3에서 BIMCO Guidelines, IACS Rec 166, NIST CSF 2.0, IAPH Cybersecurity Guidelines를 산업 모범사례로 열거한다.

### 1.8 Organization / Project — IMO MASS 관련 (원본, 1차 자료)

| 파일 | 문서 | 성격 |
| --- | --- | --- |
| `IMO-MSC-109-5-ISWG-MASS-3차-결과보고서(영문).pdf` | MSC 109/5 (2024-09-16), Report of the 3rd Intersessional MASS WG | IMO 공식 문서. Annex에 draft MASS Code 전문(Ch.1~28) 포함 |
| `IMO-MASS-Code-개발현황-MSC-108-outcome.pdf` | IMO 사무국 발표자료 (Ricardo Batista, Maritime Safety Division) | MASS Code 개발 현황·로드맵 슬라이드 |

- 사이버 관련 조항: draft MASS Code §9.7 Security and Cybersecurity, §12 Connectivity 등.
- 로드맵(발표자료 기준): 비강제 MASS Code는 MSC 110 채택 목표, 강제 MASS Code는 2032-01-01 발효 예정.

### 1.9 Note / Course — Cisco 계열 산업제어 보안 강의 노트 (2차 자료)

`Database/Maritime_OT_Cyber_security/` — 9개 모듈, 영문 강의 노트 + 한글 오답노트 + Lab HTML + Packet Tracer(.pka).

| 모듈 | 주요 지식 단위 |
| --- | --- |
| 1. Introduction to Industrial Cybersecurity | IACS 공격 사례, CIA, IIoT 보안요구, McCumber Cube, IT/OT/IoT 비교 |
| 2. Attack Concepts and Techniques | 산업 사이버공격, 위협 행위자, 공격 기법, 공격 분석, 사이버전 |
| 3. Frameworks and Regulations | ISA/IEC 62443 계열, NIST SP 800-82 / CSF, 기타 표준, 법·윤리 |
| 4. Vulnerabilities | 공통 ICS 취약점, 취약점 테스트 유형·도구 |
| 5. Risk Assessment | 리스크 평가 개념·접근법, 평가 도구, 위협 모델링(5단계) |
| 6. Securing Industrial Networks | 보안 산업망 설계, 네트워크 분할, 네트워크 보안 모니터링 |
| 7. Authentication and Authorization | 접근통제 개념·모델, 보안 원격접속 |
| 8. Hardening | 산업망·프로토콜 하드닝, 인프라 보안 |
| 9. Frontiers | 신흥 위협, Zero Trust, Network as a Sensor |

- Lab HTML / .pka는 실습 자료로, Wiki 지식 단위가 아닌 부속 자료로 취급한다.

### 1.10 Data — 선내 시스템 목록 (1차 자료)

`선내 시스템 목록 110종.csv` — 110개 선내 시스템 × 3개 컬럼(`시스템` / `기능` / `주요 data`).

- **출처 확인됨: 실제 선박의 시스템 목록.** (사용자 확인, 2026-08-18)
- 범위: 기관(BMS, G/E, SCR, Boiler), 화물(Cargo Pump, ODME, Tank Gauge), 항해(ECDIS, Radar, AIS, VDR, Gyro), 통신(Inmarsat FBB/C, MF/HF, VHF), LNG(BOG Compressor, Vaporizer, Custody Transfer), 스마트십 플랫폼(HS4, K-IMS, ISS, HiNAS, NAVBOX) 등.
- 도메인별 탐색 인덱스 → [[Onboard System Index]]
- UR E22 시스템 카테고리(Cat I/II/III)는 **부여하지 않는다.** 선박별로 달라지고(UR E22 §3.3) 현재 목적(자료 확보·검색)에 필요하지 않다.
- UR E26 §4.1.1 Vessel Asset Inventory의 기초 자료로는 쓸 수 있으나, Rec 190 §6.1 기준 컬럼 F/G/M/O/P/Q/R/S가 비어 있다.

### 1.11 Derived Document — 내부 작성 문서 (2차/파생 자료)

**출처 확인됨: 직접 작성 + AI 생성 혼합.** (사용자 확인, 2026-08-18)
따라서 두 문서는 **원본(Source of Truth)이 아니라 검증 대상 초안**으로 취급한다.

| 파일 | 내용 | 검증 상태 |
| --- | --- | --- |
| `해양 사이버보안 IT-OT 모니터링 가이드 (내부작성·미검증).docx` | 해양·선박 사이버보안 IT/OT 통합 보안 모니터링 가이드 (0~6장 + 부록 A/B/C) | **일부 수치·요건이 Database 내 원본과 어긋남. 아래 §3 참조** |
| `선박 프로토콜-통신 하드웨어 매칭 가이드 V2 (내부작성·미검증).docx` | RS-422/485, CAN, Ethernet ↔ NMEA 0183/2000, Modbus, IEC 61162-1/-2/-450 매칭표 | **IEC 61162 원문이 Database에 없어 전면 미검증** |

> AI 생성 부분이 포함되어 있으므로, 이 두 문서의 **모든 수치·포트번호·조항 인용은 원본 대조 전까지 사실로 쓰지 않는다.**
> 문서 자체는 구조와 목차가 유용하므로 폐기하지 않고 "검증 대기" 상태로 보존한다.

---

## 2. 자료 성격 구분 (중요)

```text
[1차 원본 — 그대로 인용 가능]
  IACS UR E10 / E22 / E26 / E27
  IACS Rec 166 / 171 / 190
  BIMCO Guidelines v5
  IMO MSC-FAL.1/Circ.3/Rev.3
  IMO MSC 109/5 (ISWG-MASS 3 보고서)
  IMO ISM Code 개정 결의 5건 + A.1118(30)
  NIST CSF 2.0 / NIST SP 800-82r3 (최종본)

[1차 원본 — 인용 가능하나 저작권 제약]
  IEC 62443-2-1 Ed2.0   ← 단일 사용자 라이선스. 조항 번호만 인용, 본문 전재 금지
  IEC 61162-1 Ed6.0     ← 동일

[사용 금지 — 철회/부적합 판본]
  SOLAS 1974 원 협약문   ← Chapter IX 없음. 통합본 필요
  UR E26 Apr 2022       ← 철회됨

[2차 자료 — 출처 명시 후 인용]
  Cisco 계열 강의 노트 (원 저작물의 요약 노트)

[내부 파생 문서 — 직접 작성 + AI 생성. 원본 대조 전에는 Wiki 근거로 사용 금지]
  해양 사이버보안 IT-OT 모니터링 가이드 (내부작성·미검증).docx
  선박 프로토콜-통신 하드웨어 매칭 가이드 V2 (내부작성·미검증).docx

[현장 데이터 — 실제 선박 시스템 목록]
  선내 시스템 목록 110종.csv
```

---

## 3. 버전 · 구조 불일치 (확인된 사실)

### 3.1 기능요소 개수: IMO Rev.3(6개) vs IACS·BIMCO(5개)

MSC-FAL.1/Circ.3/**Rev.3** §3.5는 기능요소를 6개로 제시한다.

```text
Govern  →  Identify  →  Protect  →  Detect  →  Respond  →  Recover
  ↑ Rev.3에서 신설
```

반면 `Database/` 내 다른 문서들은 모두 **5개 구조**다. [SOURCE]

| 문서 | 구조 | 위치 |
| --- | --- | --- |
| MSC-FAL.1/Circ.3 Rev.3 | **6개 (Govern 포함)** | §3.5 |
| IACS UR E26 Rev.1 | 5개 | §4.1 Identify ~ §4.5 Recover |
| IACS Rec 166 | 5개 | §6.2 ~ §6.6 |
| BIMCO Guidelines v5 | 5개 | ANNEX 2 |

- **Govern의 출처는 NIST CSF 2.0으로 보인다.** [INFERENCE — 근거는 아래 모두 [SOURCE]]
  - NIST CSF **1.1**에서 거버넌스는 `ID.GV`, 즉 Identify의 하위 카테고리였다. 이를 그대로 쓴 것이 SP 800-82r3(2023-09) §6.1.2다.
  - NIST CSF 2.0(2024-02)이 기능을 5개 → 6개로 늘리며 `GOVERN(GV)`를 **최상위 기능으로 승격**했다. (CSF 2.0 §2)
  - CSF 2.0의 GOVERN 정의: `The organization's cybersecurity risk management strategy, expectations, and policies are established, communicated, and monitored`
  - MSC-FAL Rev.3 §3.5.1의 Govern: `Establish and monitor risk management strategy, expectations and policies` — 문언이 거의 일치한다.
  - MSC-FAL Rev.3 §4.3.3이 `the NIST 2.0 Framework`를 명시적으로 참조한다.
- E26 Rev.1(2023-11)과 Rec 166(2020~2022)은 **CSF 2.0(2024-02)·MSC-FAL Rev.3(2025-04)보다 먼저 발행**되었으므로 Govern을 반영할 수 없었다. 시점상 자연스러운 차이다. [INFERENCE]
- Rev.2가 5개 구조였는지는 **Rev.2 원문이 없어 여전히 확인 불가**. [확인 필요]
- MSC-FAL Rev.3 §3.5는 각 기능요소 아래 통제항목을 "**minimum controls that should be implemented**"로 규정한다. 이전 판의 표현 강도와 같은지 [확인 필요]

#### 거버넌스 위치의 변천 (보유 원본만으로 재구성)

| 시점 | 문서 | 거버넌스의 위치 |
| --- | --- | --- |
| ~2023 | NIST CSF 1.1 | `ID.GV` — Identify 하위 **카테고리** |
| 2023-09 | NIST SP 800-82r3 | `ID.GV` (§6.1.2) — CSF 1.1 구조 계승 |
| 2023-11 | IACS UR E26 Rev.1 | 없음 — Identify~Recover 5개 (§4.1~§4.5) |
| 2024-02 | **NIST CSF 2.0** | `GOVERN(GV)` — **최상위 기능으로 승격** (§2) |
| 2025-04 | **IMO MSC-FAL Rev.3** | `Govern` — 최상위 기능 (§3.5.1), §4.3.3에서 CSF 2.0 참조 |

> 즉 **거버넌스가 사라지거나 새로 생긴 것이 아니라, 카테고리에서 기능으로 위치가 올라간 것**이다.
> E26·R166·BIMCO에 Govern이 없다고 해서 거버넌스 요구가 없다는 뜻은 아니다. [INFERENCE]

### 3.2 인용되는 MSC-FAL 판본이 문서마다 다르다

| 문서 | 인용한 판본 |
| --- | --- |
| IACS Rec 166 (2020/2022) | `MSC-FAL.1/Circ.3` (판본 표기 없음) |
| IACS Rec 171 (2022) | `MSC-FAL 1/Circ.3` (판본 표기 없음) |
| BIMCO Guidelines v5 | `MSC-FAL.1/Circ.3` (판본 표기 없음) |
| IMO MSC 109/5 (2024) | **`MSC-FAL.1/Circ.3/Rev.2`** |
| 보유 원본 | **Rev.3 (2025-04-04)** |

> 위 문서들이 인용한 내용은 **Rev.3이 아닌 이전 판 기준**이다. 교차 인용 시 판본을 반드시 명시한다.
> MSC-FAL Rev.3 §4.4는 "Reference should be made to the **most current version**"이라고 명시한다.

---

## 4. 원본과 대조되지 않는 서술 (확인 필요 목록)

`해양 사이버보안 IT-OT 모니터링 가이드 (내부작성·미검증).docx` §5.5 "IACS UR E26/E27 인증 체크리스트"의 서술 중 Database 내 원본에서 확인되지 않은 항목:

| 파생 문서의 서술 | UR E26 Rev.1 원문 | 판정 |
| --- | --- | --- |
| "모든 보안 이벤트 로그 최소 90일 이상 보관" | §4.2.6.3 "provide a logging function to record all remote access events and **retain for a period of time sufficient for offline review** of remote connections" — 구체적 일수 없음 | **[확인 필요]** 90일의 출처 불명 |
| "실시간 이상 탐지 시스템(IDS/SIEM) 운영, 24/7 모니터링 체계" | §4.3.1.1 "Networks ... shall be **continuously monitored**, and alarms shall be generated". IDS는 §4.3.1.3 "**may** be implemented" — 강제 아님, 또한 "passive and not activate protection functions" 조건부 | **[의미 강화됨]** may → 의무처럼 서술 |
| "UR E26은 2024년 이후 건조 계약 선박에 의무 적용" | Note 2: "ships contracted for construction **on or after 1 July 2024**" | **[부정확]** 2024-01-01 판(Apr 2022)은 철회됨 |
| "단방향 데이터 다이오드 구현" (Zone 3↔2 필수처럼 서술) | §4.2.1 에 diode는 예시로만 언급 | **[확인 필요]** 강제 여부 |
| IEC 61162-450 = UDP 60001~60250 / OPC UA = TCP 4840·4843 등 포트 값 | Database 내 IEC 61162-450, IEC 62541 원문 **없음** | **[출처 없음]** 원문 확보 전 인용 보류 |

> 원칙: 위 항목들은 원본 표준을 확보하기 전까지 Wiki에 사실로 기재하지 않는다. (CLAUDE.md §9, §21)

---

## 5. Database 커버리지 공백

### 5.1 해결됨 (2026-08-18 확보)

| 자료 | 상태 |
| --- | --- |
| IMO MSC-FAL.1/Circ.3 | ✔ Rev.3 확보 |
| IEC 62443-2-1 | ✔ Ed2.0 전문(194쪽) 확보 |
| NIST CSF 2.0 | ✔ 전문 확보 |
| NIST SP 800-82r3 | ✔ **최종본**(2023-09, 316쪽) 확보 |
| IACS UR E10 | ✔ Rev.10 확보 |
| ISM Code 개정 결의 / 이행지침 | ✔ 6건 확보 |

### 5.2 확보했으나 사용 제약

| 자료 | 제약 | 필요한 조치 |
| --- | --- | --- |
| **IEC 61162-1 Ed6.0** | 14쪽 **미리보기**. §7·§8 본문 없음 | 전문 구매 또는 이 주제 기술 보류 |
| **SOLAS 1974 원 협약문** | Chapter IX(ISM 강제화) 없음 | SOLAS 통합본(consolidated) 필요 |
| IEC 62443-2-1 / 61162-1 | 저작권·단일 사용자 라이선스 | 조항 번호만 인용, 본문 전재·외부 공유 금지 |

### 5.3 여전히 없음

| 자료 | 왜 필요한가 |
| --- | --- |
| **IEC 61162-450 (LWE)** | 파생 docx가 전적으로 의존. 이더넷 항해망 서술의 유일한 근거가 될 문서 |
| **IEC 61162-2** | 61162-1 §1이 "더 빠른 전송은 -2 적용"이라 지시. 고속 규격 확인용 |
| IEC 62443 나머지 파트 (-3-3, -4-1, -4-2 등) | 현재 -2-1(자산소유자용)만 보유. 시스템/제품 요건은 -3-3, -4-2 |
| IEC 62541 (OPC UA) | 파생 docx의 OPC UA 서술 근거 |
| ISO/IEC 27001 | MSC-FAL §4.2 참조 표준. 62443-2-1에 대응표만 있음 |
| **ISM Code 본체 (Resolution A.741(18))** | 개정 결의만 보유 → 아래 §5.4 참조 |
| SOLAS 통합본 (Ch. V, Ch. IX) | 현재 파일은 1974년 원문뿐 |
| MSC-FAL.1/Circ.3 **Rev.2** | Rev.3 변경 내역 확인용 |

> IEC 계열은 유료라 전면 확보가 어렵다. 해당 주제는 Wiki에서 **"[2차 자료 근거]"를 명시**하고, 포트번호·전송속도 같은 구체 수치는 기재하지 않는다.
> 62443은 -2-1을 확보했으므로 **자산 소유자(선주·운항사) 관점 요건은 1차 근거로 인용 가능**하다.

### 5.4 ISM Code — 무엇을 갖고 있고 무엇이 없는가

**없는 것**: ISM Code 통합 본문 (Resolution A.741(18) 및 그 개정 반영본)

**갖고 있는 것과 그 한계** [SOURCE]

| 파일 | 실제 내용 | 개정 대상 조항 |
| --- | --- | --- |
| MSC.104(73) (2000) | 증서 유효기간·중간증서·증서 양식 관련 개정 | — |
| MSC.179(79) (2004) | 개정 결의 | (본문 확인 필요) |
| MSC.195(80) (2005) | 개정 결의 | (본문 확인 필요) |
| MSC.273(85) (2008) | 개정 결의 | §1.1.10, §1.2.2, §5.1.5, §7, §8.1, §9.2, §10.3, §12.1, §13.11, §14.4.3 |
| MSC.353(92) (2013) | 개정 결의 | §1.1.10, §1.2.3.2, §3, §4, §6.2, §8, §9, §11, §12.1, §12.2 |
| A.1118(30) (2017) | 주관청의 ISM Code **이행·검증·인증 절차** 지침 (§1~§4) | — |

> **개정 결의는 "무엇을 무엇으로 바꾼다"만 담는다.** 원 조문이 없으면 개정 전후를 재구성할 수 없다.
> 다만 A.1118(30)은 ISM Code를 81회 인용하며 검증·인증 절차를 상세히 다루므로, **심사·인증 관점 작업에는 상당 부분 대체 가능**하다. [INFERENCE]

**우회 경로** — 사이버 리스크를 SMS에 통합하는 목적이라면, ISM Code 본문 없이도 다음으로 대부분 커버된다:

| 필요한 것 | 대체 근거 |
| --- | --- |
| SMS에 사이버 리스크를 넣는 방법론 | IACS Rec 171 전체 (§7 리스크 평가, §8 완화조치) |
| ISM Code 기능요소 ↔ 사이버 조치 매핑 | BIMCO Guidelines v5 ANNEX 2 |
| ISM Code 인식·교육 요구 (§6.2, §6.3, §6.5) | Rec 171이 해당 조항을 직접 인용 |
| 심사·인증 절차 | A.1118(30) §3, §4 |
| IMO의 사이버 리스크 관리 요구 | MSC-FAL.1/Circ.3 Rev.3 §3.5 |

> ISM Code 본문은 IMO 유료 간행물이다. 위 우회 경로로 부족한 경우에만 구매를 검토한다.

## 6. 관련 문서

- [[Maritime Cybersecurity MOC]] — 전체 진입점
- [[Regulation Locator]] — 주제 → 규정 조항 위치
- [[Term Locator]] — 용어 → 정의 위치
- [[Onboard System Index]] — 선내 시스템 110종
- [[OT Security Course Index]] — 강의 노트 주제별 위치
- [[2026-08-18 Database 정리 작업 로그]] — 이 인덱스가 만들어진 경위와 검증 내역
