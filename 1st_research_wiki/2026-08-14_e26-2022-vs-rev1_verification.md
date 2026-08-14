# UR E26 2022년판 ↔ Rev.1 전수 대조 검증

작성: 2026-08-14
대조 자료: `rules/ur-e26-new-apr-2022.pdf` (Apr 2022, 32쪽) ↔ `rules/UR-E26-Rev.1-Nov-2023-CR.pdf` (Rev.1, 56쪽)
목적: `outputs/2026-08-13_conference-paper_draft.md` **표 2**의 각 셀을 원문과 1:1 대조하여 확정

**2026-08-14 기준 두 판본 모두 로컬 보관됨. 표 2는 이제 전량 원문 검증 가능하다.** [규정]

---

## 0. 결론 요약

| | 건수 |
|---|---|
| ✅ 원문과 일치 | 9 |
| ⚠️ **부정확 — 수정 필요** | 2 |
| ➕ 검증 중 새로 확인, 원고에 없음 | 4 |

**중요: 부정확 2건은 모두 "원고가 실제보다 약하게 쓴" 방향이다.** 정확하게 고치면 논거가 강해진다.

---

## 1. 6.4 제외 기준 — 셀 단위 대조

### 1-1. 승격 항목 (고려사항 → 필수충족)

#### ⚠️ f) → C-a : **원고 표기 부정확 (수정 필요)**

**2022년판 f) 전문**
> f) **The connections of CBS to other CBSs have been duly investigated, understood and documented.** In particular, the CBS shall not be connected to other CBSs or devices by IP-based networks;

**Rev.1 C-a 전문**
> a) The CBS shall be isolated (i.e, have no IP-network connections to other systems or networks)

**원고 현재 표기**
> `f) ... the CBS shall not be connected to other CBSs or devices by IP-based networks` → 필수 C-a로 승격

**문제**: 원고는 f)의 **앞 문장을 "..."로 가린 채** 뒷문장만 인용하고 "승격"이라고 적었다. 실제로는 f)가 두 개의 요구로 구성되어 있고, Rev.1로 넘어간 것은 **뒷문장뿐**이다. 앞 문장 — **"CBS와 다른 CBS의 연결 관계를 조사하고, 이해하고, 문서화할 것"** — 은 Rev.1 6.4 어디에도 없다.

**의미**: 이건 표 2에서 **c) 다음으로 중요한 삭제**다. c)가 "전이가 일어나지 않을 것"을 요구했다면, f) 앞문장은 **"연결 관계를 파악할 것"**을 요구했다. 전이 검증의 전제 조건이 함께 사라진 셈이다. 현재 원고는 이 사실을 스스로 가리고 있다.

**수정안**
| 2022년판 (Apr 2022) | Rev.1 (Nov 2023) 처리 |
|---|---|
| f) The connections of CBS to other CBSs have been **duly investigated, understood and documented**. In particular, the CBS shall not be connected to other CBSs or devices by IP-based networks | 뒷문장만 필수 C-a로 승격. **앞문장(연결 관계의 조사·이해·문서화 요구)은 미반영** |

---

#### ⚠️ d) → C-d : **원고 표기가 실제보다 약함 (수정 권장)**

**2022년판 d)**
> d) The CBS must not serve **essential services** or multiple ship services;

**Rev.1 C-d**
> d) The CBS shall not be an **integrated control system** serving multiple ship functions as specified in the scope of applicability of this UR (see section 1.3)

**원고 현재 표기**: "필수 C-d로 변경 (integrated control system으로 범위 축소)"

**문제**: "범위 축소"는 사실이지만 무엇이 축소되었는지를 말하지 않는다. 실제 변화는 두 방향이다.

- **강화 방향**: 고려사항 → 필수충족으로 승격
- **완화 방향**: 금지 대상이 `essential services **또는** multiple ship services` → `multiple ship functions을 담당하는 **통합제어시스템**`으로 좁아졌다.
  → 2022년판에서는 **필수 서비스를 담당하는 단일기능 CBS가 제외 불가**였다. Rev.1에서는 통합제어시스템이 아니기만 하면 **제외 가능**하다.

**의미**: 이건 A-a(Category III는 "should", 즉 재량)와 결합될 때 특히 크다. 필수 서비스를 담당하는 단일기능 CBS는 C-d를 통과하고, A-a는 강제가 아니다.

