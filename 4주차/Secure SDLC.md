# Secure SDLC (Secure Software Development Life Cycle)
## 개요
- 보안상 안전한 소프트웨어를 개발하기 위해, 개발 과정에 보안 활동을 통합하는 방법론

## SSDLC 단계
1. 요구사항 분석: 보안 항목에 해당하는 요구사항을 식별하는 작업을 수행
2. 설계: 식별된 보안 요구사항을 설계서에 반영
3. 구현: 설계서에 따라 소프트웨어를 구현
4. 테스트: 설계서를 바탕으로 요구사항들이 반영되었는지 점검
5. 유지보수: 발생할 수 있는 보안 사고를 식별하고, 대응(침해사고 대응, 보안 패치 등)을 실시

## 보안의 5대 요소
- 기밀성(Confidentiality): 인가된 사용자만 정보에 접근할 수 있도록 보장
- 무결성(Integrity): 인가되지 않은 사용자가 정보를 변경하지 못하도록 보장
- 가용성(Availability): 인가된 사용자가 필요할 때 정보에 접근할 수 있도록 보장
- 인증(Authentication): 사용자가 자신이 주장하는 신원을 증명
- 부인방지(Non-repudiation): 송수신자가 메시지를 송수신 했음을 부인하지 못하도록 보장

## Secure Coding
- 보안 취약점을 최소화하기 위해 안전한 코딩 기법을 적용하는 것
- 입력 검증, 출력 인코딩, 에러 처리, 세션 관리, 암호화, 권한 관리 등의 기법 포함
- 각 언어별 Secure Coding 가이드북
  - Javascript: https://www.kisa.or.kr/skin/doc.html?fn=20240403_091307_718.pdf&rs=/result/2024-04/
  - Python: https://www.kisa.or.kr/skin/doc.html?fn=20240123_171651_543.pdf&rs=/result/2024-01/
  - 소프트웨어 개발보안 가이드: https://www.kisa.or.kr/skin/doc.html?fn=20220104_2030303_5.pdf&rs=/result/2022-01/

## 심화학습: Shift-Left

### 개요
- 개발의 모든 주기에 보안 테스팅을 수행하는 개발 방법론
- Test everything/everytime/early/continuously in every phase of SDLC by automation toolkit.

### 예시
- Requirements Analysis & Testing
- Design & Testing
- Coding & Testing
- Production Deployment & Testing

### 이점
- 비용 절감: 결함을 조기에 발견하고 해결함으로써, 전체적인 개발 비용을 절감
  - ![](https://blog.kakaocdn.net/dna/bh1GpW/btsv5m6WSd4/AAAAAAAAAAAAAAAAAAAAAP1w2OdcUNnm8M9HIV5D8EkwWJhnv1_ahXcMxwtVTKVO/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1761922799&allow_ip=&allow_referer=&signature=YJKrTrDNBAAt8sOkmptorK%2BWa%2FY%3D)
- 품질 향상: 결함을 조기에 포착하여, 최종 제품의 품질을 향상
- 개발 속도 향상: 별도의 테스트 단계를 기다릴 필요가 없어, 개발 속도가 빨라짐
- 보안 문제 조기 해결: 보안 취약점을 조기에 발견하고 해결하여, 보안 사고를 예방

## 문제

1. 기밀성에 대해 설명하세요.
2. 부인방지에 대해 설명하세요.
3. SSDLC의 "요구사항" 분석 단계에 대해 설명하세요.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 정답

1. 기밀성이란, 인가된 사용자만 정보에 접근할 수 있도록 보장하는 것을 의미합니다.
2. 부인방지란, 송수신자가 메시지를 송수신 했음을 부인하지 못하도록 보장하는 것을 의미합니다.
3. 보안 항목에 해당하는 요구사항을 식별하는 작업을 수행하는 것을 의미합니다.

## 참고자료/출처
- https://kairoka-sqa.tistory.com/28
- 김승주 교수님의 보안 공학 수업
  - ©2025 by Seungjoo Gabriel Kim. Permission to 
make digital or hard copies of part or all of this 
material is currently granted without fee 
provided that copies are made only for personal 
or classroom use, are not distributed for profit 
or commercial advantage, and that new copies 
bear this notice and the full citation.
