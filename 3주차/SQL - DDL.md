# DDL (Data Define Language)
- DB 구조, 데이터 형식, 접근 방식 등, DB를 구축하거나 수정할 목적으로 사용하는 언어

## CREATE

### CREATE SCHEMA

- 표기 형식
```sql
CREATE SCHEMA 스키마명 AUTHORIZATION 사용자_id;
```

- 설명
  - 스키마 생성
    - 스키마 : DB 내에서 객체(테이블, 뷰, 인덱스 등)를 논리적으로 그룹화한 것
  - AUTHORIZATION : 스키마 소유자 지정

- 예시
```sql
CREATE SCHEMA Sales AUTHORIZATION admin;
```

### CREATE DOMAIN
- 표기 형식
```sql
CREATE DOMAIN 도메인명 [AS] 데이터_타입
    [DEFAULT 기본값];
    [CONSTRAINT 제약조건명 CHECK (범위값)];
```

- 설명
  - 도메인 생성
  - 도메인 : 사용자 정의 데이터 타입
  - DEFAULT : 도메인의 기본값 지정
  - CONSTRAINT : 도메인에 제약조건 추가
  - CHECK : 도메인 값을 지정하는 것

- 예시
```sql
CREATE DOMAIN PositiveInt AS INT
    DEFAULT 0
    CONSTRAINT PositiveCheck CHECK (VALUE >= 0);
```

### CREATE TABLE
- 표기 형식
```sql
CREATE TABLE 테이블명 
    (속성명 데이터_타입 [DEFAULT 기본값] [NOT NULL], ...
    [PRIMARY KEY (속성명), ...]
    [UNIQUE (속성명), ...]
    [FOREIGN KEY (속성명) 
        REFERENCES 참조테이블(기본키_속성명), ...]
        [ON DELETE {CASCADE | SET NULL | SET DEFAULT | NO ACTION}]
        [ON UPDATE {CASCADE | SET NULL | SET DEFAULT | NO ACTION}]
    [CONSTRAINT 제약조건명 CHECK (범위값), ...]);
```
- 설명
  - 테이블 생성
  - 속성명 : 테이블의 컬럼 이름
  - 데이터_타입 : 컬럼의 데이터 타입 (INT, VARCHAR, DATE 등)
  - DEFAULT : 컬럼의 기본값 지정
  - NOT NULL : 컬럼에 NULL 값 허용하지 않음
  - PRIMARY KEY : 테이블의 기본키 지정 (중복 및 NULL 값 허용하지 않음)
  - UNIQUE : 컬럼의 값이 고유하도록 지정 (중복 허용하지 않음)
  - FOREIGN KEY : 다른 테이블의 기본키를 참조하는 외래키 지정
  - REFERENCES : 참조하는 테이블과 기본키 속성명 지정
  - ON DELETE / ON UPDATE : 참조된 행이 삭제되거나 업데이트될 때의 동작 지정 (CASCADE, SET NULL, SET DEFAULT, NO ACTION)
  - CONSTRAINT : 테이블에 제약조건 추가
  - CHECK : 컬럼 값이 특정 범위 내에 있는지 확인

- 예시
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    BirthDate DATE,
    HireDate DATE DEFAULT CURRENT_DATE,
    Salary DECIMAL,
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
        ON DELETE SET NULL
        ON UPDATE CASCADE
    CONSTRAINT SalaryCheck CHECK (Salary >= 0)
);
```

### CREATE VIEW
- 표기 형식
```sql
CREATE VIEW 뷰명[(속성명, ...)]
    AS SELECT 문;
```

- 설명
  - 뷰 생성
    - 뷰 : 하나 이상의 테이블에서 유도된 가상 테이블
  - 속성명 : 뷰의 컬럼 이름 (생략 가능)
  - AS SELECT 문 : 뷰를 정의하는 SELECT 문

- 예시
```sql
CREATE VIEW EmployeeView AS
    SELECT EmployeeID, FirstName, LastName, DepartmentID
    FROM Employees
    WHERE Salary > 50000;
```

### CREATE INDEX
- 표기 형식
```sql
CREATE [UNIQUE] INDEX 인덱스명
    ON 테이블명 (속성명 [ASC | DESC], ...)
    [CLUSTER];
```

- 설명
  - 인덱스 생성
    - 인덱스 : 테이블의 특정 컬럼에 대한 검색 속도를 향상시키는 데이터 구조
  - UNIQUE : 인덱스가 고유한 값을 가지도록 지정 (중복 허용하지 않음)
  - 속성명 : 인덱스를 생성할 컬럼 이름
  - ASC / DESC : 인덱스의 정렬 순서 지정 (오름차순 / 내림차순)
  - CLUSTER : 클러스터형 인덱스 생성 (테이블의 물리적 순서를 인덱스 순서에 맞춤)

- 예시
```sql
CREATE UNIQUE INDEX idx_employee_lastname
    ON Employees (LastName ASC);
```

## ALTER
### ALTER TABLE
- 표기 형식
```sql
ALTER TABLE 테이블명 ADD 속성명 데이터_타입 [DEFAULT 기본값];
ALTER TABLE 테이블명 ALTER COLUMN 속성명 [SET DEFAULT 기본값];
ALTER TABLE 테이블명 DROP COLUMN 속성명 [CASCADE];
```

- 설명
  - 테이블 수정
  - ADD : 테이블에 새로운 컬럼 추가
  - ALTER COLUMN : 기존 컬럼의 속성 변경 (예: 기본값 설정)
  - DROP COLUMN : 테이블에서 컬럼 삭제

- 예시
```sql
ALTER TABLE Employees ADD Email VARCHAR(100);
ALTER TABLE Employees ALTER COLUMN Salary SET DEFAULT 30000;
ALTER TABLE Employees DROP COLUMN BirthDate CASCADE;
```

## DROP
### DROP TABLE
- 표기 형식
```sql
DROP SCHEMA 스키마명 [CASCADE | RESTRICT];
DROP DOMAIN 도메인명 [CASCADE | RESTRICT];
DROP TABLE 테이블명 [CASCADE | RESTRICT];
DROP VIEW 뷰명 [CASCADE | RESTRICT];
DROP INDEX 인덱스명 [CASCADE | RESTRICT];
DROP CONSTRAINT 제약조건명;
```

- 설명
  - 스키마, 도메인, 테이블, 뷰, 인덱스, 제약조건 삭제
  - CASCADE : 관련된 모든 객체도 함께 삭제
  - RESTRICT : 관련된 객체가 있으면 삭제하지 않음

- 예시
```sql
DROP SCHEMA Sales CASCADE;
DROP DOMAIN PositiveInt RESTRICT;
DROP TABLE Employees CASCADE;
DROP VIEW EmployeeView RESTRICT;
DROP INDEX idx_employee_lastname CASCADE;
DROP CONSTRAINT SalaryCheck;
```

## 문제
1. 다음 처리조건에 부합하는 SQL문이 완성되도록 괄호에 적합한 옵션을 작성하시오.
- 처리 조건
  - <학생> 테이블을 제거한다.
  - <학생> 테이블을 참조하는 모든 데이터도 함께 제거한다.
- SQL문
  - DROP TABLE 학생 (          ) ;

2. 직원 테이블에 대해 '이름' 속성으로 '직원_name'이라는 인덱스를 정의하는 SQL문을 작성하시오.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 정답
1. CASCADE
2. CREATE INDEX 직원_name ON 직원 (이름);