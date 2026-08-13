# 분석 노트 — 위협 모델링을 이용한 선박 사이버보안 요구사항 연구

- 서지: 조용현, 차영균 (고려대 정보보호대학원), 정보보호학회논문지(JKIISC) Vol.29 No.3, pp.657-673, 2019.6
- DOI: 10.13089/JKIISC.2019.29.3.657
- 원문: `papers/위협 모델링을 이용한 선박 사이버보안 요구사항 연구 .pdf`
- 표기: `[논문]` = 원문에 직접 적힌 내용 / `[추론]` = 내 해석

## 요약 (6행)

| 항목 | 내용 |
|---|---|
| 문제 | 선박·조선 ICT 기자재 산업의 사이버보안 연구가 부족하고, 위협 모델링을 통한 체계적 방법론이 없음 |
| 방법 | 이해관계자 기반 DFD 수립 → MS Threat Modeling Tool로 1차 위협 식별 → Attack Library 구축 → STRIDE-per-element → Attack Tree → 보안 체크리스트 도출 |
| 데이터 | 사고사례(국내외 언론보도), 기술보고서, 논문, 컨퍼런스 발표, CVE. 대상 기기는 IEC 61162-450/460 기반 디바이스 목록에서 선정 |
| 결과 | STRIDE로 총 206개 위협 식별 (Repudiation 45/22%, Spoofing 41/20%, DoS 36/17%, Tampering 31/15%, Info Disclosure 28/14%, EoP 25/12%). System/Network/Application 3개 측면의 보안 요구사항 체크리스트 제시 |
| 한계 | 위협 수 집계에 그치고 실증 검증 없음. 위험도 정량화(우선순위) 부재. 규정(당시 E26 미제정)과의 연결 없음 |
| 관련성 | **비교 대상.** 국내 선박 위협모델링의 사실상 기준 논문. 방법론(DFD+STRIDE+Attack Tree)을 차용하되, 나는 "규정 제외 기준"이라는 축을 추가해 차별화해야 함 |

---

## 1. 연구 목적
[논문] 조선·해양과 ICT 융합이 진행되는 선박에 대해 위협 모델링을 수행하여 **선박 사이버보안 요구사항을 도출**하는 것.

## 2. 연구 문제
[논문] 선박에 IT/OT 시스템(ECDIS, AIS 등)이 다수 사용되면서 건조·항해 환경까지 고려한 보안 요소가 필요해졌으나, 선박·조선 ICT 기자재 산업의 사이버보안 연구가 부족하고 **위협 모델링을 통한 체계적 방법론이 부재**하다.

## 3. 연구 대상
[논문] 선박 전체를 2개 Boundary로 구분.
- **육상(Offshore)** — 7개 세부 boundary: 해운사 Shipping Management Web Services, 항만 Port MIS, 관세청 Customs Web Services, 항만 화물관리 Shipping Management, 해양경찰 VTS System, Marine Satellite Services, Shipping Management DB(B/L·용선계약서 포함)
- **선박(Ship)** — IT 영역: IBS(통합항해정보시스템), AIS, ECDIS, VDR / OT 영역: 평형수관리시스템, 화물관리시스템, 엔진시스템
- **External Entity** 6개: 발주사, 에이전트, 선주사, 조선기자재 회사, 선박 운영사 등

[논문] 선박 IT/OT 시스템은 **위성통신시스템과 게이트웨이를 통해서만** 접근 가능하다는 전제.

## 4. 연구 방법
[논문]
1. MS Threat Modeling Tool로 DFD Level 1 작성 → 개략 Attack List 식별
2. 도구가 개략 정보만 주므로 **Attack Library**를 별도 작성해 공격 방법 구체화 (사고사례 + CVE + 컨퍼런스 발표)
3. **STRIDE-per-element** 적용 — DFD 구성요소(External Entry / Data Store / Process / Data Flow)별 위협 매핑
4. **Attack Tree** 작성 후 위험분석
5. 위협 → 보안대책 체크리스트 도출 (System / Network / Application 3개 측면)