**수정안**
| 2022년판 | Rev.1 처리 |
|---|---|
| d) The CBS must not serve **essential services** or multiple ship services | 필수 C-d로 승격되었으나, 금지 대상이 **통합제어시스템으로 한정**됨. 필수 서비스를 담당하는 단일기능 CBS는 더 이상 이 항목에 걸리지 않는다 |

---

#### ✅ g) → C-b : 정확 (승격 + 구체화)

| | |
|---|---|
| 2022 g) | The CBS shall not have available physical interfaces that can be used by uncontrolled/unsecure removable devices |
| Rev.1 C-b | The CBS shall have no accessible physical interface ports. **Unused interfaces shall be logically disabled. It shall not be possible to connect unauthorised devices to the CBS** |

승격 + 문구 구체화. **이 항목은 명백히 강화되었다.** 원고 표기 유지.

#### ✅ e) → C-c : 정확

| | |
|---|---|
| 2022 e) | The CBS must be located in areas using **controlled access** |
| Rev.1 C-c | The CBS must be located in areas to which **physical access is controlled** |

승격 + "physical" 명시. 원고 표기 유지.

---

### 1-2. 유지 항목

#### ✅ a) → A-b : 정확 (Foreseeable → Known)

| | |
|---|---|
| 2022 a) | **Foreseeable** vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment |
| Rev.1 A-b | **Known** vulnerabilities, threats, potential impacts deriving from a cyber incident affecting the CBS have been duly considered in the risk assessment |

**Foreseeable(예견 가능한) → Known(알려진)** 외 나머지 문구 완전 동일. 원고 표기 정확.

#### ✅ b) → A-c : 정확 (문구 완전 동일)

> The attack surface for the CBS is minimized, having considered its complexity, connectivity, physical and logical access points, including wireless access points

두 판본 자구까지 동일. 원고 표기 유지.

---

### 1-3. 삭제 항목

#### ✅ c) 삭제 : 정확 — **논문의 핵심, 원문 확정**

**2022년판 c) 전문** (`rules/ur-e26-new-apr-2022.pdf` p.27)
> c) The CBS, considered in its function and role in the integrated system it is part of, **cannot be affected by cyber incidents vectored by other CBSs or network devices, nor it can propagate the effect of a cyber incident to other CBSs or network devices**;

Rev.1 6.4의 필수 4개·추가 3개 어디에도 대응 항목 없음. **삭제 확인.** 원고 인용 자구까지 일치.

#### ✅ h) ~ l) 삭제 : 전건 정확

| | 2022년판 원문 | Rev.1 |
|---|---|---|
| h) | The software installed on the CBS has been duly identified and evidence is given of the purpose, name, version, provider and maintainer of each software application, operating system and firmware (as applicable) | 삭제 |
| i) | The CBS is subject to a maintenance policy and such policy does not imply any permanent or temporary connection to untrusted networks, or use of uncontrolled/unsecure removable devices | 삭제 |
| j) | The CBS provides means for checking at any time its functional integrity and the quality of service provided, including checks on hardware and software integrity | 삭제 |
| k) | The CBS provides suitable interfaces allowing a human operator to take local manual control, **and such interfaces do not widen its attack surface (see also point (b))** | 삭제 |
| l) | The Incident Response Plan and Recovery Plan contain indications on how to treat the CBS in case of cyber incidents occurring on the ship | 삭제 |

※ k)의 원고 인용이 "..."로 끝나는데, 생략된 뒷부분("such interfaces do not widen its attack surface")도 함께 삭제되었으므로 논지에 영향 없음. 다만 3쪽 분량상 표 2에서 h)~l)은 **한 행으로 묶어 요약**해도 무방하다.

#### ✅ A-a 신설 : 정확

2022년판 6.4 a)~l) 전체에 Category 관련 항목 **없음**(grep 확인). Rev.1 A-a "The CBS should not serve ship functions of category III" 는 신설. 원고 표기 유지.

---

### 1-4. 재량 조항 범위 — ✅ 원고 3.1 서술 정확

| | 원문 | 재량 적용 범위 |
|---|---|---|
| 2022 6.4 | "does not fully meet the criteria as per **a) to l)** below" | **12개 전부** |
| Rev.1 6.4 | "does not fully meet the **additional criteria** listed below" | **추가 기준 3개만** |

