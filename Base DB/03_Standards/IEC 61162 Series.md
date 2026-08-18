---
type: standard
tags:
  - standard
  - iec
  - protocol
---

# IEC 61162 Series

**Maritime navigation and radiocommunication equipment and systems — Digital interfaces**. 항해 장비 간 디지털 인터페이스 표준 계열.

⚠️ **이 계열은 `Database/` 최대의 공백이다.** 보유본은 -1의 **미리보기 14쪽**뿐이다.

## 왜 중요한가 — E26·E27이 대체 경로로 인정한다

[SOURCE] **[[UR E26]] §1.3.2**

> For navigation and radiocommunication systems, the application of **IEC 61162-460 or other equivalent standards in lieu of the required security capabilities in UR E27 section 4** may be accepted by the Society, on the condition that requirements in UR E26 are complied with.

[SOURCE] [[UR E27]] §1.3에도 동일한 취지의 조항이 있다.

[INFERENCE] 즉 **항해·무선 시스템은 IEC 61162-460으로 UR E27 §4의 보안능력 30개를 대체할 수 있다.** [[Onboard System Index]]의 H그룹(항해) 21종과 I그룹(무선통신) 6종이 여기에 해당할 수 있다. 규정 해석상 매우 중요한 경로인데, **-460 원문이 없어 내용을 확인할 수 없다.**

[SOURCE] [[IACS Rec 166]] Appendix A도 참조 표준으로 `IEC 61162`(§6)와 `IEC 61162-460 (2018)`(§16)을 열거한다.

## 보유 현황

| 파트 | 주제 | 보유 |
| --- | --- | --- |
| **-1** | Single talker and multiple listeners (시리얼) | △ **Ed.6.0 (2024-04) 미리보기 14쪽** |
| **-2** | 고속 전송 | ✘ 없음 |
| **-450** | Lightweight Ethernet (LWE) | ✘ 없음 |
| **-460** | **네트워크·보안 관련** | ✘ 없음 — **가장 필요** |

## IEC 61162-1 Ed.6.0 — 확인 가능한 범위

⚠️ 보유본은 `iTeh Standards / Document Preview` 워터마크가 있는 **미리보기 14쪽**이다.

### 확인 가능 [SOURCE]

**§1 Scope**

- 해양 전자 기기, 항해·무선통신 장비가 적절한 시스템으로 상호 연결될 때의 데이터 통신 요건
- **단일 talker → 하나 이상의 listener**로의 단방향 시리얼 전송 지원
- 데이터는 출력 가능한 ASCII 형태. 위치·속력·수심·주파수 할당 등의 정보 포함 가능
- 전형적 메시지는 약 **11~79자**, 일반적으로 **초당 1회보다 빠른 전송은 요구하지 않는다**
- 전기적 정의는 레이더·영상 같은 고대역폭 응용이나 집약적 DB·파일 전송을 수용하려는 것이 아니다
- **전달 보장이 없고 오류 검사 능력이 제한적**이므로 안전 응용에서는 주의해서 사용해야 한다
- **더 빠른 전송률이 필요한 응용에는 IEC 61162-2가 적용된다**
- 육상 기반 AIS 장비에는 IEC 62320 계열이 적용된다

**§2 인용 표준**: IEC 60945, ISO/IEC 8859-1:1998, ITU-T X.27/V.11:1996 등

**목차 구조**: §4 제조사 문서 / §5 하드웨어 규격 / §7 문장(sentence) 구조 / §8 데이터 내용

### 확인 불가 — 미리보기에 없음

| 항목 | 조항 |
| --- | --- |
| 하드웨어 규격 (배선·도체·차폐·커넥터·전기 신호 특성) | §5.2 ~ §5.6 |
| 문장 구조 (문자·필드·주소 필드·**체크섬 필드**) | §7.1 ~ §7.2 |
| 문장 유형 (파라메트릭·캡슐화·질의·독자·명령) | §7.3 |
| 오류 검출·처리 / 폐지 문장 처리 | §7.4 / §7.5 |
| **승인 문장 목록** (BOD, POS 등) | §8.3 |
| **전송 속도 수치** | — **파일 내 검색 결과 0건** |

⚠️ **4 800 bps / 38 400 bps 같은 수치는 이 미리보기로 검증되지 않는다.**

## 파생 문서와의 관계

⚠️ `Database/선박 프로토콜-통신 하드웨어 매칭 가이드 V2 (내부작성·미검증).docx`가 61162-1/-2/-450에 관한 서술을 담고 있으나, **원문이 없어 전면 미검증 상태다.**

[SOURCE] 미리보기로 **부분 확인된 것**: 61162-1이 단방향, 1 talker → 다수 listener 구조이고, 더 빠른 전송에는 -2가 적용된다는 점.
**검증되지 않은 것**: 전송 속도 수치, RS-422와의 대응, -450의 UDP 포트 대역, 멀티캐스트 구조 등.

→ [[Database Inventory#4. 원본과 대조되지 않는 서술 (확인 필요 목록)]]

## Practical Implications

[INFERENCE] 확보 우선순위:

1. **IEC 61162-460** — E26 §1.3.2·E27 §1.3의 대체 경로. **규정 해석에 직접 걸린다**
2. **IEC 61162-450** — 이더넷 항해망. 파생 docx 검증도 함께 해결
3. IEC 61162-2 — 고속 규격. -1 §1이 지시
4. IEC 61162-1 전문 — §7·§8 확보

이것들이 없는 동안 `02_Technologies/`의 항해 프로토콜 문서는 착수하지 않는다.
→ [[2026-08-18 Database 정리 작업 로그#9. 02_Technologies 착수 판단 (2026-08-18)]]

## Related Standards

- [[UR E26]] §1.3.2 · [[UR E27]] §1.3 — 대체 경로 조항
- [[IACS Rec 166]] Appendix A — 참조 표준 열거
- [[IACS Rec 190]] §6.1 컬럼 R — 프로토콜 기재 예시에 `NMEA 0183` 포함

## Related Concepts

[[Attack Surface]] · [[Security Zone]] · [[Computer Based System]]

## Sources

- `Database/IEC-61162-1-Ed6.0-2024-PREVIEW-14p-Digital-Interfaces-Single-Talker.pdf` **(미리보기)**
- `Database/UR-E26-Rev.1-Nov-2023-CR.pdf` §1.3.2
- `Database/UR-E27-Rev.1-Sep-2023-CLN.pdf` §1.3
- `Database/IACS-Rec-166-Corr.2-Apr-2022-Cyber-Resilience.pdf` Appendix A
- 조항 위치: [[Regulation Locator#17b. 항해 통신 인터페이스 (IEC 61162)]]
