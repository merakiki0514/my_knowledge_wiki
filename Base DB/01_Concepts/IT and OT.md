---
type: concept
tags:
  - concept
  - ot
---

# IT and OT

정보기술(IT)과 운영기술(OT)의 구분. 해양 사이버보안의 거의 모든 문서가 이 구분에서 출발한다.

## Definition

⚠️ **문서마다 상위 개념이 다르다.** 인용 시 어느 정의인지 명시할 것. [SOURCE]

### IMO — CBS의 하위 개념으로 정의

> **Information Technology (IT)** refers to CBSs that are focused on the use of data as information
> **Operational technology (OT)** refers to CBSs that are focused on the use of data to control or monitor physical processes
> — MSC-FAL.1/Circ.3/Rev.3 §2.1

### IACS — 장치·소프트웨어의 집합으로 정의

> **Information Technology (IT):** Devices, software and associated networking focusing on the use of data as information, as opposed to Operational Technology (OT).
> **Operational Technology (OT):** Devices, sensors, software and associated networking that monitor and control onboard systems.
> — UR E26 §2 (E27 §1.4도 거의 동일)

[SOURCE] 즉 IMO는 IT/OT를 **[[Computer Based System]]의 부분집합**으로 두고, IACS는 **장치 집합**으로 둔다. 실질 내용은 같지만 상위 개념이 다르다.

- IACS Rec 166 §4.1.24 / §4.1.38, §4.1.39(OT system)에도 정의가 있다.
- UR E22 §1.5.1은 약어로만 등재한다.

## Why it matters

[SOURCE] 우선순위가 뒤집힌다.

- MSC-FAL §2.2.2 — `Vulnerabilities in the OT systems may increase the operational safety risks of ships`. 그래서 **OT는 IT로부터 분리되어야 하고, 인터넷 접점으로부터 보호되어야 한다**고 명시한다.
- BIMCO v5 §1.4 — OT는 선박의 필수 구성요소이며 **IT 시스템과 독립적으로 기능해야 한다**.
- NIST SP 800-82r3 §2.4 — OT는 시간 임계적(time-critical)이며 결정론적 응답이 요구된다. IT는 높은 처리량이 필요하고 지연·지터를 어느 정도 감내한다. OT의 예기치 않은 중단은 **허용되지 않으며**, 정지는 며칠~몇 주 전에 계획되어야 한다.

[INFERENCE] 이것이 [[Cyber Resilience]] 정의가 OT로 한정되는 이유이자, E27 §2.3이 "보안 조치가 필수 시스템의 가용성을 해쳐서는 안 된다"고 규정하는 이유로 보인다. → [[Essential Services]]

## Key Characteristics

[SOURCE] NIST SP 800-82r3 §2.4가 제시하는 OT 특성:

| 항목 | OT | IT |
| --- | --- | --- |
| 시간 요구 | 시간 임계적, 결정론적 응답 필요. RTOS 사용 多 | 지연·지터 일부 감내 가능 |
| 처리량 | 높은 처리량은 대체로 불필요 | 높은 처리량 필요 |
| 가용성 | 연속 운전. 예기치 않은 중단 **허용 불가** | 상대적으로 유연 |
| 정지 | 수일~수주 전 계획 필요 | 수시 가능 |
| 배포 전 시험 | 철저한 사전 시험이 필수 | — |

[SOURCE] BIMCO v5 §1.4의 조직적 차이:

- OT 구매에 IT 관리자가 보통 관여하지 않는다.
- OT 소프트웨어 갱신은 제조사가 수행하며 **변경관리·호환성 검토·선급 승인**을 수반한다. IT 소프트웨어는 통상 일상적으로 갱신된다.
- 따라서 사이버보안 책임자가 **OT 시스템 인벤토리**를 갖는 것이 유리하다. → [[Computer Based System]]

## Related Concepts

- [[Computer Based System]] — IMO 정의에서 IT/OT의 상위 개념
- [[Essential Services]] — OT 가용성이 왜 안전 문제인가
- [[Security Zone]] — IT/OT 분리를 구현하는 수단
- [[Untrusted Network]] — IT망이 OT 관점에서 갖는 지위
- [[Defence in Depth]]
- [[Cyber Resilience]]

## Applications

| 문서 | IT/OT 구분이 쓰이는 지점 |
| --- | --- |
| MSC-FAL | §2.2.2 OT의 IT로부터의 분리, §3.5.3.3 `segment OT device networks from IT networks` |
| UR E26 | §4.2.1.3 — 항해·통신 시스템은 기관·화물 시스템과 **같은 보안 존에 두지 않는다** |
| BIMCO v5 | §1.4 차이 설명, ANNEX 1 선내 IT·OT 시스템 목록 |
| NIST SP 800-82r3 | §2.4 비교, §5 OT 전용 아키텍처 |
| IEC 62443-2-1 | §8.2.1 비IACS 존과의 분리 |

## Limitations

- [SOURCE] BIMCO v5 §1.4 — 전통적으로 분리되어 있었으나 인터넷으로 인해 **양자가 가까워지고 있다**. 독립 시스템이었던 것이 통합되고 있다.
- [SOURCE] NIST SP 800-82r3 §2.4 — OT가 IT 기술(표준 컴퓨터·OS·네트워크 프로토콜)을 채택하면서 IT 시스템을 점점 닮아가고 있고, 그 결과 **외부로부터의 격리 수준이 이전 세대보다 현저히 낮아졌다.**
- [INFERENCE] 따라서 IT/OT 이분법은 설계 원칙으로는 유효하나, 실제 선박에서 경계가 어디인지는 사례별 판단이 필요하다. [[Onboard System Index]]의 스마트십 플랫폼(HS4, K-IMS, ISS 등)이 대표적인 경계 사례로 보인다. [확인 필요]

## Sources

- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §2.1, §2.2.2, §3.5.3.3
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §2, §4.2.1.3
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §1.4, ANNEX 1
- `Database/NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` §2.4
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.24, §4.1.38, §4.1.39

## Notes

파생 문서 `해양 사이버보안 IT-OT 모니터링 가이드`(내부작성·미검증) §0.1에도 IT/OT 비교표가 있으나, 원본 대조 전까지 근거로 쓰지 않는다. → [[Database Inventory#4. 원본과 대조되지 않는 서술 (확인 필요 목록)]]