→ 이 부분은 Rev.1에서 **강화**되었다. 원고 3.1이 "추가 기준을 완전히 충족하지 못하는 CBS라 하더라도"로 정확히 한정하고 있음. 수정 불필요.
→ 3.3절이 "일부 강화, 일부 삭제"를 정직하게 쓸 때 **이 항목도 강화 사례로 함께 제시**하면 서술이 더 단단해진다.

---

## 2. 6장 본문 대조 (표 2 밖)

### ✅ evidence → assurance : 원고 서술 정확

| 조항 | 2022년판 | Rev.1 |
|---|---|---|
| 6.1 | "The risk assessment shall provide **evidence** of the acceptable risk level" | **동일** |
| 6.2 (Rationale) | "only if **evidence** is given that the risk level ... is under an acceptable threshold" | **동일** |
| **6.4** | "only if **evidence** is given that the operation of the CBS has no impact on the safety of operations regarding cyber risk" | "only if **assurance** is given that ..." |

→ 원고의 두 주장 모두 확정. ① 6.4의 입증 수준 표현이 evidence → assurance로 바뀌었다. ② Rev.1 내부에서 6.1·6.2는 evidence, 6.4는 assurance로 **같은 장 안에서 불일치**한다. 6.1도 evidence임이 확인되었으므로 원고를 "6.1과 6.2는 여전히 evidence"로 보강 가능.

### ✅ "선내 제외 목록" 삭제 : 정확 — 그리고 **원고가 실제보다 약하게 썼음**

2022년판은 이 요구를 **세 곳**에 두었다.

1. **6.1 Requirement** — "A concise list of excluded applications of relevant requirements is to be generated and maintained with the CBS documents **onboard the ship** (e.g. the execution of test plans and any relevant updated test plans)."
2. **6.3 Requirement details** — 동일 문장 반복 + "The Class Society may **accept or reject** the exclusion of the CBS from the application of the requirements in this UR."
3. **Appendix (문서표)** — 제외 위험평가 문서의 내용 정의에 "**including a concise list of excluded applications of relevant requirements**" 명시

Rev.1에서는 **세 곳 모두 사라졌다.** 원고는 이를 한 번만 언급하며 "Rev.1에는 나타나지 않는다"로 처리 중.

### ➕ 새로 확인 — 책임 주체 변경 (원고에 없음)

| 조항 | 2022년판 | Rev.1 |
|---|---|---|
| 6.3 | 위험평가는 **the Shipyard**가 설계·건조 단계에서 작성·유지 | **the System integrator**가 작성·유지 |

→ 논지와 직접 관련은 없으나, 3.5절(이해관계자별 문서 부담)에서 이해관계자를 지칭할 때 **Rev.1 기준으로 "시스템 통합자"**를 써야 한다. 현재 원고 3.5는 주체를 특정하지 않아 문제없음.

### ➕ 새로 확인 — **Appendix 대조: 3.5절 논거를 결정적으로 강화** ⭐

**2022년판 Appendix — 제외 위험평가 문서**

| 단계 | Supplier | Shipyard/SI | Class |
|---|---|---|---|
| Design | Provide | | **Approve** |
| Construction | | Maintain | Info |
| Commissioning | Provide | | **Approve** |
| Operation | | Maintain | |
| Survey | | Make avail. | **Check** |

**Rev.1 Appendix I — Risk assessment for the exclusion of CBSs [5.1.4] NOTE 1**

| Systems integrator | | | | Shipowner | | |
|---|---|---|---|---|---|---|
| Design | Construction | Commissioning | Operation | 1st AS | AS | SS |
| Submit | Maintain | Maintain | Maintain | **(없음)** | **(없음)** | **(없음)** |

→ 두 가지가 확인된다.

1. **선급의 처리가 "Approve(승인)" → "Submit(제출)"로 바뀌었다.** 2022년판은 설계·시운전 두 단계에서 선급 **승인** 대상이었다.
2. **Rev.1에서 검사 열(1st AS / AS / SS)이 전부 비어 있다.** 비교하면:
   - `Ship cyber resilience test procedure [5.2.1]` → Commissioning **Demonstrate**, SS **Demonstrate**
   - `Ship cyber security and resilience program [5.3.1]` → 1st AS **Submit**, AS **Demonstrate**
   - `Risk assessment for the exclusion of CBSs [5.1.4]` → **검사 단계 실증 요구 없음**

