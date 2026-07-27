## 1. EU
1. EU NIS 2 지침
	- 대응은 NIST CSF(미국)
	- 관련 적용 범위 : 해상 수송(선사, 항만 시설, 운항 관리 시스템 등)을 Essential Entity로 분류하여 법적 규제 대상에 포함 => NIST CSF도 이렇게 분류가 되어있는 지 확인
	- <주요 챕터>
		- 제 21조(위협 관리 조치) : NIST CSF의 5대 기능에 대응 / 기술적, 조직적 위험 관리 10대 의무 사항을 명시
		- 제 22조(지배구조 및 이사회 책임) : 최고 경영진/이사회에 사이버보안 승인 및 관리 책임 법제화
		- 제 23조(침해사고 보고 의무) - 미국 CIRCIA와 유사
2. CRA, Regulation (EU) 2024/2847 / EU 사이버 복원력 법
	- 대응 : NIST SP 800-161(공급망 보안) 및 CISA Secure by Design 가이드라인
	- 관련 적용 범위 : EU시장에 공급되는 digital elements 전체
	- <주요 챕터>
		- 부속서 1(Annex I - 필수 사이버보안 요구사항) : 제품 개발 단계부터 통제되어야 하는 기술 제어요건
			- Part I sec.1 : Risk-based 설계 및 초기 설정 시 기본 보안
			- Part I sec.3 : 접근 제어, 무결성 보장 및 암호화를 통한 데이터 보호
			- Part II : SBOM 작성 의무화 및 취약점 패치/지급 기간 명시 요구
3. ENISA 위협 분석 및 해사 가이드라인 (ETL & Maritime Security)
	- 대응 : MITRE ATT&CK 및 NIST SP 800-82(OT 보안)
	- 해사 적용 범위 : 유럽연합 사이버보안청(ENISA)이 발간하는 해사 전용 프레임워크 및 공격 기법 분류
	- <주요 구성 요소>
		- ENISA Threat Landscape (ETL) Annex A : 공격자의 TTP를 MITRE ATT&CK 프레임워크 매핑 체계로 표준화하여 제시
		- ENISA Guidelines for Maritime Transport : 선박(IT/OT 융합 환경) 및 항만 시스템에 특화된 위험 평가 방법론 제공
4. TIBER-EU (Threat Intelligence-based Ethical Red Teaming)
	- 대응 : MITRE ATT&CK 기반 실전 레드티밍 및 CISA Red Teaming 가이드
	- 해사 적용 범위 : 실제 해사 그룹의 TTP를 MITRE ATT&CK 위협 인텔리전스 기반으로 시나리오화하여 중요 시스템(해운선사 및 항만 핵심 인프라)의 실전 방어력을 검증
## 2. 미국
1. USCG 33 CFR Part 101 Subpart F(해사 연방 규정집)
	- 주요 성격 : 미국 최초의 강제성 있는 해사 사이버보안 연방 규정(의무 규정)
	- 타겟 : US-flagged 선박, 해상 Platform, 미국 내 MTSA 규제 대상 항만/터미널
	- 주요 요건
		- Cybersecurity Officer 지정
		- CSP(Cyber Security Plan) 제출 : 사이버 위험 평가를 바탕으로 작성된 CSP를 USCG에 제출 및 승인 취득
		- 실시간 침해사고 보고
		- OT/IT 기술적 통제
2. USCG NVIC 01-20 (항행 및 선박 검사 회람)
	- 해사 운송 보안법(MTSA) 대상 시설 및 선박을 위한 사이버 위험 관리 가이드라인
	- 핵심 내용 
		- NIST CSF 개념을 해사 환경(FSA: 시설보안평가, FSP: 시설보안계획)에 맞게 이식한 실무 가이드
		- 선박 및 항만 시설의 IT(업무용 네트워크)와 OT(하역 크레인, Access Control, SCADA, CCTV등) 자산의 사이버 위협을 평가하고 최소화하는 세부 절차 제공
3. NIST IR 8323(Maritime Cybersecurity Profile)
	- 주요 성격 : NIST CSF 1.1/2.0을 해사(Maritime) 산업 특화 버전으로 패치한 프로파일
	- 핵심 내용
		- NIST CSF의 5대 기능(Identify, Protect, Detect, Respond, Recover)을 해사 운영 환경(Cargo Handling, Vessel Positioning, Navigation Systems, Engine Control등)의 용어와 시나리오에 맞춰 재해석
		- 선박이 운항 중 위성통신(VSAT)이 끊기거나 고립된 상태에서의 탐지 및 대응 가이드를 표준으로 제시
4. CISA Maritime Cyber Strategy & USCG Cyber Strategy
	- 성격 : 미국 국토안보부 상타 CISA와 USCF가 공동으로 추진하는 해상 공급망 및 융합 제어 시스템(ICS/OT) 위협 대응 전략
	- 핵심 내용
		- Secure by Design : 선박 제조시 탑재되는 항해/기관 제어 소프트웨어가 설계 단계부터 보안성을 확보하도록 요구
		- 해사 전용 위협 인텔리전스 공유 : CISA와 USCG가 수집한 해사 특화 취협을 해운업계에 실시간 전파
## 3. 한국
- EU는 법적 강제성, 미국은 연방 규정을 통해 해사 사이버보안 통제 체계를 구축
- but, 한국은 행정 지침, 선급(KR) 검사 체계, KISA 보안 모델을 중심으로 가이드라인 및 실무 지원 형태
1. 해양수산부 - 해사 사이버안전 관리 지침
	- IMO의 해상 사이버 위험관리 지침과 미국 NIST CSF의 5대 기능 체계를 국내 해사 환경에 맞춰 이식
	- 해사안전법상 안전관리체제(SMS)를 수립해야 하는 선박 및 선주/사업장에 대해 선고, 화물, 추진/기관 제어 등 주요 OT/IT 자산에 대한 리스크 평가 및 보호 조치 수립 권고
2. 국가 표준 보안 모델 : KISA
	  - 자율운항 선박 보안 모델 : IMO 자운운하 