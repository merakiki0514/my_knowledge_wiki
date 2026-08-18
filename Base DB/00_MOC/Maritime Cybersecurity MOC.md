---
type: moc
tags:
  - moc
  - maritime
  - cybersecurity
---

# Maritime Cybersecurity MOC

이 Wiki의 시작점. 목적은 **흩어진 원본 자료에서 필요한 정보를 빨리 찾는 것**이다.
따라서 이 Wiki는 원본을 요약해 대체하지 않고, **어디에 무엇이 있는지 가리키는 인덱스 계층**을 우선한다.

## 무엇을 찾고 있습니까?

| 상황 | 여기로 |
| --- | --- |
| 어떤 자료가 있는지 전체를 훑고 싶다 | [[Database Inventory]] |
| **"이 요건이 어느 규정 몇 조에 있지?"** | [[Regulation Locator]] |
| **"이 용어 정의가 어디 있지?"** | [[Term Locator]] |
| **"이 선내 시스템이 뭐 하는 거지?"** | [[Onboard System Index]] |
| OT 보안 일반 이론 (62443, NIST, Zero Trust, 위협모델링) | [[OT Security Course Index]] |
| 이 자료를 믿어도 되는지 | [[Database Inventory#2. 자료 성격 구분 (중요)]] |
| **개념이 무슨 뜻인지** | 아래 [[#개념 (01_Concepts)]] |
| **어떻게 하는지 (절차)** | 아래 [[#방법 (07_Methods)]] |
| **이 문서가 무엇인지** | 아래 [[#규정 (03_Standards)]] |
| 지금까지 무슨 작업을 했는지 | [[2026-08-18 Database 정리 작업 로그]] |

## 자료 계층

```text
SOLAS / ISM Code                          ← 협약·강제코드    [부분 ✔ 개정결의만]
   ↓
IMO MSC-FAL.1/Circ.3 Rev.3                ← 최상위 국제 지침  [보유 ✔]
   │  §4.2 → IACS UR E26·E27 / §4.3 → BIMCO, Rec166, NIST CSF 2.0
   ↓
IACS UR (E10 / E22 / E26 / E27)           ← 강제 요건        [보유 ✔]
   ↓
IACS Rec (166 / 171 / 190)                ← 비강제 권고      [보유 ✔]
   ↓
산업계 가이드 (BIMCO v5)                    ← 운영 실무        [보유 ✔]
   ↓
일반 OT 보안                              ← 이론·프로그램    [보유 ✔]
  IEC 62443-2-1 / NIST CSF 2.0 / NIST SP 800-82r3
   ↓
실제 선박 (선내 시스템 110종)                ← 현장 데이터      [보유 ✔]

별도 축:  IMO MASS Code (MSC 109/5)        ← 자율운항         [보유 ✔]
```

**규정 축이 SOLAS/ISM부터 현장 시스템까지 이어졌다.** 남은 구멍은 항해 통신 인터페이스(IEC 61162 계열) 한 칸이다.

## 개념 (01_Concepts)

원문에서 정의를 확인하고, 문서 간 정의 차이를 명시한 개념 문서 12건.
각 문서는 [SOURCE] / [INFERENCE] / [확인 필요]를 구분해 표기한다.

### 기초 — 무엇을 다루는가

- [[Computer Based System]] — 규정의 적용 단위. IMO·IACS 4개 문서의 정의가 일치
- [[IT and OT]] — ⚠️ IMO와 IACS의 **상위 개념이 다름**
- [[Essential Services]] — 보호 대상이자 동시에 보안 조치의 제약 조건
- [[System Category]] — Cat I/II/III. 정의 원문은 **UR E22 §3.1**

### 목표 — 무엇을 달성하려는가

- [[Cyber Resilience]] — 막는 것이 아니라 줄이고 완화하는 것
- [[Cyber Risk Management]] — IMO 측 상위 개념. 기능요소 6개(Govern 포함)
- [[Cyber Incident]] — ⚠️ E26/E27과 MSC-FAL의 **범위가 다름**

### 수단 — 어떻게 하는가

- [[Security Zone]] — 침해를 전제한 구조적 대응
- [[Defence in Depth]] — ⚠️ E27/NIST와 Rec 166의 **정의가 다름**
- [[Untrusted Network]] — 위협 수준이 아니라 규정 적용 범위로 신뢰를 정의
- [[Attack Surface]] — ⚠️ E26/E27과 Rec 166의 **범위가 다름**
- [[Compensating Countermeasure]] — 요건 충족이 불가능할 때의 공식 경로

> ⚠️ 표시된 5건은 문서마다 정의가 갈리는 개념이다. 인용 시 **어느 문서의 정의인지 반드시 명시**한다.

## 방법 (07_Methods)

절차 문서 8건. 각 문서는 원문의 단계·수식·임계값을 그대로 옮기고 출처 조항을 명시한다.

### 리스크 평가 — 목적에 따라 다른 방법을 쓴다

| 목적 | 방법 | 근거 |
| --- | --- | --- |
| **정량 등급·수식이 필요** | [[IACS Rec 171 Cyber Risk Assessment]] | Rec 171 §7 — `RL = 2 × (Cat + L + P − 4)` |
| **운영 절차·역할 분담** | [[BIMCO Risk Assessment]] | BIMCO v5 §6.2 — 4단계 |
| **UR E26 적용 제외** | [[CBS Exclusion Risk Assessment]] | E26 §6 |
| **OT 일반 (비해양)** | [[NIST RMF for OT]] | SP 800-82r3 §4.3 — RMF 7단계 |
| **현재/목표 격차 분석** | [[CSF Profile and Tier]] | CSF 2.0 §3.1 — 5단계 |
| 보조 도구 | [[Threat Modeling]] | ⚠️ **2차 자료 근거만** |

### 산출물 작성

- [[Vessel Asset Inventory 작성법]] — Rec 190 §6.1 컬럼 A~T. **다른 대부분 작업의 입력**
- [[Ship Cyber Resilience Test]] — E26 §5.2.1 시운전 시험 절차서

## 규정 (03_Standards)

보유 문서 15건에 대한 문서 단위 정리. 판본·적용범위·구조·핵심요건·상호관계.

### IACS Unified Requirements — 강제

- [[UR E26]] — 선박 단위. Rev.1(2023) 현행, **2024-07-01 이후 건조계약**. 2022년판 철회
- [[UR E27]] — 시스템·장비 단위. **보안능력 30개**
- [[UR E22]] — 소프트웨어 기능성. **[[System Category]] 정의의 원문 출처**
- [[UR E10]] — 형식승인 환경시험. E27 §1.2가 병행 적용 요구

### IACS Recommendations — 비강제

- [[IACS Rec 166]] — 기술 권고. **E26과 충돌 시 E26 우선**
- [[IACS Rec 171]] — SMS 통합 + **정량 리스크 평가 방법론**
- [[IACS Rec 190]] — 자산 목록 템플릿 컬럼 A~T

### IMO

- [[MSC-FAL.1-Circ.3]] — Rev.3(2025). **기능요소 6개(Govern 신설)**. §4.2가 E26·E27을 참조 표준으로 지목
- [[ISM Code]] — ⚠️ **본체 미보유.** 개정 결의 5건 + A.1118(30)만
- [[MASS Code]] — 초안 단계. 사이버 조항은 §9.7 두 문장뿐

### 산업계 · 일반 OT

- [[BIMCO Guidelines on Cyber Security Onboard Ships]] — v5. 운영 실무. 교육·방문자·장비폐기·보험
- [[NIST CSF 2.0]] — 6개 Function. MSC-FAL Rev.3 Govern의 유래
- [[NIST SP 800-82r3]] — OT 보안 316쪽. ⚠️ **CSF 1.1 구조**
- [[IEC 62443-2-1]] — 자산소유자 보안 프로그램 8개 SPE. ⚠️ **저작권 제약**
- [[IEC 61162 Series]] — ⚠️ **최대 공백.** E26 §1.3.2가 -460을 E27 §4 대체로 인정하는데 원문 없음

→ 조항 위치는 [[Regulation Locator]]

## 주제별 진입점

### 자산 · 인벤토리
[[Onboard System Index]] · [[Regulation Locator#4. 자산 목록 (Asset Inventory)]]

### 네트워크 구역 분리
[[Regulation Locator#5. 네트워크 · 구역 분리]] · [[OT Security Course Index]] (6.2.3 Zones and Conduits)

### 접근 제어 · 원격 접속
[[Regulation Locator#6. 접근 제어 · 원격 접속]] · [[OT Security Course Index]] (7.3.x)

### 탐지 · 모니터링
[[Regulation Locator#8. 탐지 · 모니터링]] · [[OT Security Course Index]] (6.3.x, 9.3.x)

### 사고 대응 · 복구
[[Regulation Locator#9. 대응 (Respond)]] · [[Regulation Locator#10. 복구 (Recover)]]

### 리스크 평가
[[Regulation Locator#11. 리스크 평가]] · [[OT Security Course Index]] (5.x 위협모델링·CVSS)

### 검사 · 입증
[[Regulation Locator#12. 입증 · 승인 · 검사]]

### MASS (자율운항선박)
[[Regulation Locator#16. MASS (자율운항선박)]]

## 주의사항

1. **파생 문서 2건**(`해양 사이버보안 IT-OT 모니터링 가이드 (내부작성·미검증).docx`, `프로토콜 매칭 가이드 V2.docx`)은 일부 서술이 원본과 어긋난다. 근거로 쓰기 전 [[Database Inventory#4. 원본과 대조되지 않는 서술 (확인 필요 목록)]]를 먼저 확인한다.
2. **버전을 섞지 않는다.** E26은 2022년판(철회)과 Rev.1(현행)이 모두 `Database/`에 있다.
3. **`shall` / `should` / `may`를 임의로 바꾸지 않는다.** 특히 E26 §4.3.1의 IDS는 `may`다. MSC-FAL은 전반이 `should` 기반이다.
4. **기능요소가 문서마다 5개/6개로 다르다.** MSC-FAL Rev.3와 CSF 2.0만 `Govern`을 최상위로 둔다. SP 800-82r3는 `ID.GV`(하위 카테고리)다. → [[Database Inventory#3.1 기능요소 개수: IMO Rev.3(6개) vs IACS·BIMCO(5개)]]
5. **MSC-FAL은 인용 판본을 확인한다.** R166·R171·BIMCO·MSC109/5는 모두 Rev.3 이전 판을 인용했다. → [[Database Inventory#3.2 인용되는 MSC-FAL 판본이 문서마다 다르다]]

### 리스크 관리 체계 · 교육
[[Regulation Locator#14. 관리체계 · 인적 요소]] — MSC-FAL §3.5.1 Govern, §3.5.3.6 연간 교육 의무

### 참조 표준 관계
[[Regulation Locator#17. 참조 표준 목록 (어떤 문서가 무엇을 인용하는가)]]

### 산업 OT 보안 프로그램 (자산 소유자)
[[Regulation Locator#18. IEC 62443-2-1 (자산 소유자 보안 프로그램)]] · [[Regulation Locator#19. NIST CSF 2.0]] · [[Regulation Locator#19b. NIST SP 800-82r3 (OT 보안 가이드)]]

### 항해 통신 인터페이스
[[Regulation Locator#17b. 항해 통신 인터페이스 (IEC 61162)]] — ⚠️ 미리보기본만 보유

### ISM Code · SOLAS
[[Regulation Locator#20. ISM Code · SOLAS]]

### 형식승인 · 환경시험
[[Regulation Locator#21. 형식승인 · 환경시험]]

## 사용 금지 파일 (보유하고 있으나 근거로 쓸 수 없음)

| 파일 | 이유 |
| --- | --- |
| `SOLAS-1974-Original-Convention-Text-...` | 1974년 **원 협약문**. Chapter IX(ISM 강제화) 부존재 |
| `UR-E26-Apr-2022-WITHDRAWN.pdf` | 발효 전 철회. Rev.1과 대조용으로만 |
| `IEC-61162-1-...PREVIEW-14p-...` | **미리보기 14쪽.** §7·§8 본문 없음 |
| 파생 docx 2건 (`...(내부작성·미검증).docx`) | 원본과 어긋나는 서술 확인됨 |

## 아직 없는 것

**여전히 없음** — IEC 61162-2 / -450, IEC 62443 나머지 파트(-3-3, -4-2 등), IEC 62541(OPC UA), ISO/IEC 27001, ISM Code 본체(A.741(18)), SOLAS 통합본, MSC-FAL Rev.2

**ISM Code 본체는 없어도 우회 가능하다** — Rec 171 + BIMCO ANNEX 2 + A.1118(30)으로 대부분 커버된다. → [[Database Inventory#5.4 ISM Code — 무엇을 갖고 있고 무엇이 없는가]]

**아직 안 만든 것** — `02_Technologies/`, `05_Organizations/`, `06_Projects/`, `08_Cases/`
→ `02_Technologies/`는 IEC 원문 제약이 정면으로 걸린다. [[2026-08-18 Database 정리 작업 로그#9. 02_Technologies 착수 판단 (2026-08-18)]] 참조.

→ [[Database Inventory#5. Database 커버리지 공백]]
