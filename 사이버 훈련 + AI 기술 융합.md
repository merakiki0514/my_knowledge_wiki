## 3.1 AiCEF: an AI-assisted cyber exercise content generation framework using named entity recognition

이 논문은 공개 사이버 보안 기사로부터 NER, 토픽 추출, 군집화, 그래프 비교, 합성 텍스트 생성을 결합해 **훈련 콘텐츠를 자동 생성**합니다.acm+1  
논문의 핵심 AI 역할은 “새로운 위협을 빠르게 구조화해 tabletop exercise 시나리오 뼈대를 만드는 것”이며, 전문가 평가로 실용성을 검증했습니다.ettrends.etri+1  
정식 DOI는 `10.1007/s10207-023-00693-z`이고, 공식 URL은 ACM 페이지입니다.acm+1  
해양 적용 측면에서는, 항만 랜섬웨어, 선박 항법망 침투, 위성통신 장애, ECDIS 오작동 같은 사건을 **기사 기반으로 자동 조립하는 ship/port exercise generator**로 이식할 수 있습니다.acm+1  
한계는 공개 기사 중심이라 실제 OT 로그·운항 데이터가 부족하고, 생성 시나리오가 선박 제어계의 물리 제약을 충분히 반영하지 못한다는 점입니다.ettrends.etri+1  
저자들은 자동화된 exercise content generation과 ontology 기반 표현의 확장 가능성을 제시했습니다.acm+1

## 3.2 Toward AI-Based Scenario Management for Cyber Range Training

