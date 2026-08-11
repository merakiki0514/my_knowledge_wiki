# Project Overview(연구를 한 문단으로 소개하기)
IACS UR E26의 Critical Criteria, Additional Criteria를 기반으로 CBS에서 제외시켰을 때, 실제 발생할 수 있는 사이버 보안 취약점에 대해 연구와 방향성에 대한 학술대회용 논문을 작성 이후에 정식논문으로 발전하려고 한다.
정식 투고용 논문은 이러한 취약점을 바탕으로 선박 인프라전체에 대한 위협모델링 및 MASS code에 따른 자율운항선박의 위협모델링을 수행하는 것이다.
핵심 목표는 UR E26만 만족한다고 생각해 고려 CBS 대상에서 제외시키는 것이 오히려 취약점을 확대시키는 것을 확인하기 위함이다.
에이전트는 문헌 정리, 규정 정리, 논문초안 작성 및 검토, Related Work 초안 작성을 돕는다.

# Research Context(연구 질문과 맥락 적기)
연구 질문 : IACS UR E26에 근거해서 대상 CBS에서 제외시키는 것으로 충분할까?
자료 : IACS UR E26 규정, 국내외 학술논문, ISM Code, Mass code
방법론 : 규정으로 제외됬으나, 발생할 수 있는 취약점을 도출해내기
용어 : CBS = Computer Based System, NMEA = 선박용 데이터 프로토콜, IACS = 국제선급협회, 

# Preferred Outputs(받고 싶은 형식 정하기)
논문 요약 : 문제, 방법, 데이터, 결과, 한계, 관련성의 6행 표로
실험 로그 : 결과, 원인, 다음 액션의 세 줄로
문헌 비교 : 논문을 행, 기준을 열로 하는 litertature matrix 형태로

# Important Files
'papers/'   : 원본 논문 PDF
'rules/'    : 규정 PDF
'llm_wiki/' : 논문 요약, 비교, 해석 
'experiments/': 실험 계획과 결과 로그
'outputs/'  : 논문 초안, 발표 자료
papers와 llm_wiki를 섞지 말 것.

# Verification Rules
- 논문에 직접 적힌 내용은 '논문 내용', 해석은 '추론'으로 표시한다
- citation이 필요한 주장은 표시하고, 출처를 모르면 '확인 필요'로 남긴다. 지어내지 않는다
- 실험 결과는 데이터셋/metric/baseline/조건과 함께 적는다.
- 모르면 모른다고 말하고, 다음에 확인할 질문을 남긴다

# DO NOT TOUCH 
