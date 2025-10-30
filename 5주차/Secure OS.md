# Secure OS

## Secure OS
- 보안 기능을 갖춘 커널을 이식하여, 시스템 자원을 보호하는 운영체제
- 보안 커널은 보안 기능을 갖춘 커널을 의미하며, TCB를 기반으로 참조 모니터의 개념을 구현하고 집행한다.
- 보호 방법을 분류
  - 암호적 분리: 내부 정보를 암호화하는 방법
  - 논리적 분리: 프로세스의 논리적 구역을 지정하여 구역을 벗어나는 행위를 제한하는 방법
  - 물리적 분리: 사용자별로 특정 장비만 사용하도록 제한하는 방법
- Secure OS의 보안 기능
  - 식별 및 인증
  - 임의적/강제적 접근통제
  - 객체 재사용 보호
  - 완전한 조정
  - 신뢰 경로
    - 감사 및 감사기록 축소 등
![](https://mblogthumb-phinf.pstatic.net/MjAyMzEwMTRfMjUx/MDAxNjk3MjQ5NzIyNDU4.Vpy94Qat_yRIaBFY26orXrxJ7tJHz0dKq1exR-8mHjwg.3_TWmmAv98CHPlA4aYuXEKNs5cioZyrs72a5nvluJ48g.PNG.leety72/image.png?type=w800)

## 참조 모니터
- 보호 대상 객체에 대한 접근 통제를 수행하는 추상 머신
- 보안 커널 데이터베이스를 참조하여 객체에 대한 접근 허가 여부를 결정
- 참조 모니터와 보안 커널의 특징
  - 격리성: 부정 조작이 불가능해야 함
  - 검증 가능성: 적절히 구현되었다는 것을 확인할 수 있어야 함
  - 완전성: 우회가 불가능해야 함
![](https://postfiles.pstatic.net/MjAyMzEwMTRfMjQ4/MDAxNjk3Mjc4NTE2MzE1.6ms48fw2M5pfZgcG7a8pVyPWRUBzkXovVXvQgBrG5W8g.d8yzTGNZrDfD2bteVJYLYB00TiP1WABwiSw_Jb-sEoYg.PNG.leety72/image.png?type=w773)

## 참고자료
- https://blog.naver.com/leety72/223236326769
- https://charstring.tistory.com/465