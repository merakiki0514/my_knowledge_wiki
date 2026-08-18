---
type: method
tags:
  - method
  - risk
  - ot
---

# NIST RMF for OT

NIST SP 800-82r3 §4.3 — 위험관리 프레임워크(RMF)를 OT 시스템에 적용하는 7단계.

## Overview

[SOURCE] NIST SP 800-82r3 §4.1은 OT 보안 리스크 관리를 4개 활동으로 제시한다.

| 활동 | 조항 |
| --- | --- |
| Framing OT Risk (리스크 프레이밍) | §4.1.1 |
| Assessing Risk in an OT Environment | §4.1.2 |
| Responding to Risk in an OT Environment | §4.1.3 |
| Monitoring Risk in an OT Environment | §4.1.4 |

[SOURCE] 특별 고려 영역 — §4.2.1 **공급망 리스크 관리**, §4.2.2 **안전 계통(Safety Systems)**.

## Procedure — RMF 7단계 (§4.3)

| 단계 | 조항 |
| --- | --- |
| 1. **Prepare** | §4.3.1 |
| 2. **Categorize** | §4.3.2 |
| 3. **Select** | §4.3.3 |
| 4. **Implement** | §4.3.4 |
| 5. **Assess** | §4.3.5 |
| 6. **Authorize** | §4.3.6 |
| 7. **Monitor** | §4.3.7 |

[INFERENCE] 이름과 순서는 NIST 표준 RMF와 같다. SP 800-82r3의 기여는 각 단계를 **OT 환경에 맞게 조정하는 방법**을 제시하는 데 있다. 각 단계의 OT 특화 내용은 원문 해당 절을 볼 것.

## OT 보안 프로그램 수립 (§3)

[SOURCE] RMF 적용 이전에 프로그램 자체를 세우는 절차가 §3에 있다.

| 단계 | 조항 |
| --- | --- |
| OT 보안 프로그램 헌장 수립 | §3.1 |
| 비즈니스 케이스 (편익 / 작성 / 자료 / 경영진 보고) | §3.2.1 ~ §3.2.4 |
| **OT 보안 거버넌스 수립** | §3.3.1 |
| 교차기능팀 구성·교육 | §3.3.2 |
| OT 보안 전략 정의 | §3.3.3 |
| OT 특화 정책·절차 정의 | §3.3.4 |
| OT 환경 보안 인식 교육 프로그램 | §3.3.5 |
| **OT용 리스크 관리 프레임워크 도입** | §3.3.6 |
| 유지보수 추적 능력 개발 | §3.3.7 |
| 사고 대응 능력 개발 | §3.3.8 |
| 복구·복원 능력 개발 | §3.3.9 |
| 프로그램 내용 요약 | §3.3.10 |

## 왜 OT에서 다르게 해야 하는가

[SOURCE] SP 800-82r3 §2.4 — OT는 시간 임계적이고 결정론적 응답이 요구되며, 예기치 않은 중단이 허용되지 않는다. 정지는 수일~수주 전 계획되어야 하고, 배포 전 철저한 시험이 필수다.

[SOURCE] §2.4 — IT용으로 설계된 보안 솔루션을 OT 환경에 도입할 때는 **특별한 주의**가 필요하며, 경우에 따라 **OT 환경에 맞춘 새로운 보안 솔루션**이 필요하다.

→ [[IT and OT]] · [[Essential Services]]

## ⚠️ CSF 버전 주의

[SOURCE] SP 800-82r3(2023-09) §6 "Applying the Cybersecurity Framework to OT"는 **CSF 1.1 구조**를 쓴다.

- 기능이 5개다: Identify(ID) / Protect(PR) / Detect(DE) / Respond(RS) / Recover(RC)
- **거버넌스는 `ID.GV`, 즉 Identify의 하위 카테고리**다 (§6.1.2)
- 파일 전체에서 `GV.` 기능 카테고리 검색 결과 0건

[SOURCE] NIST CSF 2.0(2024-02)은 거버넌스를 최상위 `GOVERN` 기능으로 승격했다. 따라서 SP 800-82r3의 §6 매핑을 CSF 2.0에 그대로 대응시킬 수 없다.

→ [[CSF Profile and Tier]] · [[Database Inventory#거버넌스 위치의 변천 (보유 원본만으로 재구성)]]

## Limitations

- [SOURCE] §6이 CSF 1.1 기준이므로, CSF 2.0을 기준으로 삼는 작업(예: MSC-FAL Rev.3 대응)에서는 매핑을 다시 해야 한다.
- [INFERENCE] SP 800-82r3는 선박이 아니라 일반 산업 OT를 대상으로 한다. 선박 적용 시 IACS UR과의 대응 관계는 별도로 확인해야 한다. 원문에 해양 관련 매핑은 없다. [확인 필요]
- [확인 필요] RMF 각 단계의 OT 특화 조정 내용은 이 문서에 옮기지 않았다. 원문 §4.3.1~§4.3.7을 직접 볼 것.

## Related

- [[Cyber Risk Management]] — 상위 개념
- [[CSF Profile and Tier]] — CSF 2.0 기준 방법
- [[IACS Rec 171 Cyber Risk Assessment]] — 해양 특화 정량 방법
- [[BIMCO Risk Assessment]] — 해양 운영 관점
- [[IT and OT]] · [[Essential Services]] · [[Defence in Depth]]

## Sources

- `Database/NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` §2.4, §3.1~§3.3.10, §4.1~§4.3.7, §6
- 조항 위치: [[Regulation Locator#19b. NIST SP 800-82r3 (OT 보안 가이드)]]
