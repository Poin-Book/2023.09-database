# 과제 풀이

> 작성자: 심세원
### Database System Concept 7th Problem Solving
Chapter 1

## 목차
- [1.4](#1.4)
- [1.7](#1.7)
- [1.10](#1.10)
- [1.15](#1.15)

<br>

## 문제 풀이

<br>

# 1.4

Suppose you want to build a video site similar to YouTube. Consider each of the
points listed in Section 1.2 as disadvantages of keeping data in a file-processing
system. Discuss the relevance of each of these points to the storage of actual
video data, and to metadata about the video, such as title, the user who uploaded
it, tags, and which users viewed it

→ 데이터 처리 시스템에서 데이터를 파일 처리 시스템에 저장하는 단점에 대한 내용을 논의하라 .

 특히 비디오 데이터와 비디오에 관한 메타데이터 (예: 제목, 업로드한 사용자, 태그 및 비디오를 본 사용자)에 대한 이러한 단점이 어떻게 관련되는지에 중점을 두고 논의할 것

 <br>

## 풀이

## 1. **데이터 중복성 (Data Redundancy)**


비디오 데이터 → 동일한 비디오가 여러 사용자에 의해 업로드 되고 저장

### 이러한 중복성은 저장공간을 낭비하고 비효율적인 데이터 관리를 초래함

메타데이터 또한 중복될 수 있다. 

ex) 여러 사용자가 동일한 비디오에 대한 태그를 추가할 때

### file-processing system

- 데이터는 각 응용 프로그램마다 **별도의 파일**로 저장됨
- 동일한 데이터가 **여러 파일에 중복 저장**될 수 있음

→ 데이터 중복 문제

→ 데이터 일관성을 유지하기 어려울 수 있음

### Data-Base system

- **중앙 집중식 데이터베이스에 저장함**

→ 중복 데이터가 최소화됨

→ 데이터 일관성, 정확성을 향상시킴

## 2. **데이터 무결성 (Data Integrity)**


- 비디오 데이터의 무결성은 비디오 파일이 손상되거나 변경되지 않는지 확인하는 중요한 고려 사항

### file-processing system

- 파일이 손상되거나 데이터가 잘못 수정될 수 있음
- 이를 검증하거나 복구하기 어려움

### Data-Base system

- 데이터의 무결성을 위해 다양한 메커니즘을 제공함
- 데이터를 안정하게 저장하고 무결성 제약 조건을 적용하여 데이터의 정확성을 보장함

## 3. **데이터 독립성 (Data Independence)**


> 비디오 데이터 및 메타데이터의 독립성은 **시스템의 유연성을 결정하는 중요한 요소**
> 

### file-processing system

- 데이터 구조와 응용 프로그램이 강하게 결합되어 있어 데이터 구조 변경이 어려울 수 있음
- 각 응용프로그램은 자체 데이터 정의를 가지고 있음

### Data-Base system

- 데이터와 응용 프로그램을 분리하고 데이터 독립성을 제공함
- 데이터 구조 변경이 상대적으로 쉬워짐
- 여러 응용 프로그램이 동일한 데이터베이스를 공유할 수 있음

## 4. **데이터 보안 (Data Security)**

---

> 비디오 데이터 및 메타데이터에는 개인 정보와 민감한 정보가 포함될 수 있으므로 이러한 데이터의 보안이 중요
> 

### file-processing system

- 데이터의 보안 및 접근 제어를 관리하기 어렵고, 민감한 정보가 노출될 위험이 있음

### Data-Base system

- 데이터베이스 레벨에서 보안 및 접근 제어를 관리함
- 사용자 및 역할 기반의 세밀한 권한 관리를 제공하여 데이터의 안전성을 높임

## 5. **동시성 제어 (Concurrency Control)**


> 여러 사용자가 동시에 비디오 업로드, 수정 또는 메타데이터 변경을 시도할 때 데이터의 무결성을 유지하기 위한 제어가 필요
> 

### file-processing system

- 파일 단위로 동시 액세스 및 수정을 제어하기 어렵고 복잡함

### Data-Base system

- 동시성 제어 메커니즘을 제공함
- 여러 사용자가 동시에 데이터에 접근하거나 변경할 때 데이터의 일관성을 유지할 수 있음

<br>

# 1.7

List four significant differences between a file-processing system and a DBMS.

→ 파일 처리 시스템과 데이터베이스 관리 시스템(DBMS) 간의 네 가지 중요한 차이점

<br>

## 풀이

1. ***데이터 중복성 (Data Redundancy):***
    - ***`*file-processing system*`***: 파일 시스템에서 데이터는 여러 애플리케이션에서 중복으로 저장될 수 있습니다. 이로 인해 데이터 중복성이 발생하고 데이터 일관성이 유지하기 어려울 수 있음
    - ***`*DBMS*`***: DBMS는 중복 데이터를 최소화하고 중앙 데이터 저장소를 사용하여 데이터 일관성을 유지합니다. 이는 데이터의 정확성과 일관성이 향상됨
2. ***데이터 독립성 (Data Independence):***
    - ***`*file-processing system*`***: 데이터 구조가 애플리케이션과 강하게 결합되어 있어 데이터 구조 변경이 어려울 수 있으며, 각 애플리케이션은 데이터에 대한 자체 정의를 가짐
    - **`*DBMS*`**: DBMS는 데이터와 애플리케이션을 분리시키고 데이터 독립성을 제공합니다. 이로써 데이터 구조 변경이 용이하며, 여러 애플리케이션이 동일한 데이터베이스를 공유할 수 있음
3. ***데이터 보안 및 접근 제어 (Data Security and Access Control):***
    - ***`file-processing system`***: 파일 단위로 보안 및 접근 제어를 관리하기 어려울 수 있으며, 데이터의 보안이 취약할 수 있음
    - ***`DBMS`***: DBMS는 데이터베이스 레벨에서 보안 및 접근 제어를 관리하며, 사용자 및 역할 기반의 세밀한 권한 관리가 가능합니다. 이로써 데이터의 안전성을 높일 수 있음
4. ***동시성 제어 (Concurrency Control):***
    - ***`file-processing system`***: 여러 사용자가 동시에 데이터를 엑세스하거나 수정할 때 데이터의 무결성을 유지하기 어려움
    - ***`DBMS`***: DBMS는 동시성 제어 메커니즘을 제공하여 여러 사용자가 동시에 데이터에 접근하거나 변경할 때 데이터의 일관성을 유지합니다. 이는 다중 사용자 환경에서 안정성을 보장함

<br>

# 1.10

List at least two reasons why database systems support data manipulation using
a declarative query language such as SQL, instead of just providing a library of
C or C++ functions to carry out data manipulation.

→ 데이터베이스 시스템이 SQL과 같은 선언적 쿼리 언어를 지원하고 라이브러리 형태의 C 또는 C++ 함수를 제공하는 대신 선언적 쿼리 언어를 사용하는 이유

<br>

## 풀이

## 1. **데이터 독립성과 추상화 (Data Independence and Abstraction)**

> ***Declarative query language***를 사용하면 데이터베이스 시스템은 어떻게 데이터를 가져오고 조작할지에 대한 구체적인 **구현 세부사항**을 숨길 수 있음
> 

- 데이터베이스의 논리적 구조와 물리적 구현을 분리 가능
    - 데이터를 가져오고 조작하는 방법에 대한 구체적인 구현 세부사항을 숨길 수 있기 때문
- 데이터베이스 스키마가 변경되어도 쿼리는 변경하지 않고 사용할 수 있음
    - 데이터 구조의 변화에 따른 영향을 최소화하며 데이터 독립성을 제공함
- 사용자 및 응용 프로그래머는 데이터베이스에 대한 세부 사항을 몰라도 데이터를 조작할 수 있음
    - 데이터베이스 시스템의 유지 보수성과 확장성을 향상 시킴

## 2. **최적화와 최적 실행 계획 (Optimization and Query Execution Planning)**

> ***Declarative query language***를 사용하면 데이터베이스 시스템이 쿼리를 최적화하고 최적 실행 계획을 결정할 수 있음
> 
- 데이터베이스 시스템은 쿼리를 어떻게 효율적으로 실행할지를 판단함
    - 데이터베이스 시스템은 쿼리를 최적화하고 최적 실행 계획을 결정할 수 있음
- 쿼리에 대한 최적 실행 경로를 선택함
    - 데이터베이스 시스템은 쿼리가 어떻게 효율적으로 실행될지를 판단하고, 쿼리에 대한 최적 실행 경로를 선택함
- 데이터베이스 성능을 최적화하고 응답 시간을 최소화하는 데 도움이 됨

→ C 또는 C++ 라이브러리를 사용하면 이러한 최적화 및 최적 실행 계획 생성이 더 어렵고 복잡해짐

→ 응용 프로그래머가 직접 최적화를 수행해야 하므로 개발 및 유지 보수가 더 어려워짐

### 따라서, 선언적 쿼리 언어를 사용하는 것은 데이터베이스 시스템의 유지 보수성과 성능 최적화를 향상시키는 데 도움을 주며, 사용자 및 응용 프로그래머가 데이터베이스를 보다 효과적으로 활용할 수 있게 함

<br>

# 1.15

Describe at least three tables that might be used to store information in a socialnetworking
system such as Facebook.

→소셜 네트워킹 시스템(예: Facebook)에서 정보를 저장하는 데 사용되는 세 가지 테이블을 설명해라

<br>

## 풀이

### **User (사용자) 테이블:**

- 이 테이블은 모든 사용자에 대한 정보를 저장합니다. 각 행은 개별 사용자를 나타내며 고유한 사용자 ID를 포함.
- 열에는 사용자의 개인 정보가 포함될 수 있으며, 이에는 사용자 이름, 이메일 주소, 생일, 프로필 사진 URL 등이 포함
- 사용자 관계와 인증을 관리하기 위한 열도 포함될 수 있습니다. 예를 들어, 사용자의 비밀번호 해시, 로그인 상태 등을 저장하는 데 사용

ex)

```sql
CREATE TABLE User (
    UserID INT PRIMARY KEY,
    UserName VARCHAR(255),
    Email VARCHAR(255),
    Birthday DATE,
    ProfilePictureURL VARCHAR(255),
    PasswordHash VARCHAR(128)  -- 비밀번호 해시값 저장
);
```

### **Post (게시물) 테이블:**

- 이 테이블은 사용자가 생성한 게시물 및 게시물 관련 정보를 저장합니다. 각 행은 개별 게시물을 나타내며, 게시물 ID를 가지고 있음
- 열에는 게시물의 내용, 작성 시간, 작성자(사용자 ID), 좋아요 수, 댓글 수 등과 같은 정보가 포함
- 게시물과 사용자 간의 관계를 나타내는 외래 키 (예: 게시물 작성자)가 이 테이블에 포함

ex)

```sql
CREATE TABLE Post (
    PostID INT PRIMARY KEY,
    Content TEXT,
    CreationTime TIMESTAMP,
    AuthorID INT,  -- 외래 키: 게시물 작성자의 UserID
    Likes INT,
    Comments INT
);
```

### **Friendship (친구 관계) 테이블:**

- 이 테이블은 사용자 간의 친구 관계를 저장합니다. 각 행은 두 사용자 간의 친구 관계를 나타내며, 양방향으로 저장
- 열에는 친구 관계를 구성하는 두 사용자의 사용자 ID가 포함
- 이 테이블은 친구 관계를 쉽게 확인하고 조회하기 위해 사용. 사용자가 친구 목록을 볼 때 또는 친구 제안을 생성할 때 유용

ex)
```sql
CREATE TABLE Friendship (
    FriendshipID INT PRIMARY KEY,
    UserID1 INT,  -- 외래 키: 첫 번째 사용자의 UserID
    UserID2 INT,  -- 외래 키: 두 번째 사용자의 UserID
    CONSTRAINT FK_UserID1 FOREIGN KEY (UserID1) REFERENCES User(UserID),
    CONSTRAINT FK_UserID2 FOREIGN KEY (UserID2) REFERENCES User(UserID)
);
```