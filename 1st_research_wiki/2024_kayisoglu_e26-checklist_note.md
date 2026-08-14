# Kayışoğlu 외 (2024) — Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard

서지: G. Kayışoğlu, E. Düzenli, P. Bolat, and F. Bolat, "Maritime Cyber Security: Adopting a Checklist Based on IACS UR E26 Standard," *Turkish Journal of Maritime and Marine Sciences*, vol. 10, Special Issue 1, pp. 31-50, 2024. DOI: 10.52998/trjmms.1531150
원문: `papers/2024_kayisoglu_e26-checklist.pdf`
※ 원래 파일명에 줄바꿈 문자가 들어 있어 셸에서 열리지 않았으므로 `파일명_규칙.md` 형식으로 변경함(2026-08-14)
소속: Istanbul Technical University, Maritime Faculty
작성: 2026-08-14

---

## 1. 연구 목적

IACS UR E26을 기반으로 **선박 사이버보안 점검표(checklist)를 개발**하는 것. 저자들이 밝힌 효용은 "선주와 운항자가 표준을 준수하고 **검사 절차를 용이하게** 하며, 국제 규정 준수에 드는 노력을 줄이는 것"이다. [논문 내용]

## 2. 연구 문제

E26이 2024년 7월 1일부터 신조선에 적용되나, 이를 선내 안전관리체계(SMS) 안에서 실제로 운용할 **실무 도구가 없다**는 문제 인식.

## 3. 연구 대상

선박 OT 시스템 16종: SATCOM & ICS, VOIP, WLAN, Engine System, Fuel Oil System, Alarm Monitoring & Control System, Power Management System(PMS), ECDIS, RADAR, AIS, GPS, GMDSS, VDR, INS, CCR, BWS.

## 4. 연구 방법

① 선박 OT 시스템과 사이버 위험 정리(표 2, iTrust 자료 활용) → ② 각 위험의 공격 방법과 완화책 조사 → ③ E26의 17개 요구사항을 보안 점검 항목으로 변환 → ④ **요구사항(17행) × OT 시스템(16열) 매트릭스**로 점검표 구성(표 3).

실증·시험 없음. 문헌 기반 도구 개발.

## 5. 핵심 결과

표 3 점검표. 각 셀에 해당 요구사항이 그 시스템에 적용되는지를 체크 표시로 나타낸다. R1(자산 목록)은 전 시스템에 적용되고, R2(보안 구역·망분리) 이하는 시스템별로 적용 여부가 갈린다.

부수적으로 E26이 ISM Code 대비 갖는 차별점을 **Detect 기능(4.3.1 네트워크 운영 감시)**에서 찾는다. Identify·Protect는 이미 ISM 체제에서 상당 부분 이행되고 있다는 관찰. [논문 내용]

## 6. 기존 연구와 차이

E26을 다른 프레임워크와 비교하거나(→ [10]) 네트워크 설계에 반영한 연구(→ [11])와 달리, **운항 단계에서 쓸 수 있는 점검 도구**를 만든 점.

## 7. 한계

저자 명시 한계 없음. **[추론]** 점검표의 유효성을 검증한 사례 적용이 없다. 또한 아래 인용 문제가 있다.

## 8. 내가 가져갈 것

### ⭐ 2.2절 "공백" 주장의 보강 — 제외를 한 문장으로만 지나침

E26 6장을 언급하는 곳은 논문 전체에서 **한 문장뿐**이다. [논문 내용]

> "Its supplementary part is related to **risk assessment for exclusion of CBS from the application of requirements.**"

표준의 구성을 소개하는 개관 문장이고, **6.4의 수용 기준(필수 4 + 추가 3)이나 판정 방법은 전혀 다루지 않는다.** grep 결과 "exclusion/exclude/excluded"는 이 한 곳뿐이고, "6.4", "acceptance criteria" 서술은 없다.

### ⭐ 더 흥미로운 점 — 제외 판정 없이 적용 범위를 나누고 있다

표 3은 결과적으로 **"어느 요구사항이 어느 시스템에 적용되는가"의 매트릭스**다. 즉 시스템별로 요구사항 적용 여부가 갈린다. 그런데 이 구분은 **E26 6.4의 제외 절차와 무관하게** 저자들의 판단으로 이루어진다. 6.4가 요구하는 위험평가·수용 기준·선급 승인은 개입하지 않는다. [추론]

→ 규칙이 제외 경로를 두고 있으나 그 판정 기준이 실무 도구로 번역되지 않고 있다는, 우리 논지와 정합적인 사례. **다만 이건 원고에 직접 쓰기에는 해석이 개입하므로, 2.2절에서는 "제외 경로를 분석 대상으로 삼지 않는다"까지만 쓴다.**

### ⚠️ 인용 주의 — 이 논문은 판본 표기가 부정확하다

- 참고문헌 표기: **"IACS UR E26, Cyber Resilience of Ships, (2022)"** (ClassNK 사본 URL), 표 1 제목도 `(IACS UR E26, 2022)`
- 그러나 표 1이 인용한 요구사항 본문은 **Rev.1 자구**다. 예: R13 network isolation을 "It shall be possible to terminate network-based communication to or from a security zone"로 인용 — 2022년판 4.4.3은 "It shall be possible to **manually or automatically** terminate network-based communication…"이다. `rules/ur-e26-new-apr-2022.pdf` 대조 확인. [규정]
- 또한 초록은 Rev.1의 적용 시점("built on and after 1 July 2024")을 쓴다

→ **본문을 Rev.1에서 가져오면서 판본은 2022로 표기한 혼동.** 이 논문을 인용할 때 판본 관련 서술을 그대로 옮기면 안 된다.
→ **[추론]** 두 판본의 혼동이 문헌에서 실제로 발생하고 있다는 방증이며, 우리 원고가 판본을 명시적으로 대조하는 것(표 2)의 필요성을 뒷받침한다. 단 이 관찰을 원고 본문에 쓰면 특정 논문을 지적하는 서술이 되므로 **쓰지 않는다.** 우리가 정확히 쓰는 것으로 충분하다.

## 9. 내 연구와의 관계

**비교 (선행연구의 공백을 보이는 데 사용)**

[10]·[11]·강남선 외(2024)와 함께 **"규칙을 어떻게 준수할 것인가"를 다룬 연구군**으로 묶는다. 국내 연구만으로 공백을 주장하면 "해외 문헌 미조사" 지적을 받을 수 있으므로, **해외 사례를 하나 포함시키는 것이 2.2절 방어에 필요하다.**

---

## 관련 문서
- `2024_kang_e26-technical-analysis_note.md` — 같은 성격의 국내 연구
- `llm_wiki/2026-08-14_e26-2022-vs-rev1_verification.md` — 2022년판 4.4.3 자구 대조 근거
