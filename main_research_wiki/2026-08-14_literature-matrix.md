# Literature Matrix — 해사 AI 사이버보안 (papers/ 9편)

작성 2026-08-14. 새 논문 추가 시 행 추가하고 날짜 갱신. 표시: O=다룸, △=부분, X=안다룸.

## A. 종합 매트릭스

| # | 논문(연도) | 대상 시스템 | 공격측 | 방어측 | AI자체 취약점 | 방법론 | 실증/정량 | 사고연계 | 내 연구와의 관계 |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Li 2024 (survey) | AIS/GNSS/ECDIS/VDR/RADAR/VSAT/GMDSS | O | O | △ | 서베이+taxonomy | X | O | 참고+확장 |
| 2 | Cichocki 2025 (dual-use) | 해사 IT/OT, 자율선박, ICS | O | O | O | 서술 리뷰 | X | △ | **비교/경쟁(최근접)** |
| 3 | 유지운 2022 | 자율선박 AI, 선박시스템 | △ | △ | O | 개념 분석 | X | X | 참고 |
| 4 | Yoo 2023 (AI-SNSD) | MASS 선박-육상 네트워크 | X | O | X | 설계/인터페이스 정의 | X | △(NotPetya 언급) | 참고(형식)+확장 |
| 5 | Walter 2023 (red team) | MAS AI(객체탐지) | O | O | O | 레드팀 체크리스트 | O(취약점 발견) | X | **확장(자동화)** |
| 6 | VessiGuard 2026 | AIS/GPS + OT센서 | X | O | X | LSTM+IsolationForest | O(94.2/92.8%) | X | 비교/부분반박 |
| 7 | 김구경 2024 | 해안감시 YOLOv11 | O | X | O | adversarial patch 실험 | O(우회지표) | X | 참고/확장 |
| 8 | 정태진 2024 | 일반 사이버(비해사) | O | △ | X | 해외사례 서술 | X | △ | 참고 |
| 9 | Neumann 2024 | 해사산업/offshore, SMS | X | △ | X | 규정/거버넌스 리뷰 | X | X | 참고(규정) |

## B. 관찰 (gap 진술 재료)
- **공격측 AI를 정면으로 다룬 것**: Cichocki(서술), 김구경(적대적예제만), 정태진(비해사). → **해사 도메인 + 사고 심각도까지 이은 공격측 연구는 비어 있음.**
- **AI 자율 에이전트가 공격을 수행**하는 연구: 없음(Walter는 사람 레드팀). → 논문3 신규성.
- **실제 대형 사고의 방벽을 AI공격으로 무력화**하는 매핑: 없음. → 논문1·2 신규성.
- **방어 실증**: VessiGuard만 정량. 나머지는 서술/설계. 탐지지연·점진조작 약점 미검증 → 논문3 회피실험 여지.
- **KINPR 게재 형식 벤치마크**: Yoo 2023(동일 학회지, 동일 주제군).

## C. 논문1(위협 전이)에서의 역할 배치
- 육상 AI공격 성숙도 근거: 정태진 2024 + (Cases/) MS MDDR 2025, Heiding 2024, advances-in-threat-actor, first AI-orchestrated espionage
- 해사 IT/OT 공격표면: Li 2024 + drawio + 유지운 2022
- 최근접 선행(차별화 대상): Cichocki 2025
- 방어 gap: VessiGuard 2026, Yoo 2023
- 규정 배경: Neumann 2024

## 확인 필요
- 김구경 2024 본문 표의 우회율 실제 수치
- Cichocki가 언급한 "GPS 스푸핑으로 인한 grounding" 사건 특정
