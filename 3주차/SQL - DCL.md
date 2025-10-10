# DCL (Data Control Language)
- 데이터의 보안, 무결성, 회복, 병행 제어 등을 정의하는 데 사용하는 언어


| 명령어       | 기능                            |
|-----------|-------------------------------|
| COMMIT    | 트랜잭션의 변경 사항을 영구적으로 저장         |
| ROLLBACK  | 트랜잭션의 변경 사항을 취소하고 이전 상태로 되돌림  |
| SAVEPOINT | 트랜잭션 내에서 특정 지점을 설정하여 부분 롤백 가능 |
| GRANT     | 사용자에게 특정 권한 부여                |
| REVOKE    | 사용자로부터 특정 권한 회수               |

## GRANT / REVOKE

### 사용자 등급 지정 및 해제

- 표기 형식
```sql
GRANT 사용자등급 TO 사용자_ID_리스트 [IDENTIFIED BY '암호'];
REVOKE 사용자등급 FROM 사용자_ID_리스트;
```

- 설명
  - GRANT : 사용자에게 특정 권한 부여
    - 사용자등급 : 권한 수준 (예: DBA, RESOURCE, CONNECT 등)
    - 사용자_ID_리스트 : 권한을 부여할 사용자 ID 목록
    - IDENTIFIED BY '암호' : 새 사용자 생성 시 암호 지정
  - REVOKE : 사용자로부터 특정 권한 회수
    - 사용자등급 : 회수할 권한 수준
    - 사용자_ID_리스트 : 권한을 회수할 사용자 ID 목록

- 예시
```sql
GRANT CONNECT TO user1 IDENTIFIED BY 'password123';
REVOKE CONNECT FROM user1;
```

### 테이블 및 속성애 대한 권한 부여 및 취소
- 표기 형식
```sql
GRANT 권한_리스트 ON 개체 TO 사용자 [WITH GRANT OPTION];
REVOKE [GRANT OPTION FOR] 권한_리스트 ON 개체 FROM 사용자 [CASCADE];
```

## COMMIT
- 트랜젝션 처리가 완료된 후, 그 내용을 데이터베이스에 반영하는 명령
- DML 명령어(INSERT, UPDATE, DELETE 등)가 성공하면 자동으로 COMMIT 됨
- DML 명령어가 실패하면 자동으로 ROLLBACK 되도록 Auto Commit 모드로 설정할 수 있음

## ROLLBACK
- 변경되었으나 아직 COMMIT 되지 않은 데이터를 이전 상태로 되돌리는 명령
- 일부 내용만 변경된 경우, 비일관성 문제로 ROLLBACK을 수행해야 함

## SAVEPOINT
- 트랜젝션 내에 ROLLBACK할 위치인 저장점을 지정하는 명령어
- 저장점을 지정할 때는 이름을 부여한다
- ROLLBACK 할 때, 지정된 저장점까지의 트랜젝션 처리 내용이 모두 취소됨

## 문제
- DCL을 이용하여 다음 요구 사항에 맞는 SQL 명령어를 작성하세요.
  - 학생(**학번**, 주민등록번호, 이름, 학년, 전화번호, 주소)
  - 강좌(**강좌번호**, 강좌명, 학점, 수강인원, 강의실, 학기, 연도, 교수번호)
  - 수강(**학번**, **강좌번호**, 성적)
  - 교수(**교수번호**, 주민등록번호, 이름, 직위, 임용년도)

1. 김하늘에게 학생 테이블에 대한 접근 및 조작에 관한 모든 권한을 부여하는 SQL문을 작성하세요.
2. 김하늘에게 강좌 테이블에 대해 삭제하는 권한을 부여하고, 강좌 테이블에 대해 삭제하는 권한을 다른 사람에게 부여할 수 있는 권한을 부여할 수 있는 권한을 부여하는 SQL문을 작성하세요.
3. 임꺽정에게 부여된 교수 테이블에 대한 SELECT, INSERT, UPDATE 권한을 취소하는 SQL문을 작성하세요.
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 정답
1. GRANT ALL ON 학생 TO 김하늘;
2. GRANT DELETE ON 강좌 TO 김하늘 WITH GRANT OPTION;
3. REVOKE SELECT, INSERT, UPDATE ON 교수 FROM 임꺽정;