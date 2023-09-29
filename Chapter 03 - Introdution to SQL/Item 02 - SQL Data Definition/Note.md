# SQL Data Definition

> 작성자: 김나현

## 목차

- Data Definition Language (DDL)
- Data Menipulation Language (DML)
- Data Control Language (DCL)
- Transcation Control Language (TCL)

<br/><br/>

## SQL Data Definition

![](<https://velog.velcdn.com/images/alicesykim95/post/e12c29bf-f5ba-4c5d-9905-50e1ba60c443/%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%20(1).png>)

## [Data Definition Language (DDL)](https://wonit.tistory.com/218)

: 데이터 정의 언어

- 관계에 대한 정보를 지정할 수 있음
  - 각 관계에 대한 스키마
  - 각 속성과 연관된 값의 도메인
  - 무결성 제약 조건
  - 각 관계 별로 유지해야 할 인덱스 집합
  - 각 관계에 대한 보안 및 권한 정보
  - 디스크의 각 관계에 대한 물리적 스토리지 구조
- 테이블과 컬럼을 정의하는 명령어로 생성, 수정, 삭제 등의 데이터 전체 골격을 결정하는 역할을 담당

<br/>

> **DDL의 특징**

- DDL은 명령어를 입력하는 순간 작업이 즉시 반영(Auto Commit)됨. 따라서 사용할 때 주의 필요

</br>

> **DDL의 종류**

| 명령어                                                                                                                                                                                                                        | 내용                         | 예시                                               |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | -------------------------------------------------- |
| [CREATE](https://jhnyang.tistory.com/entry/ORACLE-MYSQL-SQL-CREATE-TABLE-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%83%9D%EC%84%B1%ED%95%98%EA%B3%A0-%EC%A3%BC%ED%82%A4%EA%B8%B0%EB%B3%B8%ED%82%A4-%EC%A7%80%EC%A0%95%ED%95%98%EA%B8%B0) | 테이블 생성                  | CREATE TABLE [테이블명] (내용);                    |
| [ALTER](https://extbrain.tistory.com/39)                                                                                                                                                                                      | 테이블 구조 수정             | ALTER TABLE [테이블명];                            |
| [DROP](https://blog.naver.com/regenesis90/222199419086)                                                                                                                                                                       | 테이블이나 DB 삭제           | DROP TALBE [테이블명];                             |
| [RENAME](https://extbrain.tistory.com/61)                                                                                                                                                                                     | 테이블 이름, 칼럼 등 변경    | RENAME TABLE [원래 테이블명] TO [새로운 테이블명]; |
| [COMMENT](https://jhnyang.tistory.com/309)                                                                                                                                                                                    | 테이블 또는 칼럼에 주석 달기 | COMMENT ON TABLE [테이블명] IS ‘[주석]’;           |
| [TRUNCATE](https://m.blog.naver.com/regenesis90/222199390453)                                                                                                                                                                 | 테이블 초기화                | TRUNCATE TABLE [테이블명];                         |

<br/>
<aside>
💡 DROP와 TRUNCATE의 차이

---

- `DROP`: 데이터베이스에서 개체를 삭제하는 데 사용. 테이블 자체를 삭제
- `TRUNCATE`: 레코드에 할당된 모든 공간을 포함하여 테이블에서 모든 행을 제거하는 데 사용
</aside>

- `CREATE` 예시

  ```sql
  create table department(
  	dept_name varchar(20),
  	building varchar(15),
  	budget numeric(12,2),
  	primary key (dept_name)
  );
  ```

    <aside>
    💡 Primary Key를 지정하는 2가지 방법
    
    ---
    
    1️⃣ **Column 뒤에 지정**
    
    ```sql
    create table department(
    	dept_name varchar(20) primary key,
    	building varchar(15),
    	budget numeric(12,2),
    );
    ```
    
    2️⃣ **마지막에 지정**
    
    ```sql
    create table department(
    	dept_name varchar(20),
    	building varchar(15),
    	budget numeric(12,2),
    	primary key (dept_name)
    );
    ```
    
    → 2번의 경우, 여러 primary key를 지정할 수 있음
    
    ex) `primary key (dept_name, building)`
    
    </aside>

- `ALTER` 예시

  1. 이름이나 정의 변경

     ```sql
     alter table t1 change a b bigint not null;
     alter table t1 rename column b to a;
     alter table t1 modify column a varchar(16) NULL;
     ```

     \*\* t1: 테이블명

  2. 칼럼 추가, 삭제

     ```sql
     alter table t1 add column a int;
     alter table t1 drop column a;
     ```

  3. 제약 조건 변경

     ```sql
     alter table t1 drop foreign key fk_symbol;
     ```

  4. 여러 칼럼 변경

     ```sql
     alter table t2 frop column c, drop column d;
     ```

---

## [Data Manipulation Language (DML)](https://mozi.tistory.com/208)

: 데이터 조작 언어

- 데이터베이스의 내부 데이터를 관리하기 위한 언어
- 데이터를 조회, 추가, 변경, 삭제 등의 작업을 수행하기 위해 사용

<br/>

> **DML의 특징**

- DDL과 달리 DML은 적는 즉시 반영(Auto Commit)이 되기 않음
  → DML에 의한 데이터 변동은 영구적인 변경이 아니기 때문에 `ROLLBACK`으로 다시 되돌릴 수 있음
- DML은 타깃 테이블을 **메모리 버퍼** 위에 올려두고 변경을 수행하기 때문에, 실시간으로 테이블에 반영되지 않음
  → `COMMIT`명령어를 통해 Transaction을 종료해야 해당 변경 사항이 테이블에 반영

</br>

> **DML의 종류**

| 명령어                                                                                                | 내용                             | 예시                                                        |
| ----------------------------------------------------------------------------------------------------- | -------------------------------- | ----------------------------------------------------------- |
| [SELECT](https://velog.io/@re-deok/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-DML-SELECT) | DB 내에서 데이터 검색            | SELECT \* FROM [테이블명]; SELECT [필드명] FROM;[테이블명]; |
| [INSERT](https://gent.tistory.com/498)                                                                | 테이블에 데이터 추가             | INSERT INTO [테이블명] VALUES (’1234’, ‘33’, ‘finance’, 4); |
| [UPDATE](https://gent.tistory.com/499)                                                                | 테이블 내에 존재하는 데이터 변경 | UPDATE [테이블명] SET salary = salary \* 1.03;              |
| [DELETE](https://gent.tistory.com/500)                                                                | 테이블의 데이터를 제거           | DELETE FROM [테이블명];                                     |

---

<br/><br/>

## [Data Control Language (DCL)](https://velog.io/@seyeop03/Chapter-11.-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%A3%BC%EC%9A%94-%EA%B8%B0%EB%8A%A5-4-Grant-Revoke)

: 데이터 제어 언어

- 데이터를 관리 목적으로 보안, 무결성, 회복, 병행 제어 등을 정의하는데 사용
- DCL을 사용하면 데이터베이스에 접근하여 읽거나 쓰는 것을 제한할 수 있는 권한을 부여하거나 박탈할 수 있고, 트랜잭션을 명시하거나 조작할 수 있음

</br>

> **DCL의 특징**

- 불법적인 사용자로부터 데이터를 보호하기 위한 데이터 보안의 역할을 수행
- 데이터의 정확성을 위한 무결성을 유지
- 시스템 장애에 대비한 회복과 병행수행을 제어

</br>

> **DCL의 종류**

| 명령어 | 내용                  | 예시                                          |
| ------ | --------------------- | --------------------------------------------- | ---- | ----------------------------- |
| GRANT  | 권한을 부여할 때 사용 | GRANT [권한명] (컬럼) ON [객체명] TO { 유저명 | 롤명 | PUBLC} [WITH GRANT OPTION]    |
| REVOKE | 권한을 회수할 때 사용 | REVOKE [권한명] ON [객체명] FROM {유저명      | 롤명 | PUBLIC} [CASCADE CONSTRAINTS] |

---

<br/><br/>

## **[Transaction Control Language (TCL)](https://mozi.tistory.com/209)**

: 트랜잭션 제어 언어

- DCL과 비슷한 맥락이지만 데이터를 제어하는 언어가 아닌 트랜잭션을 제어할때 사용
- 논리적인 작업 단위를 묶어 DML에 의해 조작된 결과를 트랜잭션 별로 제어

</br>

> **트랜잭션이란?**

- 데이터베이스의 상태를 변화시키기 위해 수행하는 작업의 단위
- 보통 DBMS 선능을 초당 트랜잭션이 몇개가 실행되었는지로 측정
- **MySQL의 입력하는 모든 명령어들은 각각 하나의 트랜잭션이라고 할 수 있음**

</br>

> **트랜잭션의 특성**

| 특성                | 설명                                                                                                                                   |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 원자성(Atomicity)   | 트랜잭션에서 정의된 연산들은 모두 성공적으로 실행되거나 아니면 전혀 실행되지 않은 상태로 남아있어야 함 (All Or Nothing)                |
| 일관성(Consistency) | 트랜잭션이 실행되기 전의 데이터베이스 내용이 잘못 되어 있지 않다면 트랜잭션이 실행된 이후에도 데이터베이스의 내용에 잘못이 있으면 안됨 |
| 독립성(Isolation)   | 트랜잭션이 실행되는 도중에 다른 트랜잭션의 영향을 받아 잘못된 결과를 만들어서는 안됨                                                   |
| 지속성(Dutability)  | 트랜잭션이 성공적으로 수행되면 그 트랜잭션이 갱신한 데이커베이스의 내용은 영구적으로 저장됨                                            |

</br>

> **TCL 종류**

| 명령어    | 내용                                                   | 예시                  |
| --------- | ------------------------------------------------------ | --------------------- |
| COMMIT    | 변경된 데이터를 테이블에 영구적으로 반영               | COMMIT;               |
| ROLLBACK  | 모든 작업을 다시 돌려 놓겠다                           | ROLLBACK;             |
| SAVEPOINT | Commit 전에 특정 시점까지만 반영하거나 Rollback 하겠다 | SAVEPOINT [포인트명]; |

[참고 자료]

- [https://velog.io/@alicesykim95/DB-DDL-DML-DCL-TCL이란](https://velog.io/@alicesykim95/DB-DDL-DML-DCL-TCL%EC%9D%B4%EB%9E%80)
- [https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/](https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/)

---