**즉 제외 판정 문서는 제출 후 유지될 뿐, 검사 단계에서 실증되지 않는다.** 이것은 원고 3.5절이 주장하는 "문서 부담의 비대칭"을 **Rev.1 Appendix I만으로** 증명한다. 3.5절에 반드시 반영할 것.

※ 추가로 `NOTE 1: If applicable`이 제외 위험평가와 보상대책 설명 두 행에만 붙어 있다 — 즉 이 문서들은 **조건부 문서**다.

---

## 3. 3.4절(범주 차용) 관련 — 두 판본 동일

E26 1.3.1 System Category 문장이 두 판본 모두 동일하다.
> "System categories are defined in IACS UR E22 on the basis of the consequences of a **system failure** to human safety, safety of the vessel and/or threat to the environment."

→ 3.4절의 "고장 결과 기준" 논증은 **2022년판과 무관하게 성립한다.** Rev.1 원문만으로 완결. 이 절은 손댈 필요 없음.

---

## 4. 원고 수정 지시 — ✅ 전건 반영 완료 (2026-08-14)

- [x] **표 2 f) 행 수정** — 앞문장(연결 관계의 조사·이해·문서화)을 복원하고 "뒷문장만 필수 C-a로 승격, 앞문장 미반영"으로 표기
- [x] **표 2 d) 행 수정** — "범위 축소" → "필수 C-d로 승격. 단 금지 대상이 통합제어시스템으로 한정"
- [x] **3.3절 본문 보강** — 미반영된 것이 c) 하나가 아니라 **c) + f) 앞문장** 두 개임을 명시. "전이의 결과를 판정하는 조건과 그 판정의 전제가 되는 연결 관계 파악 요구가 함께 사라졌다"
- [x] **3.3절 강화 사례 보강** — 재량 조항 범위 축소(a~l 전체 → additional 3개만)를 강화 사례로 추가. 서술 구조를 "세 방향의 변경(강화 / 전이 조건 미반영 / d)의 범위 축소)"으로 재편
- [x] **3.3절 "선내 목록"** — "2022년판이 6.1과 6.3 및 부속서에 걸쳐 요구하던"으로 세 곳임을 반영
- [x] **3.5절에 Appendix 대조 추가** ⭐ — 시험 절차서(5.2.1)·복원력 프로그램(5.3.1)과 대비하여 제외 위험평가 문서(5.1.4)의 **검사 열이 비어 있음**을 한 문단으로 추가
- [x] **3.3절 마지막 문단 유지** — "발효 전 철회 → 완화가 아니라 최종안 미반영" 유지
- [x] **"IACS는 변경 사유를 공개하지 않았다"를 원고가 먼저 명시** — 3.3절 말미에 "본 논문은 변경의 의도를 추정하지 않으며 그 결과로 남은 조문의 상태만을 분석 대상으로 한다"로 추가
- [x] 참고문헌 [확인필요] 표시 해제 — 2022년판은 현 **[5]**

### 연쇄 수정 (위 반영에 따라 함께 손댄 곳)
- [x] 3.3절 제목: "사고 전이 조건의 부재" → **"전이 검증 조건의 부재"**
- [x] 4.2절: "2022년판 c) 항목이 최종안에 반영되었다면" → "3.3에서 확인한 두 조건, 즉 전이 여부의 판정과 연결 관계의 파악이…"
- [x] 요약·ABSTRACT·V장 결론 첫 항목: 미반영 조건이 둘임을 반영
- [x] V장 제언 첫 항목: "2022년판 c) 항목과 f) 항목 앞 문장에 해당하는 전이 검증 조건의 복원"
- [x] V장 제언 셋째 항목: "6.2와 6.4에서" → "6장 안에서" (6.1도 evidence임이 확인되었으므로)
- [x] 표 2의 h)~l) 5행을 **한 행으로 압축** (분량 확보)

## 5. 인용 표기 확정

- **[6]** IACS, *UR E26 Cyber resilience of ships*, Apr. 2022 (withdrawn before entry into force on 1 Jan. 2024, see [1] Note 1).
- 원문 각주 표기 시 쪽수: 6장 전체 **pp. 25-27 of 32**, 6.4 acceptance criteria는 **p.27**
