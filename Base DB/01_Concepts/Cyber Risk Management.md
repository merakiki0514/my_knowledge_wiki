---
type: concept
tags:
  - concept
  - risk
---

# Cyber Risk Management

## Definition

[SOURCE] IMO MSC-FAL.1/Circ.3/Rev.3 §2.1 (§3.1에 동일 문언 반복)

> The process of identifying, analysing, assessing and communicating a cyber-related risk and tolerating, terminating, transferring or treating it to an acceptable level by taking into consideration the costs and benefits of actions taken by stakeholders.

구조가 두 갈래다:

| 단계 | 행위 |
| --- | --- |
| 분석 | identify → analyse → assess → communicate |
| 처리 (4T) | **t**olerate / **t**erminate / **t**ransfer / **t**reat |

[SOURCE] MSC-FAL §1.1은 `maritime cyber risk`도 정의한다 — [[Computer Based System]]이 잠재적 상황·사건에 의해 위협받는 정도로서, 정보나 시스템의 손상·손실·훼손의 결과로 해운 관련 운항·안전·보안 실패를 초래할 수 있는 것.

IACS Rec 166 §4.1.11에도 정의가 있다. 문언 대조는 [확인 필요]

## Why it matters

[SOURCE] IMO는 사이버보안을 **기술 표준만으로는 다룰 수 없다**고 명시한다.

> These rapidly changing technologies and threats make it difficult to address these risks only through technical standards. As such, these Guidelines recommend a risk management approach...
> — MSC-FAL §2.2.7

[SOURCE] IACS Rec 171 §1 Foreword — IMO는 사이버보안을 **ISM Code의 기존 목표와 기능 요건에 따라** 다루기로 결정했다. 회사(DOC 보유자)는 기존 안전관리체계(SMS)를 사용해 리스크를 평가하고 안전장치를 구현한다.

[INFERENCE] 즉 사이버 리스크 관리는 새로운 별도 체계가 아니라 **기존 SMS에 통합되는 것**이 IMO의 방향이다. 이는 규정 준수 작업의 성격을 바꾼다.

## Key Characteristics

[SOURCE] **MSC-FAL Rev.3 §3.5의 기능요소 6개** — 순차적이지 않으며 동시·연속적으로 수행되어야 한다.

| 요소 | 내용 |
| --- | --- |
| **Govern** | 리스크 관리 전략·기대·정책 수립 및 감시, 역할·책임 정의, 업무연속성. 책임자 지정 및 권한·전문성 확보 (§3.5.1) |
| **Identify** | 시스템·자산·서비스·데이터·능력 식별, 안전 필수 시스템 간 상호의존성, **선내 디지털 시스템 인벤토리**, 리스크 평가 (§3.5.2) |
| **Protect** | 고유 자격증명, 기본 암호 변경·MFA, **OT망과 IT망 분리**, 이동식 매체 통제, **연간 교육**, 백업·업데이트·IR 계획, 공급망 보안, 효과성 감사 (§3.5.3) |
| **Detect** | 위협·위협행위자 TTP 목록 유지 및 모니터링 (§3.5.4) |
| **Respond** | 주관청이 정한 기한 내 보고, 사고 기록 보관 (§3.5.5) |
| **Recover** | 핵심 자산 복구 전략, **근본원인 분석** (§3.5.6) |

[SOURCE] §3.5는 각 요소 아래 통제항목을 `minimum controls that should be implemented`로 규정한다.

⚠️ **문서마다 기능요소 개수가 다르다.** MSC-FAL Rev.3와 NIST CSF 2.0만 `Govern`을 최상위에 둔다. UR E26·Rec 166·BIMCO v5는 5개다. → [[Database Inventory#3.1 기능요소 개수: IMO Rev.3(6개) vs IACS·BIMCO(5개)]]

## Related Concepts

- [[Cyber Incident]] — 리스크가 현실화된 것
- [[Cyber Resilience]] — IACS 측의 대응 개념
- [[Attack Surface]] — Rec 171 §7.2.3의 평가 축
- [[Computer Based System]] — 리스크 정의의 기준 단위
- [[System Category]] — Rec 171이 리스크 평가 입력으로 사용
- [[Defence in Depth]]

## Applications

### 정량 평가 방법론 — IACS Rec 171 §7

[SOURCE] 가장 구체적인 절차를 제공한다.

| 단계 | 조항 |
| --- | --- |
| 영향 평가 | §7.1 |
| 발생가능성 = 복잡도(CX) · 연결성(CY) · **공격면(AS)** · 사용자(US) · 공격자수준(AT) · 인적요인(H) | §7.2.1 ~ §7.2.6 |
| 발생가능성 등급 (L) | §7.3 |
| 리스크 등급 (RL) | §7.4 |
| 리스크 처리 | §7.5 |
| 잔여 리스크 (RRL) | §7.6 |
| 완화 조치 (비기술 / 기술) | §8.1 / §8.2 |

[SOURCE] Rec 171 §2.1.2 — 이 방법의 사용은 **의무가 아니며** 다른 방법을 쓸 수 있다.

### 그 밖의 문서

| 문서 | 위치 |
| --- | --- |
| MSC-FAL | §3.4 리스크 기반 접근 (선종·운항프로파일·복잡도·연결성 고려) |
| BIMCO v5 | §6.2 리스크 평가 4단계 / §2~§5 위협·취약점·발생가능성·영향 |
| UR E26 | §6 CBS 적용 제외를 위한 리스크 평가 |
| UR E22 | §4.3.4 시스템 리스크 평가 (통합자) |
| NIST SP 800-82r3 | §4.1 OT 리스크 관리 / §4.3 RMF 7단계 |
| IEC 62443-2-1 | §5.3.2 요건 대비 리스크 평가 / §6.3.1 리스크 완화 (조항 참조만) |

## Limitations

- [SOURCE] MSC-FAL §2.3.2 — 지침이 **광범위한 적용을 위해 넓은 용어로 표현**되어 있다. 디지털 시스템이 제한적인 선박은 단순 적용으로 충분할 수 있고, 복잡한 선박은 더 높은 수준의 주의가 필요하다.
- [SOURCE] MSC-FAL §1.3 — 구체적 리스크 관리 프로세스는 각 주관청 요구사항과 국제·산업 표준을 참조하라고 넘긴다. **MSC-FAL 자체는 절차를 제공하지 않는다.**
- [확인 필요] Rec 171의 정량 방법론이 UR E26 §6(적용 제외 리스크 평가)에서 인정되는지 확인하지 않았다.

## Sources

- `Database/MSC-FAL.1-Circ.3-Rev.3.pdf` §1.1, §1.3, §2.1, §2.2.7, §2.3.2, §3.1~§3.5
- `Database/IACS-Rec-171-May-2022-Cyber-Risk-Management-in-SMS.pdf` §1, §2.1.2, §7, §8
- `Database/NIST-CSWP-29-Cybersecurity-Framework-2.0-Feb-2024.pdf` §2
- `Database/NIST-SP-800-82r3-Sep-2023-FINAL-Guide-to-OT-Security.pdf` §4.1, §4.3
- `Database/BIMCO-Guidelines-on-Cyber-Security-Onboard-Ships-V5.pdf` §6.2
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §6
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` §4.1.11

## Notes

ISM Code 본체가 `Database/`에 없으므로 SMS 통합의 근거 조문은 직접 확인할 수 없다. 우회 경로는 [[Database Inventory#5.4 ISM Code — 무엇을 갖고 있고 무엇이 없는가]] 참조.
