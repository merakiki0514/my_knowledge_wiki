---
type: method
tags:
  - method
  - verification
---

# Ship Cyber Resilience Test

시운전 단계에서 선박 전체의 사이버 복원성을 입증하는 절차. UR E26 §5.2.1.

## Overview

[SOURCE] UR E26 §5.2.1 — 이 문서의 내용은 §4의 각 요건별 "Demonstration of compliance" 중 **Commissioning phase** 항목에 규정되어 있다. 즉 §4 전체를 훑어 시운전 단계 요구를 모아야 한다.

## Procedure

### Step 1. 시험 생략 가능 여부 판단

[SOURCE] E26 §5.2.1 — 각 CBS에 요구되는 고유 보안능력과 그 설정은 **UR E27에 따른 CBS 인증 과정에서 검증·시험**된다. 따라서 조건부로 생략할 수 있다.

**생략 조건**: 해당 §4 소절의 "Commissioning phase"에 생략이 명시되어 있고, 그 보안 기능이 UR E27 인증 과정에서 성공적으로 시험되었을 것.

⚠️ **다만 생략하더라도 모든 시험은 시험 절차서에 포함되어야 하며, 생략 결정은 선급이 내린다.**

[SOURCE] **생략이 일반적으로 허용되지 않는 경우**:

- 인증 과정의 지적사항·코멘트가 시운전 단계로 이월된 경우
- 해당 요건이 **보완대책**으로 충족된 경우 → [[Compensating Countermeasure]]
- 인증 이후 CBS가 변경된 경우 등

### Step 2. 보완대책 시험 방법 명시

[SOURCE] E26 §5.2.1 — 시험 절차서는 §5.1.2에 기술된 **보완대책을 어떻게 시험할지도 명시**해야 한다.

### Step 3. 절차서 내용 구성

[SOURCE] E26 §5.2.1 — 시험 중 상태를 갱신하고 지적사항을 기록할 수단을 포함하고, 다음 정보를 명시한다.

```text
- Necessary test setup   (동일 조건에서 동일 결과로 재현 가능하도록)
- Test equipment
- Initial condition(s)
- Test methodology, detailed test steps
- Expected results and acceptance criteria
```

[INFERENCE] `재현 가능성`과 `합격 기준`이 명시적으로 요구된다는 점에서, 단순 점검표가 아니라 시험 규격 수준의 문서를 요구한다.

### Step 4. 통합자의 사전 확인

[SOURCE] E26 §5.2.1 — 선급에 제출하기 전 시스템 통합자가 확인할 사항:

- 선내 시스템 상호 간, 그리고 선박 외부 CBS(예: 육상)와의 통합 상태
- 문서화된 시험이 **선내 CBS·네트워크의 최종 형상**에 대해 관련 요건 충족을 위한 조치의 설치·작동을 검증하기에 충분히 상세한지

### Step 5. 통합 선박 상태에서의 검증 문서화

[SOURCE] E26 §5.2.1 — 시스템 통합자는 다음을 문서화한다.

- 완전히 통합된 선박에서의 보안 통제·조치에 대한 검증 시험 또는 평가
- 형상에 대한 변경관리 유지
- 시험 결과에 **특정 상황이나 고장으로 안전 조건이 영향받을 수 있는 지점**을 기록

### Step 6. 승선 시험 실시

[SOURCE] E26 §5.2.1 — 시험은 **CBS에 대한 다른 시운전 활동이 완료된 후**, 승인된 시험 절차서에 따라 선상에서 수행한다.

**선급은 추가 시험 실시를 요구할 수 있다.**

## Related Phases

| 단계 | 조항 | 산출물 |
| --- | --- | --- |
| 설계·건조 | E26 §5.1 | Zones and conduit diagram(§5.1.1), CSDD(§5.1.2), 자산 목록(§5.1.3), 적용제외 리스크 평가(§5.1.4), 보완대책 기술서(§5.1.5) |
| 시운전 | E26 §5.2 | **Ship cyber resilience test procedure**(§5.2.1) |
| 운항 | E26 §5.3 | 최초 연차검사(§5.3.1), 후속 연차검사(§5.3.2) |

[SOURCE] E26 §5.3 — 선박 인도 후 선주는 프로세스를 수립·이행하여 기술적·조직적 보안 대책을 관리한다.

## Limitations

- [SOURCE] §5.2.1의 내용은 §4 각 소절의 "Commissioning phase"에 흩어져 있다. **단일 조항에 시험 항목 목록이 없다.**
- [확인 필요] E26 Appendix I(Summary of actions and documents)과 Appendix II(Summary of requirements and documents)에 이를 정리한 표가 있는 것으로 보이나, 내용을 확인하지 않았다.
- [확인 필요] 생략 판단의 선급별 편차에 대한 기준은 원문에 없다.

## Related

- [[Compensating Countermeasure]] — 시험 생략이 허용되지 않는 사유이자 별도 시험 대상
- [[Vessel Asset Inventory 작성법]] — 시운전 단계 갱신 대상
- [[Security Zone]] — §5.1.1 zones and conduit diagram
- [[Computer Based System]]
- [[Cyber Resilience]]

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §4 (각 소절 Demonstration of compliance), §5.1, §5.2.1, §5.3, Appendix I·II
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §3.1.4 (보안능력 시험 절차), §3.1.10 (시험 보고서)
- 조항 위치: [[Regulation Locator#12. 입증 · 승인 · 검사]]

## Notes

[INFERENCE] E26 Appendix I·II를 확인하면 §4 전체에 흩어진 단계별 요구를 한 표로 볼 수 있을 것으로 보인다. 시험 절차서 작성 시 먼저 볼 것.