이 논문은 cyber range 훈련의 시나리오 관리 자체에 AI를 적용하려는 초기 방향을 제시한 연구입니다.acm+1  
확인 가능한 메타데이터상 2021년에 출판되었고, DOI는 `10.1007/978-3-030-90963-5_32`입니다.acm+1  
주요 기여는 훈련 중 시나리오를 정적 자산이 아니라 **AI가 동적으로 관리·조정할 수 있는 대상**으로 본 점입니다.[acm](https://dl.acm.org/doi/10.1007/978-3-030-90963-5_32)  
해양 분야에선 선박 운항 단계, 항만 혼잡도, 통신 가용성, 기상 변화에 따라 난이도를 바꾸는 **적응형 maritime exercise manager**로 확장 가치가 큽니다.acm+1  
다만 검색 결과로는 실험 세부가 제한적으로 드러나며, 대규모 검증과 실제 운영 환경 이식성은 더 필요합니다.acm+1

## 3.3 A Multiagent CyberBattleSim for RL Cyber Operation Agents

이 논문은 CyberBattleSim을 확장해 **적대적 multi-agent RL 환경**에서 red agent와 blue agent를 함께 학습합니다.[arxiv](https://arxiv.org/abs/2304.11052)  
핵심 결과는 blue agent를 혼자 훈련하는 것보다 red와 공동 훈련할 때 방어 성능이 향상된다는 점입니다.[arxiv](https://arxiv.org/abs/2304.11052)  
정식 DOI는 arXiv-issued DOI `10.48550/arXiv.2304.11052`이며, 공개된 대체 URL은 arXiv입니다.[arxiv](https://arxiv.org/abs/2304.11052)  
해양 적용에서는 선박 내부 IT/OT 분리망에서 lateral movement, 계정 탈취, 원격 유지보수 경로를 학습하는 **shipboard attack-defense sandbox**로 자연스럽게 전환할 수 있습니다.arxiv+1  
한계는 enterprise 네트워크 중심 설계라, ECDIS·engine control·satcom·bridge system처럼 안전제약이 큰 해양 시스템 특성을 아직 직접 다루지 못한다는 점입니다.[arxiv](https://arxiv.org/abs/2304.11052)  
저자들은 더 정교한 attacker/defender 공동 학습과 network topology 일반화 가능성을 보여줍니다.[arxiv](https://arxiv.org/abs/2304.11052)

## 3.4 Knowledge guided Two-player Reinforcement Learning for Cyber Attacks and Defenses

이 연구는 CyberBattleSim에 **사이버 지식그래프**를 결합해 공격·방어 RL 에이전트의 수렴을 가속합니다.[ebiquity.umbc](https://ebiquity.umbc.edu/paper/html/id/1047/Knowledge-guided-Two-player-Reinforcement-Learning-for-Cyber-Attacks-and-Defenses)  
AI 역할은 보상학습만으로는 느린 탐색을, 전문가 지식 기반의 path guidance로 보완하는 것입니다.[ebiquity.umbc](https://ebiquity.umbc.edu/paper/html/id/1047/Knowledge-guided-Two-player-Reinforcement-Learning-for-Cyber-Attacks-and-Defenses)  
DOI는 `10.1109/ICMLA55696.2022.00213`입니다.[ebiquity.umbc](https://ebiquity.umbc.edu/paper/html/id/1047/Knowledge-guided-Two-player-Reinforcement-Learning-for-Cyber-Attacks-and-Defenses)  
해양에서는 IEC 62443, IMO Cyber Risk Management, UR E26/E27, 선박 취약점 지식그래프를 학습 신호로 써서 **규정 준수형 방어 정책**을 훈련하는 방식이 가능해집니다.smartmaritimenetwork+1  
하지만 실제 해양 규정·장비 상호의존성까지 통합한 지식그래프는 아직 부족합니다.smartmaritimenetwork+1  
저자들은 지식 주입이 RL 수렴과 성능을 개선한다고 주장합니다.[ebiquity.umbc](https://ebiquity.umbc.edu/paper/html/id/1047/Knowledge-guided-Two-player-Reinforcement-Learning-for-Cyber-Attacks-and-Defenses)

## 3.5 Assessing the Effectiveness of Deception-Based Cyber Defense with CyberBattleSim

이 논문은 CyberBattleSim을 사용해 **deception-based defense**의 효과를 평가합니다.[eudl](https://eudl.eu/doi/10.1007/978-3-031-56583-0_15)  
핵심은 공격자 오판을 유도하는 허니팟, 미끼 자산, 허위 경로를 cyber range에서 정량적으로 측정한 점입니다.[eudl](https://eudl.eu/doi/10.1007/978-3-031-56583-0_15)  
DOI는 `10.1007/978-3-031-56583-0_15`입니다.[eudl](https://eudl.eu/doi/10.1007/978-3-031-56583-0_15)  
해양에선 항만 OT 네트워크, 원격 접속 경로, 선박 관리망에 미끼 장비를 배치해 공격자의 reconnaissance를 탐지하는 **maritime deception range**로 확장 가능합니다.eudl+1  
한계는 deception의 물리·운항 안전 영향이 고려되지 않았다는 점입니다.[eudl](https://eudl.eu/doi/10.1007/978-3-031-56583-0_15)  
저자들은 CyberBattleSim으로 deception 효과를 체계적으로 비교할 수 있음을 보였습니다.[eudl](https://eudl.eu/doi/10.1007/978-3-031-56583-0_15)

## 3.6 Simulating Network Lateral Movements through the CyberBattleSim Web Platform

이 논문은 CyberBattleSim을 웹 기반으로 조작 가능하게 만들어 네트워크 토폴로지 시뮬레이션과 자동 공격자를 다룹니다.[dspace.mit](https://dspace.mit.edu/handle/1721.1/143191)  
AI 역할은 Q-learning 전략 평가와 공격 진행 경로 분석입니다.[dspace.mit](https://dspace.mit.edu/handle/1721.1/143191)  
이 작업은 정식 학술 저장소에 보관된 석사논문 성격이지만, 실제 구현 가치가 높습니다.[dspace.mit](https://dspace.mit.edu/handle/1721.1/143191)  
해양 분야에서는 선박의 구역별 네트워크 분리, 유지보수 포트, 위성통신 게이트웨이를 모델링하는 **shipboard lateral-movement trainer**로 매우 유용합니다.[dspace.mit](https://dspace.mit.edu/handle/1721.1/143191)  
한계는 실제 선박 프로토콜과 안전 인터락이 반영되지 않은 범용 기업망 모델이라는 점입니다.[dspace.mit](https://dspace.mit.edu/handle/1721.1/143191)  
저자는 다양한 토폴로지에서 공격 진행을 관찰하고 대응 계획을 만드는 데 도움이 된다고 설명합니다.

## 3.8 AI-Driven Multi-Agent System for adaptive cyber attack simulation

2026년 Sci Rep 논문은 AI 기반 MAS가 공격 시뮬레이션과 incident response를 동시에 자동화한다고 보고합니다.[nature](https://www.nature.com/articles/s41598-026-45937-9)  
이 연구는 CICIDS2017과 UNSW-NB15를 CyDER 2.0 시뮬레이터에 결합하고, RL과 anomaly detection으로 adaptive agent를 구성했습니다.[nature](https://www.nature.com/articles/s41598-026-45937-9)  
정식 DOI는 `10.1038/s41598-026-45937-9`입니다.[nature](https://www.nature.com/articles/s41598-026-45937-9)  
해양에서는 항만 SOC, 선박 원격운용센터, 플릿 관리 환경에서 **자동화된 대응 연습 엔진**으로 옮길 수 있습니다.nature+1  
한계는 데이터셋이 일반 침입탐지용이라 maritime protocol, timing, safety constraints를 반영하지 못한다는 점입니다.[nature](https://www.nature.com/articles/s41598-026-45937-9)  
저자들은 static/rule-based 시스템보다 높은 현실성, 응답성, 탐지 성능을 제시합니다.[nature](https://www.nature.com/articles/s41598-026-45937-9)

## 3.9 GenAI-Powered Autonomous Cyber Offense-Defense

이 2026년 논문은 LLM이 red team과 blue team을 함께 제어하는 **closed-loop offense-defense framework**를 제안합니다.[techscience](https://www.techscience.com/JCS/v8n1/67431)  
공격 계획, 자연어 설명, 자가 학습 정책 갱신을 결합하고, 설명 가능성이 인간 신뢰와 정렬을 크게 높였다고 보고합니다.[techscience](https://www.techscience.com/JCS/v8n1/67431)  
공식 DOI는 아직 본문에서 명시된 저널 DOI 체계로 확인되며, 웹 결과에서는 `Journal of Cyber Security`의 2026년 1권 논문으로 제시됩니다.[techscience](https://www.techscience.com/JCS/v8n1/67431)  
해양 분야에서 이 방식은 선박 운항자, 항만 운영자, 훈련생에게 **설명 가능한 AI 교관** 역할을 할 수 있습니다.techscience+1  
다만 enterprise testbed 중심이며, 안전 필수 영역의 해양 제어 시스템으로 바로 전환하기에는 검증이 부족합니다.[techscience](https://www.techscience.com/JCS/v8n1/67431)  
저자들은 AI-on-AI red-blue co-evolution과 설명가능성의 중요성을 강조합니다.[techscience](https://www.techscience.com/JCS/v8n1/67431)