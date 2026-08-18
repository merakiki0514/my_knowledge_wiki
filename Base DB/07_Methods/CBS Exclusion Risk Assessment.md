---
type: method
tags:
  - method
  - risk
---

# CBS Exclusion Risk Assessment

UR E26 적용 범위에 드는 CBS를 요건 적용에서 **제외하려 할 때** 요구되는 리스크 평가. E26 §6.

## Overview

[SOURCE] UR E26 §6 — 적용 범위에 속하는 CBS를 관련 요건 적용에서 제외하려면 정당화와 문서화가 필요하다.

> Such exclusion can be accepted by the Classification Society only if evidence is given that the risk level associated to the operation of the CBS is under an acceptable threshold by means of specific risk assessment.

[SOURCE] E26 §1.1 구조표 — 이 절은 **Supplementary Part**이며 `required only when systems are excluded from application of this UR`이다. 즉 제외를 시도하지 않으면 수행할 필요가 없다.

## Procedure

### Step 1. 평가 기반 확보

[SOURCE] E26 §6 — 리스크 평가는 다음에 기반해야 한다.

- 가용한 지식 기반(knowledge base)과 유사 설계에 대한 경험(있는 경우)
- **CBS 카테고리** → [[System Category]]
- **연결성(connectivity)**
- 선박 및 CBS의 기능 요건과 사양

[SOURCE] 내부·외부 출처의 사이버 위협 정보를 사용해 사이버보안 사건의 발생가능성과 영향을 더 잘 이해할 수 있다.

### Step 2. 운영 환경 분석

[SOURCE] E26 §6.3 — 대상 CBS의 예상 운영 환경을 분석하여, **CBS 카테고리를 고려해** 사이버 사고의 발생가능성과 그 사고가 다음에 미칠 영향을 판별한다.

- 인명 안전
- 선박의 안전
- 해양 환경

### Step 3. 공격면 분석

[SOURCE] E26 §6.3 — [[Attack Surface]]를 분석한다. 고려 항목:

- CBS의 연결성
- 휴대 장치를 위한 가능한 인터페이스
- 논리적 접근 제한
- 기타

### Step 4. 필수 고려 요소

[SOURCE] E26 §6.3 — 리스크 평가에 다음 요소를 반드시 포함한다.

```text
- Asset vulnerabilities (자산 취약점)
- Threats, both internal and external (내부·외부 위협)
- 자산에 영향을 미치는 사이버 사고가 인명 안전·선박 안전·해양환경에 미칠 잠재적 영향
- 시스템 통합 또는 시스템 간 인터페이스와 관련된 가능한 영향
  (선박 외부 시스템 포함 — 예: 선내 시스템에 원격 접속이 제공되는 경우)
```

또한 대상 CBS의 **특정 구성에서 비롯되는 신흥 리스크(emerging risks)**를 식별해야 한다.

### Step 5. 유지·갱신

[SOURCE] E26 §6.3 — 갱신 책임이 단계별로 나뉜다.

| 단계 | 주체 | 내용 |
| --- | --- | --- |
| 설계·건조 | **시스템 통합자** | 원 설계의 변경 가능성, 초기에 알려지지 않았던 신규 위협·취약점을 고려해 작성·최신화 |
| 운항 | **선주** | 사이버 상황의 지속적 변화와 선내 CBS에서 새로 식별된 약점을 고려해 지속적 개선 과정으로 갱신 |

[SOURCE] 새로운 리스크가 식별되면 선주는 기존 완화 조치를 갱신하거나 새 조치를 구현해야 한다.

**임계 초과 시**: 사이버 상황의 변화로 대상 CBS의 리스크 수준이 수용 가능 임계값을 넘게 되면, 선주는 **선급에 통보하고 갱신된 리스크 평가를 제출해 평가받아야 한다.**

### Step 6. 제출

[SOURCE] E26 §5.1.4 — 설계·건조 단계 제출 문서 5종 중 하나로 `Risk assessment for the exclusion of CBSs`가 포함된다.

## Limitations

- [SOURCE] "acceptable threshold"의 구체적 수치가 E26 §6에 **명시되어 있지 않다.** 선급 판단 사항으로 보인다. [INFERENCE]
- [확인 필요] [[IACS Rec 171 Cyber Risk Assessment]]의 정량 방법론(RL 수식)을 이 목적에 사용할 수 있는지 E26이 명시하지 않았다. Rec 171은 SMS 통합용으로 작성된 문서다.
- [SOURCE] 이 평가는 **제외를 위한 것**이지 일반적인 리스크 평가 절차가 아니다. 제외를 시도하지 않는 CBS에는 요구되지 않는다.

## Related

- [[Computer Based System]] — 제외 대상
- [[System Category]] — 평가 입력
- [[Attack Surface]] — §6.3의 분석 대상
- [[Cyber Risk Management]] — 상위 개념
- [[IACS Rec 171 Cyber Risk Assessment]] — 별개의 정량 방법론
- [[Compensating Countermeasure]] — 제외가 아닌 다른 경로
- [[Vessel Asset Inventory 작성법]]

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §1.1, §5.1.4, §6, §6.3
- 조항 위치: [[Regulation Locator#11. 리스크 평가]]

## Notes

[INFERENCE] 제외(§6)와 보완대책([[Compensating Countermeasure]], E27 §2.4)은 다른 경로다. 제외는 **요건을 적용하지 않는 것**이고, 보완대책은 **다른 수단으로 요건을 충족하는 것**이다. 혼동하지 말 것.
