---
type: standard
tags:
  - standard
  - guideline
---

# BIMCO Guidelines on Cyber Security Onboard Ships

산업계 공동 지침 **버전 5**. 규정이 아니라 **운영 실무 안내**다.

## Version

[SOURCE] version 5. 제작·지원 단체 (Annex 5):

BIMCO, Class NK, Columbia Shipmanagement Cyprus, Chamber of Shipping of America, Cygnus Technologies, DCSA, INTERMANAGER, INTERCARGO, INTERTANKO, ICS, IMCA, IUMI, Maersk, MTS-ISAC, NORMA Cyber, OCIMF, Superyacht Builders Association (Sybass), Templar Executives, World Shipping Council

⚠️ [SOURCE] Terms of use — 이 간행물의 조언과 정보는 **순전히 이용자 자신의 책임 하에 사용되는 안내로 제공**되며, 정확성에 대한 보증이나 책임을 지지 않는다.

## Overview

[SOURCE] Introduction — 목적은 선원·환경·화물·선박의 안전과 보안을 개선하는 것이다. 관련 규정과 모범 관행에 부합하는 적절한 사이버 리스크 관리 전략의 수립을 돕되, **업무 프로세스·장비·훈련·사고 대응·복구 관리**에 초점을 둔다.

## Scope

[INFERENCE] 다른 문서와 달리 **회사·선원의 행동과 절차**를 다룬다. IACS UR이 설계·건조·검증을 다루고 MSC-FAL이 고위 수준 원칙을 다룬다면, 이쪽은 그 사이의 운영 실무를 메운다.

## Structure

| 장 | 내용 |
| --- | --- |
| 1 | 사이버보안과 리스크 관리 (1.4 **IT와 OT의 차이**, 1.6~1.8 선주·관리사·대리점·벤더 관계) |
| 2 | **위협 식별** (위협 행위자, 위협 유형, 사고 단계, 위협 정량화) |
| 3 | **취약점 식별** (공통 취약점, 문서화, 취약 시스템, 선박-육상 인터페이스, 선박 방문, 원격접속, 유지보수) |
| 4 | **발생가능성 평가** (위협 × 취약점) |
| 5 | **영향 평가** (5.1 CIA 모델, 5.3 "Critical" 장비) |
| 6 | **리스크 평가** (6.2 4단계, 6.3 제3자 평가) |
| 7 | 보호 조치 (7.1 심층방어·광범위방어, 7.2 기술적, 7.3 절차적) |
| 8 | 탐지 조치 (8.1 탐지·로깅·차단·경보, 8.2 악성코드 탐지) |
| 9 | 비상 계획 수립 |
| 10 | 대응·복구 (10.2 4단계, 10.3 복구계획, 10.5 조사, 10.6 손실, 10.7 보고) |
| ANNEX 1 | **선내 IT·OT 시스템·장비·기술 목록** |
| ANNEX 2 | **사이버 리스크 관리와 안전관리체계** (Identify~Recover) |
| ANNEX 3 | **선내 네트워크** (물리 배치, 관리, 분할, 데이터 활동 모니터링, 보호 조치) |
| ANNEX 4 | 용어집 |
| ANNEX 5 | 기여 단체 |

## Key Content

### §1.4 IT와 OT의 차이

[SOURCE] OT는 선박의 **필수 구성요소이며 선내 IT 시스템과 독립적으로 기능해야 한다.** 성능 모니터링·원격 지원 등을 위해 IT망에 연결될 수 있으나, 이 경우 **최소한 방화벽으로 인터페이스를 충분히 방호**하고 OT의 잠재 취약점이 IT망에 노출되지 않도록 해야 한다. **OT 시스템에서 적절한 패치 수준을 보장하는 것이 항상 가능하거나 실행 가능하지는 않기 때문**이다.

[SOURCE] 조직적 차이도 짚는다 — IT 관리자는 보통 OT 구매에 관여하지 않는다. OT 소프트웨어 갱신은 제조사가 수행하며 변경관리·호환성 검토·선급 승인을 수반한다. 따라서 사이버보안 책임자가 **OT 시스템 인벤토리**를 갖는 것이 유리하다.

→ [[IT and OT]]

### §6.2 리스크 평가 4단계

Phase 1 사전 활동 / Phase 2 선박 평가 / Phase 3 보고 / Phase 4 제조사 브리핑
→ **[[BIMCO Risk Assessment]]**

### ANNEX 2 — SMS 연계

[SOURCE] Identify / Protect / Detect / Respond / Recover **5개 구조**. Govern 없음.

## Practical Implications

[INFERENCE] `Database/` 문서 중 **선원 교육, 방문자 통제, 개인 장비, 장비 폐기, 보험·용선계약** 같은 주제를 다루는 유일한 문서다. IACS UR에는 대응 조항이 없다.

[SOURCE] §7.3의 절차적 조치 항목: 훈련·인식, 방문자 컴퓨터 접근, 승무원 개인 장비, 업그레이드·소프트웨어 유지보수, 백신 관리, 원격접속, 관리자 권한 사용, 물리·이동식 매체 통제, **장비 폐기 및 데이터 파기**

[SOURCE] §10.6 — 사이버 사고로 인한 손실. 재물 손해 담보, 배상책임 담보, **용선계약용 사이버보안 조항**.

## Related Standards

- [[MSC-FAL.1-Circ.3]] — §4.3.1이 이 지침을 산업 모범사례로 열거
- [[IACS Rec 171]] — §1이 이 지침을 참조
- [[UR E26]] · [[UR E27]] · [[IACS Rec 166]]
- [[ISM Code]]

## Related Methods / Concepts

[[BIMCO Risk Assessment]] · [[IT and OT]] · [[Defence in Depth]] · [[Security Zone]] · [[Cyber Incident]] · [[Attack Surface]]

## Sources

- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf`
- 조항 위치: [[Regulation Locator]]

## Notes

[INFERENCE] 규정이 아니므로 `shall`이 아니라 `should` 기반이다. 요건 근거로 인용할 때는 **강제성이 없음**을 함께 명시해야 한다.
