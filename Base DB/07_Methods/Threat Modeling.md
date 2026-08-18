---
type: method
tags:
  - method
  - threat-modeling
---

# Threat Modeling

⚠️ **이 문서는 2차 자료에 근거한다.** `Database/` 내 규정 원문에 위협 모델링 절차를 규정한 조항이 없다.

## 근거 수준

| 구분 | 상태 |
| --- | --- |
| 1차 근거 | **없음.** IACS UR·IMO 문서에 위협 모델링 절차 조항 없음 |
| 2차 근거 | 강의 노트 `Database/Maritime_OT_Cyber_security/5. Risk Assessment/3. Assessing Risk with Threat Modeling.txt` §5.3.1~§5.3.7 |
| 관련 1차 근거 | NIST SP 800-82r3 §4.1.2 (OT 환경의 리스크 평가) — 위협 모델링을 직접 규정하지는 않음 [확인 필요] |

> 이 문서의 내용을 규정 준수 근거로 인용하지 않는다. 작업 방법의 참고로만 쓴다.

## Overview

[2차 자료] 위협 모델링은 시스템·소프트웨어의 보안을 평가하는 **선제적 접근법**으로, 취약점 평가와 리스크 평가를 하나의 일관된 체계로 묶는다.

이상적으로는 시스템이 설계·생산의 각 단계를 지날 때마다 **반복적으로** 적용한다. 이미 배치된 시스템에도 새 취약점이 발견되면 적용할 수 있으나, **취약점 대응 비용은 설계 → 개발 → 배치로 갈수록 급격히 증가**하므로 개발 과정 전반에 적용하는 것이 가장 좋다.

## 세 가지 접근 방식

[2차 자료]

| 접근 | 관점 |
| --- | --- |
| Attack-centric | 공격자의 관점에서 수행 |
| **Defense-centric** | 시스템 아키텍처를 분석해 각 구성요소에 대한 위협을 식별 |
| Asset-centric | 자산을 분류하고 가치를 부여하는 데 초점 |

[2차 자료] 해당 강의는 주로 **defense-centric** 접근을 다룬다.

## Procedure — 5단계

[2차 자료] 시작 시 던지는 질문:

```text
What are we modeling?
What are the potential threats?
What are the risks?
What can be done to address the risks?
Did we do a good job of addressing the threats?
```

| 단계 | 내용 | 대응 질문 |
| --- | --- | --- |
| 1 | **Define Security Objectives** | 무엇을 모델링하는가 |
| 2 | **Document the System** | 〃 |
| 3 | **Identify Threats and Assign Risk** | 잠재 위협·리스크는 무엇인가 |
| 4 | **Recommend Mitigation** | 리스크에 무엇을 할 수 있는가 |
| 5 | **Validate the Model** | 위협 대응을 잘 했는가 |

### Step 1. 보안 목표 정의 (§5.3.2)

[2차 자료] 시스템의 목적과 운영에 근거해 보안 목표를 정한다. 목표 결정 범주:

| 범주 | 내용 |
| --- | --- |
| Identify | 사용자와 장치를 인증 |
| Financial | 재정적 위험이 결부된 자산 식별 |
| Reputation | 공격 시 조직 평판에 미치는 영향 고려 |
| Privacy and Regulation | 프라이버시 및 기타 준수 요구의 영향 문서화 |
| Availability Guarantees | 시스템 가용성 요구 식별 |
| Safety | 인명·장비·시설에 미치는 영향 판단 |

[2차 자료] IACS(산업자동화제어시스템)는 높은 가용성을 가져야 한다. 핵심 기반시설이 제공하는 서비스는 항상 가용해야 하며, 중단은 국가 수준의 영향을 줄 수 있다.

→ 해양 맥락의 대응 개념은 [[Essential Services]]

### Step 2~3. 시스템 문서화와 데이터 흐름 (§5.3.3~§5.3.6)

[2차 자료]

- 보안 목표 식별 후 **시스템 아키텍처의 기능을 도식화**한다. 모든 구성요소를 그리는 것이 아니라 **기능 구획 간 데이터 흐름**을 그린다.
- **DFD(Data Flow Diagram)** — 기능 구성요소 사이의 데이터 경로, 시스템 진입점, 그 진입점을 사용하는 장치와 사람을 표시한다. 데이터 흐름의 종류와 사용 중인 **프로토콜**도 표기할 수 있다.
- 관련 하위 주제: §5.3.4 DFD 구성요소, §5.3.5 시스템의 존, §5.3.6 **신뢰 경계(Trust Boundary) 결정**

[INFERENCE] §5.3.5의 "존"과 §5.3.6의 "신뢰 경계"는 [[Security Zone]] 및 [[Untrusted Network]]와 개념적으로 대응하나, **정의가 같은지는 확인되지 않았다.** 강의 노트는 IEC 62443 계열 용어를 쓰고, E26은 자체 정의를 둔다.

## 해양 규정 작업에서의 위치

[INFERENCE] 규정이 요구하는 것은 위협 모델링이 아니라 **리스크 평가**다.

| 목적 | 사용할 방법 |
| --- | --- |
| UR E26 §6 적용 제외 | [[CBS Exclusion Risk Assessment]] |
| SMS 통합·정량 평가 | [[IACS Rec 171 Cyber Risk Assessment]] |
| 운영 관점 절차 | [[BIMCO Risk Assessment]] |
| OT 일반 | [[NIST RMF for OT]] |
| **위협 모델링** | 위 방법들의 **보조 도구**로만 |

[INFERENCE] DFD와 신뢰 경계 도출은 E26 §5.1.1이 요구하는 **Zones and conduit diagram** 작성에 실질적으로 도움이 될 수 있다. 다만 규정이 DFD를 요구하는 것은 아니다.

## Limitations

- 전체가 2차 자료 근거다. **규정 준수 근거로 쓸 수 없다.**
- STRIDE, DREAD 등 구체적 위협 분류 기법은 이 강의 노트에서 확인되지 않았다. [확인 필요]
- [확인 필요] NIST SP 800-82r3 §4.1.2가 위협 모델링을 어떻게 다루는지 원문 대조하지 않았다. 대조하면 1차 근거를 확보할 가능성이 있다.

## Related

- [[IACS Rec 171 Cyber Risk Assessment]] · [[BIMCO Risk Assessment]] · [[NIST RMF for OT]] · [[CBS Exclusion Risk Assessment]]
- [[Security Zone]] · [[Untrusted Network]] · [[Attack Surface]] · [[Essential Services]]
- [[OT Security Course Index]] — 강의 노트 원본 위치

## Sources

- `Database/Maritime_OT_Cyber_security/5. Risk Assessment/3. Assessing Risk with Threat Modeling.txt` §5.3.1~§5.3.7 **(2차 자료)**
- `Database/Maritime_OT_Cyber_security/5. Risk Assessment/2. Using a Risk Assessment Tool.txt` §5.2.1~§5.2.5 CVSS **(2차 자료)**
