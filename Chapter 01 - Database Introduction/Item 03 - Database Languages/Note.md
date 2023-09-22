# Database Languages

> 작성자: 이재혁

> Database system은 데이터베이스 스키마를 지정하는 데이터 정의 언어(DDL)와 데이터베이스 쿼리 및 업데이트를 표현하는 데이터 조작 언어(DML)을 제공한다. <br>
> DDL과 DML은 두 개의 별개 언어가 아니라 단순히 SQL 언어와 같은 하나의 데이터베이스 언어의 일부를 구성함. <br>
> 거의 모든 관계형 DB 시스템은 SQL 언어를 사용.

## 목차
- Data-Definition Language(DDL)
- Data-Manipulation Language(DML)
- Structured Query Language(SQL)

## Data-Definition Language(DDL)
**DDL을 통해 데이터베이스 스키마를 지정함.** DDL은 추가적인 property를 지정하는 데에도 사용됨<br>
DDL문 집합에 의해 데이터베이스 시스템이 사용하는 저장 구조와 접근 방법을 지정함. 이 statements는 데이터베이스 스키마의 구현 세부사항을 정의하는데, 보통 사용자로부터 숨겨져 있음.<br>
DDL compiler는 <span style="color: red">*data dictionary*</span>에 저장되어 있는 table template의 set를 생성.
```SQL
create table department
    (dept_name  char(20),
    building    char(15),
    budget      numeric(12,2));
```

<br>
Data dictionary는 metadata(data에 대한 data)를 포함함. <br>
- Database schema
- Integrity constraints: primary key
- Authorization: who can access what data

## Data-Manipulation Language(DML)
DML은 사용자가 적절한 데이터 모델에 의해 구성된 데이터에 접근하거나 조작할 수 있도록 하는 언어이다.<br>
접근 유형:
- DB에 저장된 정보 검색
- DB에 새 정보 삽입
- DB에서 정보 삭제
- DB에 저장된 정보 수정

DML에는 기본적으로 두 가지 타입이 있다:
- 절차적(Procedural) DML : 사용자에게 어떤 데이터가 필요하고 어떻게 그 데이터를 얻을 것인지를 지정해야 함.
- 선언형(Declarative) DML(또는 비절차형 DML) : 사용자가 해당 데이터를 얻는 방법을 지정하지 않고 필요한 데이터를 지정할 것을 요구.

```SQL
select instructor.ID, department.dept_name
from instructor, department
where instructor.dept_name = department.dept_name and department.budget > 95000;
```

## Structured Query Language(SQL)
- DBMS에서 데이터를 정의하고 관리하기 위해 고안된 특수 목적 프로그래밍 언어
- 가장 널리 쓰이는 상용 언어
- 응용 프로그램은 일반적으로 다음을 통해 데이터베이스에 접근함:
  - 언어 확장을 통해 내장된 SQL 또는
  - SQL 쿼리를 데이터베이스로 보낼 수 있는 응용 프로그램 인터페이스(예: ODBC/JDBC)