# Basic Structure of SQL Queries

> 작성자: 김나현

## 목차

- 기본적인 쿼리 구조
- SELECT
- WHERE
- FROM

</br></br>

## **기본적인 쿼리 구조**

- 일반적인 SQL 쿼리는 다음과 같은 형태를 가짐
  $$
  select\ A_1, A_2, ..., A_n \\ from\ r_1, r_2, ..., r_m \\ where\ P_i
  $$
  - A(i)는 attribute(칼럼)를 나타냄
  - R(i)는 relation(테이블)를 나타냄
  - P는 술어를 나타냄

\*\* SQL 쿼리의 결과는 `relation`임

</br></br>

## [SELECT](https://gmlwjd9405.github.io/2019/04/25/db-sql-select.html)

- 쿼리 결과에서 원하는 속성을 나열
- 관계형 projection 연산에 해당
- SQL 이름은 대소문자를 구별하지 않는다
  ```sql
  select name from instructor;
  SELECT name FROM instructor;
  ```
  위의 결과는 동일

</br>

> **SELECT 명령문**

- `distinct`
  : 중복된 데이터를 제거하고 찾은 결과를 보여줌
  ```sql
  select distinct dept_name from instructor;
  ```
- `all`
  : 중복을 제거하지 말 것을 지정
  ```sql
  select all dept_name from instructor;
  ```
- `*`
  : 모든 속성을 찾을 것을 나타냄
  ```sql
  select * from instructor;
  ```
- `상수`
  : 속성은 from 절이 있는 상수일 수 있음
  ```sql
  select 'A' from instructor;
  ```
  → 결과적으로 하나의 열과 N개의 행(instructor 테이블의 튜플 수)이 있는 테이블을 생성하고, 각 행은 "A" 값을 가짐
  → 테이블의 열의 개수를 셀 때 많이 사용
- 칼럼 이름 변경
  ```sql
  select '437' as FOO;
  ```
  → 결과적으로 하나의 열과 "437" 값을 가진 하나의 행이 있는 테이블이 됨
  → 칼럼명을 FOO로 출력
- 속성 여러 개 검색
  : constats 또는 tuple 특성에 대한 연산 +, -, \* 및 /를 포함하는 산술 식을 포함할 수 있음
  ```sql
  select ID, name, salary/12 from instructor;
  ```
  → 속성 salary의 값을 12로 나눈 것을 제외하고 instructor 테이블과 동일한 관계를 반환

</br></br>

## WHERE

- 관계 대수의 선택 술어에 해당
- 비교 결과는 논리적 연결체(`and`, `or`, `not`)를 사용하여 조합될 수 있음
  ```sql
  select name
  from instructor
  where dept_name = 'Comp.Sci.' and salary > 80000;
  ```
- SQL은 `between` 비교 연산자를 포함할 수 있음
  ```sql
  select name from instructor where salary between 90000 and 100000;
  ```
  → `between 90000 and 100000`은 `≥ 90000 and ≤ 100000`과 동일한 결과

</br></br>

### FROM

- 쿼리에 관련된 관계를 나열
- 관계 대수의 `Cartesian product` 연산에 해당
  E.g., instructor x teaches의 Cartesian product
  ```sql
  select * from instructor, teaches;
  ```
  - 두 relation에서 모든 속성을 사용하여 가능한 모든 쌍을 생성
  - 일반적인 속성(e.g., ID)의 경우, 결과 테이블의 속성 이름이 관계 이름을 사용하여 변경됨 (e.g., instructor.ID)
- Cartesian product 은 직접적으로는 그다지 유용하지 않지만, where-clause 조건과 결합하면 유용
