# Walter et al. 2023 — A Red Teaming Framework for Securing AI in Maritime Autonomous Systems

- 출처: arXiv:2312.11500v1 (30p). Walter, Barrett, Tam (Univ. Plymouth / Alan Turing Institute).
- 분류: reference. **논문3(공격능력 평가)·논문2(위협모델링)의 방법론 앵커.**

## 1. 연구 목적
해상 자율시스템(MAS)의 AI 보안을 평가하는 **레드팀 프레임워크**(최초급) 제안. [논문 내용]

## 2. 연구 문제
AI는 불투명·취약하여 adversarial AI로 악용 시 사이버+물리 위험. 실세계 영향 이해와 AI 보안검증이 부족. [논문 내용]

## 3. 연구 대상
실제 MAS AI(객체탐지 등). 선제(secure-by-design) + 사후(post-deployment) 평가. [논문 내용]

## 4. 연구 방법
시스템/요구사항별로 맞춤 가능한 **다부분 체크리스트** 프레임워크 → 실제 MAS AI에 레드팀 적용. [논문 내용]

## 5. 핵심 결과
실제 시스템에서 **poisoning ~ adversarial patch** 등 다수 취약점 발견. 저엔트로피 실험실 결과가 실세계에서 다르게 작동함을 지적. [논문 내용]

## 6. 기존 연구와 차이
MAS 특화 AI 레드팀 프레임워크는 사실상 최초. 미국 정부의 mission-critical AI 레드팀 요구(2023.11) 흐름과 정합. [논문 내용]

## 7. 한계
체크리스트 기반 → 자동화·정량 커버리지 제한. 특정 시스템 사례 중심 일반화 주의. [추론]

## 8. 내가 가져갈 것
- 논문3 공격 에이전트의 **평가 축**(레드팀 체크리스트 → 능력평가 하네스 항목화).
- 논문2에서 "AI 자체 취약점(poisoning/adversarial)"을 방벽 무력화 경로로 편입.

## 9. 내 연구와의 관계
**확장.** 이들은 사람이 수행하는 레드팀, 나는 **로컬 LLM 자율 에이전트**가 수행 → 자동화가 신규성.