## 5. 핵심 결과
[논문]
- STRIDE 총 **206개** 위협 식별. 분포: Repudiation 45(22%) > Spoofing 41(20%) > DoS 36(17%) > Tampering 31(15%) > Information Disclosure 28(14%) > EoP 25(12%)
- DFD 요소별 위협 매핑: Data Store와 Data Flow는 STRIDE 6개 전부 해당, External Entry는 S·R·E, Process는 S·R·D·E
- 요구사항 도출 예시:
  - **System**: AIS·GNSS(GPS 스푸핑 대응 — 안테나 추가, 스푸핑 화이트리스트 확장, 다중 GPS 신호 사용, 지연 감소), VDR(Remote File Inclusion·File forgery → 파일 검증, IDS/IPS), VSAT(악성 장치 → 인가 장비 검증, 기본 ID/PW 변경, 브루트포스 → IDS/IPS, 패스워드 정책)
  - **Network**: SAN·CAN 프로토콜 위협 대응
  - **Application**: VSAT 및 원격 접속(선주·조선사 등) 대상 요구사항
- Attack Library 근거 사례: Balduzzi의 AIS 무인증·무결성 미보장 실증(2013), Santamarta의 위성통신 장비 취약점 시연(BLACKHAT 2014), IOActive의 VDR 원격 데이터 무단 변조 취약점(2014), 2012년 충돌사고 후 VDR 음성기록 삭제 사건

[논문] VDR에 대해: "폐쇄구조가 아니라 원격에서도 접근할 수 있고 Ethernet을 통해서도 접근 가능하고 **노트북을 통해 Direct로 접근이 가능**"

## 6. 기존 연구와 차이
[논문] 기존 해양 사이버보안 연구는 위협 분석이 산발적이었고, Tam & Jones의 MaCRA(자율운항 수준·공격자 보상·공격 용이성 3축, 5단계)처럼 리스크 평가 프레임은 있었으나 **선박 시스템 전체에 대한 체계적 위협 모델링과 요구사항 도출은 부재**했다는 것이 저자들의 차별점 주장.

## 7. 한계 (저자 인정 + 관찰)
[논문 — 저자 인정] 결론에서 "현재까지 발표된 해양 사이버보안에 대한 위협 도출과 대응방안은 미비한 상태"라고만 언급하고, 자기 연구의 한계는 명시적으로 서술하지 않음.

[추론 — 내 관찰]
- 206개 위협을 **개수로만** 제시하고 심각도·우선순위 정량화가 없음. 어느 위협부터 대응할지 판단 불가
- 실증(PoC)이 없고 문헌·CVE 기반 도출에 머무름
- 2019년 논문이라 **UR E26/E27(2022~2023 제정) 이전**. 규정 준수 관점이 전혀 없음
- DFD가 "위성통신시스템과 게이트웨이를 통해서만 접근 가능"을 전제 → **선내 시리얼 경로와 물리 접근 경로가 모델에서 빠짐**

## 8. 내가 가져갈 것
1. **방법론 뼈대**: 이해관계자 기반 DFD → Attack Library → STRIDE-per-element → Attack Tree. 내 연구도 동일 골격을 쓰되 DFD의 신뢰경계를 "E26 대상 CBS vs 제외된 CBS"로 잡으면 그대로 재사용 가능
2. **Attack Library 구축 방식**: 사고사례 + CVE + 컨퍼런스 발표를 IEC 61162-450/460 기반 디바이스 목록으로 범위 한정 — 내 연구에서 제외 대상 기기(Smart ship solution 등)에 그대로 적용
3. **선박 IT/OT 자산 분류표** (IBS/AIS/ECDIS/VDR vs 평형수/화물/엔진) — 내 아키텍처 다이어그램 정비에 참조
4. **VDR 사례**가 특히 유용: 폐쇄구조가 아니고 **노트북 Direct 접근 가능** → 내 매핑표 R3(C-b 물리 인터페이스 기준)의 직접 근거

## 9. 내 연구와의 관계
**비교 + 확장.**
- 비교: 이 논문은 "선박에 어떤 위협이 있는가"를 망라했다. 내 연구는 "**규정이 제외를 허용한 CBS**에 어떤 위협이 남는가"로 범위를 좁히고 축을 바꾼다. 같은 STRIDE를 써도 산출물의 성격이 다름
- 확장: 이 논문의 DFD는 육상↔선박을 위성통신 단일 경로로 모델링했다. 내 연구는 여기에 **시리얼 경로와 물리 접근 경로**를 추가해야 한다 (2026-08-12 메모의 내부/외부 두 경로)
- ⚠️ **차별화 필수**: STRIDE 단독으로 선박 위협모델링을 하면 이 논문의 재탕이 된다. ATT&CK for ICS 매핑과 "제외 기준" 축이 반드시 들어가야 함

## 연결
- [[2026-08-13_e26-exclusion-residual-threat_mapping]] — R3, R5의 근거로 인용
- [[2024_yu_vsat-threat-modeling_note]] — 이 논문을 참고문헌 [2]로 인용하고 있음(계보 관계)
