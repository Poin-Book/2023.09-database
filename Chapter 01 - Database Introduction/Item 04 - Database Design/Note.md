# Database Design

> 작성자: 최선규

## 목차

- [Database Design](#database-design)
  - [목차](#목차)
  - [Design Approach](#design-approach)
  - [Logical Design](#logical-design)
    - [1. Entity-Relationship Model](#1-entity-relationship-model)
    - [2. Object-Relational Data Model](#2-object-relational-data-model)
    - [A. Relational vs Object-Oriented vs Object-Relational](#a-relational-vs-object-oriented-vs-object-relational)
  - [Physical Design](#physical-design)
    - [1. Normalization (정규화)](#1-normalization-정규화)


## Design Approach

> 목표: Database를 효율적으로 사용하는 것

[두 가지 접근 방법]

- Entity-Relationship Model
  - Entity Model 사이의 관계를 통해 데이터를 표현
- Normalization
  - Database 테이블을 효율적으로 설계하기 위해 테스트하고 수정

[데이터베이스 설계 단계]
1. 요구사항 분석
2. Conceptual Design (개념적 설계)
3. Logical Design (논리적 설계)
4. Physical Design (물리적 설계)
5. 구현

## Logical Design

> database schema를 설계하는 과정

### 1. Entity-Relationship Model

> Entity Model 사이의 관계를 통해 데이터를 표현

[Entity]

- database에 저장되는 정보(attribute)의 집합(set)
  - ex. 사람, 장소, 사물, 이벤트 등 (like Object)

[Relationship]

- Entity 사이의 관계
  - ex. 사람과 사람 사이의 관계, 사람과 장소 사이의 관계 등

<center>

```mermaid
flowchart LR
  A[Instructor] --- B;
  B{Member} --- C;
  C[Department];
```

</center>

### 2. Object-Relational Data Model

> 기존의 관계형 데이터베이스 시스템에 객체 지향 데이터베이스의 장점을 통합한 데이터 모델

- 사용자 정의 타입을 지원한다.
- 참조 타입을 지원한다.
- 중첩 테이블을 지원한다.
- 대단위 객체의 저장, 추출이 가능하다.
- 객체 간의 상속 관계를 지원하는 것이 가능하다.

### A. Relational vs Object-Oriented vs Object-Relational

> 출처 : [DBMS의 종류(관계형, 객체지향형, 객체관계형)](https://chessire.tistory.com/entry/DBMS%EC%9D%98-%EC%A2%85%EB%A5%98%EA%B4%80%EA%B3%84%ED%98%95-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%ED%98%95-%EA%B0%9D%EC%B2%B4%EA%B4%80%EA%B3%84%ED%98%95)

| | Relational | Object-Oriented | Object-Relational |
|:---:|:---:|:---:|:---:|
| 데이터 모델 | 단순 정보타입만 지원 | 사용자 정의 타입,<br>비정형 정보타입 지원 | 사용자 정의 타입,<br>비정형 정보타입 지원 |
| 대규모 정보 처리 | 우수 | 보통 | 우수 |
| 안정성 | 우수 | 보통 | 우수 |
| 장점 | 사용하기 쉽고, 편리하며 안정적 | 복잡한 구조의 정보 모델링 가능 | 관계형 데이터베이스의 안정성 + 객체지향 모델링의 장점 |
| 단점 | 확장성의 부족 및<br>정보 표현의 어려움 | 안정성과 성능이 떨어짐 | |

## Physical Design

> Physical(물리적)인 단계에서의 Database 설계

### 1. Normalization (정규화)

> Database 테이블을 효율적으로 설계하기 위해 테스트하고 수정하는 과정

- 테이블을 분해하여 중복을 제거하고, 데이터를 구조화하는 과정
