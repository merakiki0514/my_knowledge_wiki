# 1. EU Cyber-MAR
## 전체 아키텍처 (3계층(Technologies - People - Procedure))
### 핵심 구성요소
1. Orchestrator : 전체 시스템의 메인 컨트롤러 / 모든 컴포넌트를 동기화하고 임의의 토폴로지와 공격 시나리오를 구동하며 공통 API를 제공
2. DIATEAM CyberRange : 가상 환경 생성/관리, 실제 IT/OT 장비와 연동, 모든 VM에 대한 뷰 및 상호작용 제공
3. VTT Tools : 오픈소스 네트워크 모니터링 도구 집합, LMS(Learning Management System), 보안 경고 수집/대시보드 제공, 기술 전문가용 및 고위급 관리자용 모듈 2개
4. SIEM/ADS : 보안 이벤트 상관관계 분석, 실시간 네트워크 흐름 기반 행동 분석, 시스템 구성 업데이트 지점 식별
5. MISP(Malware Information Sharing Platform) : 실제 기술/운영 데이터 기반 공격 시나리오 기록 및 재생, CERT/CSIRT 간 정보공유 연동
6. MaCRA Framework : 사이버 위험 노출 평가 프레임 워크
7. Econometic Model : 공격 시나리오의 경제적 영향(다운타임, 복구 시간 등 ) 평가
8. Recommendation Engine : inflict risk + 경제모델 비실시간 평가, 포트 토폴로지/트래픽/MISP 데이터/시나리오 입력
9. Ship Simulator : 선박 시뮬레이터(Plymouth 대학) 연동, 항해/제어 시스템 공격 시나리오 수행
# 2. NTNU

# 3. Ploymouth
- 하드웨어 기반 선박 사이버보안 연구 플랫폼
- 실제 선박 브리지에 탐
# 4. 독일