# 논문1 핵심 자료 종합 (가다듬기)

작성 2026-08-14. 통합 분석노트(../../llm_wiki/)에서 논문1에 직접 쓰이는 것만 추려 **전이(transfer) 서사** 축으로 재배치.

## 논문1의 3단 논증과 근거 배치

### 1단 — "육상에서 AI 공격이 여기까지 왔다" (성숙도)
| 근거 | 무엇을 뒷받침 | 위치 |
|---|---|---|
| 정태진 2024 | 딥페이크·ChatGPT 스피어피싱·허위정보 (국내 인용) | papers/ · [note](../../llm_wiki/2024_chung_ai-cyberthreat-overseas-cases.md) |
| Heiding 2024 (LLM 스피어피싱) | LLM 완전자동 피싱 클릭률 54% = 인간 전문가 동등, 정보수집 정확도 88% | Cases/2412.00586v1.pdf |
| Jing/Wang 2024 (LLM 피싱탐지) | 방어측 LLM 탐지 성능·한계 | Cases/3_iis_2024_327-341.pdf |
| MS Digital Defense Report 2025 | 위협행위자의 AI 도구 사용 동향(규모) | Cases/Microsoft-...2025.pdf |
| advances-in-threat-actor-usage-of-ai | 실제 위협행위자 AI 활용 정리 | Cases/advances-...en.pdf |
| first AI-orchestrated espionage | AI 에이전트 주도 공격 실사례 | Cases/Disrupting the first...pdf |
| 13가지 생성형 AI 공격 수법 | 공격 기법 카탈로그 | Cases/'13가지...ITWorld.pdf |

### 2단 — "해상 IT/OT는 이렇게 뚫린다" (공격표면)
| 근거 | 무엇을 뒷받침 | 위치 |
|---|---|---|
| Li 2024 survey | AIS/GNSS/ECDIS/RADAR/VSAT/GMDSS 시스템별 취약점 (부록 컴포넌트 목록) | [note](../../llm_wiki/2024_li_maritime-cyber-survey.md) |
| 기본 아키텍쳐.drawio | 신조선 IT/OT 노드(M/E,G/E,ICMS,Navigation,Cargo,VSAT/LEO…) | ../../experiment/ |
| 유지운 2022 | 자율선박 AI 적용지점·위협 범주 | [note](../../llm_wiki/2022_yu-jiwoon_autonomous-ship-ai-threats.md) |
| Neumann 2024 | IT/OT 융합·규정 배경(IMO/NIST/SMS) | [note](../../llm_wiki/2024_neumann_cybersecurity-maritime-industry.md) |

### 3단 — "결합되면 사고 심각도가 이만큼 오른다" (전이+심각도)
| 근거 | 무엇을 뒷받침 | 위치 |
|---|---|---|
| Maritime accident.csv | 10대 사고 피해/원인 (Herald, El Faro, Dali, NotPetya, Ever Given…) | ../../Cases/ |
| Herald of Free Enterprise 조사보고서 | 절차·소통 실패형 방벽 | ../../Cases/FormalInvestigation...pdf |
| Cichocki 2025 | GPS 스푸핑→grounding 등 결합 서사(최근접 선행) | [note](../../llm_wiki/2025_cichocki_ai-dualuse.md) |

## 차별화 (Related Work 핵심 문장 재료)
- **Cichocki 2025 = 가장 가까운 선행.** 공격/방어 이중용도를 "나열"함. → 논문1은 (a) 육상→해상 **전이 경로의 구조화**, (b) **실제 사고 방벽에 대한 심각도 투영**으로 넘어선다.
- 공격측 AI를 해사 도메인에서 **사고 심각도까지 이은 연구는 매트릭스상 비어 있음**(../../llm_wiki/2026-08-14_literature-matrix.md B절).

## 반사실 프레이밍 (필수)
Dali·El Faro는 실제로는 사이버 사고 아님 → "동일 방벽 구조에 AI공격이 결합됐다면"으로 서술. Herald는 사이버 이전 시대 사례 = baseline.

## 확인 필요
- Cases/ 각 리포트가 실제로 위 주장을 뒷받침하는지 본문 확인(특히 MS MDDR 규모 수치, first AI-orchestrated espionage의 자율성 수준)
- Heiding 수치(54%/88%) 본문 재확인
