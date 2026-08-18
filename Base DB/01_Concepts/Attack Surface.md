---
type: concept
tags:
  - concept
---

# Attack Surface

## Definition

⚠️ **IACS UR과 Rec 166의 정의 범위가 다르다.** [SOURCE]

### 넓은 정의 — 디지털 + 물리 (E26 / E27)

> The set of all possible points where an unauthorized user can access a system, cause an effect on or extract data from. The attack surface comprises two categories: digital and physical.
> — UR E26 §2 (UR E27 §1.4도 동일)

- **디지털 공격면**: 조직 네트워크에 연결되는 모든 하드웨어·소프트웨어 — 애플리케이션, 코드, 포트, 서버, 웹사이트
- **물리 공격면**: 공격자가 물리적으로 접근 가능한 모든 엔드포인트 — 데스크톱, 하드드라이브, 노트북, 휴대전화, 이동식 드라이브, **부주의하게 폐기된 하드웨어**

### 좁은 정의 — 외부 접근 가능한 CBS (Rec 166)

IACS Rec 166 §4.1.2는 `The computer based systems which can be accessed externally...`로 정의를 시작한다. **외부 접근 가능성**으로 한정되어 E26/E27보다 좁다.

[INFERENCE] E26·E27이 물리 공격면과 폐기 하드웨어까지 포함하는 반면 Rec 166은 외부 접근 가능한 CBS에 초점을 둔다. 인용 시 어느 정의인지 명시할 것.

## Why it matters

[SOURCE] E26 §3에서 공격면은 요건 설계의 기준이다. E26 §1(Introduction)이 `minimum requirements applied consistently to the **full threat surface** using a goal-based approach`를 명시한다.

[SOURCE] E26 §4.2.1.3 — [[Security Zone]] 분할의 첫 번째 목적이 `reduce the extent of the attack surface`다.

[SOURCE] MSC-FAL §2.2.1 — 사이버 위협·리스크로 이어지는 것은 시스템에 **접근·상호연결·네트워크화**할 때 생기는 취약점이다. 즉 연결이 곧 공격면이다.

[SOURCE] NIST SP 800-82r3 §2.4 — OT가 IT 기술을 채택하면서 이전 세대보다 외부로부터의 격리 수준이 현저히 낮아졌고, 그만큼 보안 필요성이 커졌다. → [[IT and OT]]

강의 노트 `9. Frontiers/1. The Emerging Threat Landscape.txt` §9.1.3 `Increased Connectivity and the Expanding Attack Surface`도 같은 주제를 다루나 **2차 자료**다.

## Key Characteristics

| 구분 | 포함되는 것 (E26 §2) |
| --- | --- |
| 디지털 | 애플리케이션, 코드, 포트, 서버, 웹사이트, 네트워크 연결 하드웨어·소프트웨어 |
| 물리 | 데스크톱, 하드드라이브, 노트북, 휴대전화, 이동식 드라이브, 폐기 하드웨어 |

[INFERENCE] **폐기 하드웨어가 정의에 명시되어 있다**는 점이 특징적이다. BIMCO v5 §7.3 `Equipment disposal including data destruction`이 이에 대응하는 운영 조치로 보인다.

## Related Concepts

- [[Security Zone]] — 공격면을 줄이는 수단
- [[Untrusted Network]] — 공격면을 만드는 연결
- [[Computer Based System]] — 공격면을 갖는 대상
- [[Defence in Depth]]
- [[Cyber Risk Management]] — Rec 171 §7.2.3이 공격면을 등급으로 평가
- [[Cyber Resilience]]

## Applications

| 문서 | 위치 |
| --- | --- |
| **IACS Rec 171** | **§7.2.3 Attack Surface (AS) grade assessment** — 공격면을 등급화해 발생가능성 산정에 사용 |
| UR E26 | §2 정의 / §1 도입 / §4.2.1.3 존 분할의 목적 |
| BIMCO v5 | §3 취약점 식별, §7.3 장비 폐기 및 데이터 파기 |
| Rec 190 | §6.1 컬럼 Q(물리 인터페이스), R(지원 프로토콜), P(비신뢰망 연결) — 공격면 기록 |
| MSC-FAL | §2.2.1, §2.2.5 |

[INFERENCE] Rec 190 자산 목록의 컬럼 P·Q·R을 채우는 작업이 사실상 공격면 목록화 작업이 된다. [[Onboard System Index]]의 110종에는 이 세 컬럼이 비어 있다.

## Limitations

- [확인 필요] E26 §2 정의의 디지털 공격면 예시(`웹사이트`)는 일반 IT 문헌의 표현을 그대로 옮긴 것으로 보인다. 선박 OT 환경에 그대로 대응하지 않는 항목이 있다.
- [확인 필요] Rec 166과 E26의 정의 차이가 의도적인지, 발행 시점 차이(2020 vs 2023)에 따른 것인지 확인하지 않았다.

## Sources

- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §1, §2, §4.2.1.3
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.4
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.2
- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` §7.2.3
- `Database/IACS-Rec-190-Jun-2025-Vessel-Asset-Inventory.pdf` §6.1
- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §2.2.1, §2.2.5

## Notes

Rec 171 §7.2는 발생가능성을 복잡도(CX)·연결성(CY)·**공격면(AS)**·사용자(US)·공격자수준(AT)·인적요인(H) 6개 등급으로 산정한다. 공격면은 그중 하나의 축이다.
