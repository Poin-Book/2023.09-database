# Views

> 작성자: 최선규

- [Views](#views)
  - [View란?](#view란)
    - [view의 필요성](#view의-필요성)
    - [뷰의 장·단점](#뷰의-장단점)
  - [View 기본 문법](#view-기본-문법)
    - [View creation](#view-creation)
    - [View 조회](#view-조회)
    - [View 삭제](#view-삭제)
  - [Update of a View](#update-of-a-view)

## View란?

하나 이상의 기본 테이블이나 다른 뷰를 기반으로 만들어진 가상 테이블

- 기본 테이블은 디스크에 공간이 할당되어 데이터를 저장함
- view는 데이터 딕셔너리(data dictionary) 테이블에 view에 대한 정의 (SQL 문)만 저장되어 디스크 공간을 차지하지 않음
- 전체 데이터 중에서 일부만 접근할 수 있도록 함
- view에 대한 수정 결과는 view를 정의하는 기본 테이블에 반영됨
- view를 정의한 기본 테이블에서 정의된 무결성 제약조건은 그대로 유지

### view의 필요성

- 사용자 마다 특정 객체(데이터)만 조회할 수 있도록 할 필요가 있음
- 복잡한 쿼리를 단순화 할 수 있음
- 데이터의 중복성을 최소화 할 수 있음

### 뷰의 장·단점

장점

- 논리적 독립성을 제공함
- 데이터의 접근 제어 (보안)
- 사용자의 테이터 관리 단순화
- 여러 사용자의 다양한 데이터 요구 지원

단점

- 뷰의 정의 변경 불가
- 삽입 , 삭제 , 갱신 연산에 제한이 있음

## View 기본 문법

### View creation

- view 생성 with base table

```sql
CREATE VIEW view_name AS
SELECT column_list
FROM table_name
WHERE condition;
```

- view 생성 with another view

```sql
CREATE VIEW view_name2 AS
SELECT column_list
FROM view_name1
WHERE condition;
```

### View 조회

```sql
SELECT * FROM view_name;
```

### View 삭제

```sql
DROP VIEW view_name;
```

## Update of a View

- row 추가

```sql
-- view_name의 column_list는 생략 가능
INSERT INTO view_name
VALUES (value1, value2, ...);

-- where 절을 사용하여 특정 row에만 추가 가능
INSERT INTO view_name (column_list)
VALUES (value1, value2, ...);
WHERE condition;
```

- row 수정

```sql
UPDATE view_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

- row 삭제

```sql
DELETE FROM view_name
WHERE condition;
```
