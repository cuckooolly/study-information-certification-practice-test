# DML (Data Manipulation Language)
- DB 내의 데이터를 조회, 삽입, 수정, 삭제하는 데 사용하는 언어

| 명령어    | 기능               |
|--------|------------------|
| SELECT | 테이블에서 튜플을 검색함    |
| INSERT | 테이블에 새로운 튜플을 삽입함 |
| DELETE | 테이블에서 튜플을 삭제함    |
| UPDATE | 테이블의 튜플의 내용을 갱신함 |


## 삽입문 (INSERT INTO~)
- 표기 형식
```sql
INSERT INTO 테이블명 [(속성명, ...)]
VALUES (값1, 값2, ...);
```
- 설명
  - 테이블에 새로운 튜플(행)을 삽입
  - 속성명 : 삽입할 컬럼 이름 (생략 가능, 생략 시 테이블의 모든 컬럼에 대해 값을 삽입해야 함)
  - VALUES : 삽입할 값 목록
- 예시
```sql
INSERT INTO Students (StudentID, Name, Age)
VALUES (1, 'Alice', 20);
``` 

## 삭제문 (DELETE FROM~)
- 표기 형식
```sql
DELETE FROM 테이블명 [WHERE 조건식];
```
- 설명
  - 테이블에서 특정 조건을 만족하는 튜플(행)을 삭제
  - WHERE : 삭제할 튜플을 지정하는 조건식 (생략 시 테이블의 모든 튜플이 삭제됨)
- 예시
```sql
DELETE FROM Students WHERE StudentID = 1;
```

## 갱신문 (UPDATE~SET~)
- 표기 형식
```sql
UPDATE 테이블명
SET 속성명1 = 값1, ...
[WHERE 조건식];
```
- 설명
  - 테이블의 특정 튜플(행)의 속성 값을 갱신
  - SET : 갱신할 속성과 새로운 값 목록
  - WHERE : 갱신할 튜플을 지정하는 조건식 (생략 시 테이블의 모든 튜플이 갱신됨)
- 예시
```sql
UPDATE Students
SET Age = 21
WHERE StudentID = 1;
```

## 문제
1. 학생 테이블에서 "이름"이 "민수"인 튜플을 삭제하고자 한다. 다음 처리 조건을 참고하여 SQL문을 작성하시오
- 최소한의 코드로 작성될 수 있도록 SQL문을 구성한다.
- 명령문 마지막의 세미콜론(;)은 생략이 가능하다
- 인용부호가 필요한 경우 작은 따옴표('')를 사용한다.

2. 사원 테이블에 있는 자료 중에서 "부서"가 "기획"인 자료를 검색하여 기획부(성명, 경력, 주소, 기본급) 테이블에 삽입하는 SQL문을 작성하시오.
- 사원(**성명**, 부서, 경력, 주소, 기본급)
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 정답
1. DELETE FROM 학생 WHERE 이름 = '민수';
2. INSERT INTO 기획부 (성명, 경력, 주소, 기본급)
   SELECT 성명, 경력, 주소, 기본급
   FROM 사원
   WHERE 부서 = '기획';