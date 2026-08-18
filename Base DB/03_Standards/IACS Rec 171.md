---
type: standard
tags:
  - standard
  - iacs
  - recommendation
  - risk
---

# IACS Rec 171

IACS Recommendation No.171 — **Recommendation on incorporating cyber risk management into Safety Management Systems**. 2022년 5월.

## Overview

[SOURCE] §1 Foreword

> IMO has decided that cyber security shall be handled in accordance with the existing objectives and functional requirements of the ISM Code. Companies (DOC holders) should use their existing Safety Management Systems (and SMS measures) to assess risks and implement safeguards and otherwise handle cyber security.

[SOURCE] §1 — IMO의 리스크 정의를 인용한다: `The combination of the frequency and the severity of the consequence.` (MSC-MEPC.2/Circ.12/Rev.2). 즉 리스크는 **발생가능성**과 **결과의 심각도** 두 성분을 갖는다.

[SOURCE] §1 — **이 권고의 목표는 리스크 평가와 리스크 관리에만 초점을 둔다.**

[SOURCE] §1이 참조하는 문서: MSC-FAL.1/Circ.3, 그리고 BIMCO 등이 제작·지원하는 The Guidelines on Cyber Security onboard ships.

## Scope

[SOURCE] §4 — 어떤 시스템이든 OT와 IT로 구성될 수 있고, 육상측(공공기관·터미널·화물취급자 포함)과 연결·통합될 수 있다.

[SOURCE] §4 Table 1 "Systems reference table"이 평가 대상 시스템을 제시하며, **해당 선박의 OT/IT 아키텍처를 정확히 반영하도록 수정·보완해야 한다.**

Table 1의 그룹:

```text
Machinery Systems        (Main Engine, Remote Propulsion control, Engine Control,
                          Boiler Management, Steering Gear, Auxiliary Engine,
                          Emergency generator, DPS, IAS)
Ballast / Bilge Systems  (Ballast water management, Remote Tank gauging)
Cargo Management Systems (Cargo Control and monitoring/loading computer, ODME, Inert Gas)
Radio Communication      (VHF, MF/HF, INMARSAT-C, NAVTEX, 기타 위성통신)
Bridge Systems           (Gyro compass, ECDIS, Speed Log, Echo Sounder, AIS, GNSS,
                          RADAR, SSAS, BNWAS, Heading/track control, VDR, Weather Fax, Anemometer)
Safety Systems           (Fire detection, Gas detection / Gas Sampling 등)
```

→ 실제 선박 목록은 [[Onboard System Index]]

[SOURCE] §2.1.2 — **이 방법의 사용은 의무가 아니다.** 다른 방법을 사용할 수 있다.
[SOURCE] §2.2.3 — 선종(벌크선, 컨테이너선, 원유운반선 등)이 달라도 적용 가능하다는 취지의 서술.

## Structure

| 절 | 내용 |
| --- | --- |
| 1 | Foreword |
| 2 | Introduction (2.1 목적, 2.2 사용법 — 3단계, 2.3 방법론, 2.4 참조 지침·표준) |
| 3 | Terms and Definitions |
| 4 | Scope of application (Table 1 시스템 레퍼런스) |
| 5 | **Key equipment and technical systems identification** (UR E22 카테고리 기반) |
| 6 | Cyber threats, attacks, and techniques (Table 2, Appendix 1) |
| **7** | **Cyber Risk Assessment methodology** |
| 8 | Mitigation measures (8.1 비기술 / 8.2 기술) |

## Key Requirements

### §5 핵심 장비 식별

[SOURCE] **UR E22 시스템 카테고리를 사용**해 핵심 선상 운용에 쓰이는 기술 시스템을 식별한다. → [[System Category]]

Cat II·III 예시가 §5에 열거되어 있다.

[SOURCE] Table 3에서 각 시스템에 카테고리를 제안하나, **정확한 카테고리는 모든 운항 시나리오에 대한 리스크 평가에 따라 달라질 수 있다.**

### §7 리스크 평가 방법론 — 이 문서의 핵심

[SOURCE] 영향 · 발생가능성 · UR E22 카테고리를 결합해 시스템별 Risk Level을 산출한다.

```text
RL = 2 × (Cat + L + P − 4)
```

전체 절차와 등급표는 → **[[IACS Rec 171 Cyber Risk Assessment]]**

### §6 위협 목록

[SOURCE] Table 2 (Appendix 1)에 사이버 위협·공격·기법 목록이 있다. **비망라적**이며 식별된 추가 위협을 더해야 한다.

[SOURCE] 시스템의 연결성 등급이 Table 2의 해당 열과 일치하면, 그 위협·공격·기법(및 발생 시 결과)을 영향 평가에서 고려해야 한다.

### §8 완화 조치

[SOURCE] §8.1 비기술적 (§8.1.1 인적 관련) / §8.2 기술적.

[SOURCE] §8.1.1 — **ISM Code 6.2, 6.3, 6.5장의 권고에 따라** 인식 제고 활동을 수행한다.

## Practical Implications

[INFERENCE] `Database/`에서 **가장 실행 가능한 형태의 리스크 평가 절차**다. 수식과 임계값이 명시되어 있어 결과를 재현할 수 있다.

⚠️ [SOURCE] §7.2.2 — 여기서 정의하는 연결성 등급은 **시스템·장비에 관한 IACS UR의 "connectivity grades"와 일치하지 않는다.** 혼용 금지.

## Related Standards

- [[ISM Code]] — 이 권고의 전제. ⚠️ **본체가 `Database/`에 없다**
- [[MSC-FAL.1-Circ.3]] — §1·§2.4가 참조
- [[UR E22]] — §5가 카테고리 사용
- [[IACS Rec 166]] · [[IACS Rec 190]]
- [[BIMCO Guidelines on Cyber Security Onboard Ships]] — §1이 참조

## Related Methods / Concepts

[[IACS Rec 171 Cyber Risk Assessment]] · [[BIMCO Risk Assessment]] · [[CBS Exclusion Risk Assessment]]
[[Cyber Risk Management]] · [[System Category]] · [[Attack Surface]]

## Sources

- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf`
- 조항 위치: [[Regulation Locator#11. 리스크 평가]]

## Notes

[SOURCE] §1이 인용하는 MSC-FAL.1/Circ.3에는 **판본 표기가 없다.** 보유본은 Rev.3(2025-04)이므로 이 권고(2022-05)가 참조한 것은 이전 판이다. → [[Database Inventory#3.2 인용되는 MSC-FAL 판본이 문서마다 다르다]]
