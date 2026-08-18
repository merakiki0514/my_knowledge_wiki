---
type: method
tags:
  - method
  - risk
---

# BIMCO Risk Assessment

BIMCO Guidelines v5 §6.2 — 선박 사이버 리스크 평가의 **운영 관점 4단계 절차**.
[[IACS Rec 171 Cyber Risk Assessment]]가 등급·수식 중심이라면, 이쪽은 **누가 무엇을 언제 하는가**에 초점이 있다.

## Overview

[SOURCE] BIMCO v5는 리스크 평가에 이르는 경로를 장 단위로 나눈다.

| 장 | 내용 |
| --- | --- |
| §2 | 위협 식별 (위협 행위자, 위협 유형, 사고 단계, 위협 정량화) |
| §3 | 취약점 식별 (공통 취약점, 문서화, 취약 시스템, 선박-육상 인터페이스, 선박 방문, 원격접속, 유지보수) |
| §4 | 발생가능성 평가 (위협 × 취약점) |
| §5 | 영향 평가 (CIA 모델, 정량화, "critical" 장비) |
| **§6** | **리스크 평가** |
| §7~§10 | 보호 / 탐지 / 비상계획 / 대응·복구 |

## Procedure — 4단계 (§6.2)

### Phase 1: Pre-assessment activities

[SOURCE] 승선 평가 착수 전에 수행할 활동.

- §3.2에 기술된 **IT·OT 시스템 문서를 검토**하고, CIA 모델(§5.1)을 이용해 잠재적 영향 수준을 평가
- 핵심 선내 IT·OT 장비의 **주요 제조사 식별** (리스크 기반 접근으로)
- 주요 제조사의 **사이버보안 담당 창구를 식별하고 협력 관계를 구축**
- 선박의 IT·OT 시스템 유지보수·지원에 관한 상세 문서 검토
- 선내 네트워크·장비의 유지보수·지원에 대해 선주·운항사가 가질 수 있는 **계약상 요구사항과 의무 확정**

[SOURCE] 리스크 평가는 복잡한 작업이며 사이버 리스크 관리에 대한 상세 지식이 필요하다. **제3자 지원이 필요할 가능성이 높다.**

[SOURCE] 기존 선박·신조선·중고선 모두에 적용되며, **선대에 편입되는 중고선에는 추가 주의**가 필요하다.

### Phase 2: Ship assessment

[SOURCE] 모든 리스크 요인(위협·취약점·발생가능성·영향)이 평가되면 리스크 평가와 완화를 수행한다.

- **시스템 단위(system by system)**로 수행하며, §5.2의 시스템 문서에 기반한다
- 정확도를 위해 다음에 대한 지식이 필요하다:
  - 시스템의 기능
  - 시스템으로 들고 나는 **데이터 흐름**
  - 각 시스템이 유선·무선으로 **다른 시스템과 정확히 어떻게 연결되는지**
- 회사 내 다양한 인력, 장비 제조사, 필요 시 외부 전문가의 입력이 필요하다

> Every connection is a potential vulnerability.
> — BIMCO v5 §6.2 Phase 2

[SOURCE] 예시로 인터넷 접근 가능한 공유 네트워크 프린터 연결이 제시된다 — 공격자가 그 프린터를 다른 시스템으로 가는 관문으로 쓸 수 있다.

### Phase 3: Debrief and reporting

[SOURCE] **ISM Code 요구를 충족하기 위해**, 리스크 평가는 리스크가 어떻게 평가되고 완화되었는지를 반영하는 **일관되고 최신인 문서**여야 한다.

[SOURCE] 이는 흔히 **반복적 과정**이 된다 — 여러 완화 조치 조합을 검토하다가, 법적 요구·리스크 감수 수준·실행가능성·효과성·비용 측면에서 최적 구성을 결정한다.

[SOURCE] 외부 기관이 수행하는 경우, 초기 보고서는 권고를 담은 **잠정 보고**일 가능성이 높다. 권고를 검토하고 최종 결정이 내려지면 이를 최종 리스크 평가에 반영한다.

**제3자 초기 평가 보고서의 구성 예시** [SOURCE]:

| 항목 | 내용 |
| --- | --- |
| Executive summary | 결과·권고·평가 선박의 전반적 보안 프로파일 요약 |
| Technical findings | 발견된 취약점, 악용 가능성, 악용의 금전적 비용, 승무원·선박·환경에 미치는 영향, 기술적 수정·완화 조언 |
| **Prioritised list of actions** | 효과성·비용·적용가능성을 반영한 우선순위. ⚠️ **가용한 모든 선택지를 포함해야 하며, 평가 수행자가 팔고 싶은 서비스·제품 목록이 되어서는 안 된다** |
| Supplementary data | 모든 핵심 발견의 기술적 상세와 치명적 결함의 종합 분석. 침투시험을 수행했다면 그 과정에서 확보한 데이터 포함 |
| Appendices | 평가팀이 수행한 활동과 사용한 도구의 기록 |

### Phase 4: Manufacturer's debrief

[SOURCE] 선주가 발견사항을 검토·논의·평가한 뒤, 발견사항 중 일부를 **영향받는 시스템의 제조사에 전달**하여 리스크를 줄이거나 완화할 수단을 제공받을 수 있다.

## Limitations

- [SOURCE] BIMCO v5 이용약관 — 이 지침의 조언과 정보는 **순전히 이용자 자신의 책임 하에 사용되는 안내**로 제공된다. 보증이나 책임을 지지 않는다.
- [SOURCE] §6.3 Third party risk assessments가 별도로 있다. 외부 위탁 시 참조.
- [INFERENCE] 등급 체계나 수식이 없다. 정량 결과가 필요하면 [[IACS Rec 171 Cyber Risk Assessment]]와 병행해야 한다.
- [확인 필요] Phase 3이 언급하는 "ISM Code 요구"의 근거 조문은 ISM Code 본체가 `Database/`에 없어 직접 확인할 수 없다. → [[Database Inventory#5.4 ISM Code — 무엇을 갖고 있고 무엇이 없는가]]

## Related

- [[Cyber Risk Management]] — 상위 개념
- [[IACS Rec 171 Cyber Risk Assessment]] — 정량 방법
- [[CBS Exclusion Risk Assessment]] — E26의 별도 목적 평가
- [[NIST RMF for OT]]
- [[Vessel Asset Inventory 작성법]] — Phase 1·2의 입력 문서
- [[Attack Surface]] — "모든 연결이 잠재적 취약점"

## Sources

- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §2, §3, §4, §5, §6.2, §6.3, ANNEX 2
- 조항 위치: [[Regulation Locator#11. 리스크 평가]]
