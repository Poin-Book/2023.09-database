# Introduction - Part 1

> 작성자: 이재혁

## 목차
1. DBMS
2. Drawbacks of File Systems
3. Schemas and Instances
4. Data Models
5. Data Definition Language (DDL)
6. Structured Query Language (SQL)


## 1. Database Management System (DBMS)
- DBMS contains information about a particular organization
    - Collection of inter-related data
    - Set of programs to access those data
    - An environment that is _convenient_ and _efficient_ to use
- Databases can be very large

### Database-System Applications
Database systems are used to manage collections of data that:
> - are highly valuable,
> - are relatively large, and
> - are accessed by multiple users and applications, often at the same time

#### Database applications:
    - Banking
    - Airlines
    - Universities
    - Sales
    - Manufacturing
    - Human resources

#### Example: University Database
    - Add new students, instructors, and courses
    - Register students for courses, and generate class rosters
    - etc...

### Two modes in which databases are used:
1. **online transaction processing(oltp)**
을 지원 : <br>
각 사용자는 비교적 적은 양의 데이터를 검색하고 작은 업데이트를 수행한다. 데이터베이스 애플리케이션의 대다수 사용자에 대한 주요 사용 모드 <br> 참고: <https://www.oracle.com/kr/database/what-is-oltp/>

2. **data analytics**를 지원 : <br>결론 도출을 위한 데이터 처리를 지원하고 규칙이나 의사결정 절차를 추론 -> 이를 통해 의사결정을 추진하는 데 사용 

## 2. Drawbacks of File Systems
> 데이터베이스가 있기 전에는 데이터를 어떻게 사용했을까<br>
> -> **File System**을 사용했음 : <br>
> 파일 시스템에서는 각각의 응용프로그램이 독자적인 파일을 갖고 있었음. <br>
> 그러나 파일 시스템에는 여러가지 문제점 有

**1. Data redundancy and inconsistency** (데이터 중복 및 불일치)  <br>
- 오랜 시간에 걸쳐 파일과 응용 프로그램을 만들기 때문에 다양한 파일이 서로 다른 구조를 가질 가능성이 높고, 프로그램은 여러 프로그래밍 언어로 작성될 수 있음.
- **\+** 동일한 정보가 여러 곳(파일)에서 중복될 수 있음
- ex) 음악과, 수학과 복수전공하는 학생:
    - 음악과 학생목록 파일과 수학과 학생목록 파일에 같은 학생의 주소와 전화번호가 나타날 수 있음
- 이러한 redundancy는 higher storage와 access cost를 유발함.<br>
-> 자료의 분산으로 일관된 자료 처리의 어려움, 데이터 저장공간 낭비, 데이터 효율성 감소<br>
-> 또한, 이러한 Data redundancy는 **Data inconsistency (불일치)** 도 유발<br>
즉, 동일한 데이터의 다양한 복사본이 더 이상 일치하지 않게 될 수도 있음.
    - ex) 변경된 학생의 주소는 음악과 기록에는 반영되어도, but 수학과 기록에는 반영되지 않을 수 있음


**2. Difficulty in accessing data**
- 특정 우편 번호 지역에 사는 모든 학생들의 이름을 조회해야 한다고 가정:
    - 목록을 만들어 달라고 자료 처리 부서에 요청 <br>
    -> 원래 시스템 설계자는 이 요청을 예상 못하기 때문에, 이를 충족시킬 프로그램이 없음.  <br>
    -> 하지만 모든 학생들의 목록을 만들어 내는 응용 프로그램은 이미 있음 <br>
    -> 이때 두 가지 선택지 존재 : 
        - 모든 학생들의 목록을 얻고 필요한 정보를 수동으로 추출
        - 프로그래머에게 필요한 프로그램 만들어 달라고 요청
        - 이 두 가지 모두 별로임 <br>
- 프로그램을 만들었다고 했을 때, 며칠 후 그 목록에서 최소 60학점 이상 이수한 학생들만을 포함하도록 다듬는다고 가정할 때, **동일한 문제가 반복**
- 여기서 요점은, 종래의 file-processing 환경은 필요한 데이터를 _convenient and efficient_ 한 방식으로 검색하는 것을 허용하지 못한다는 것. <br>
-> 일반적인 사용을 위해서는 보다 응답성이 높은 데이터 검색 시스템이 필요

**3. Data isolation**
- 데이터가 다양한 파일에 흩어져 있고, 파일이 다른 포맷일 수 있기 때문에, 적절한 데이터를 검색하기 위해 새로운 프로그램을 작성하는 것이 어려움.

**4.Integrity problems** (무결성 문제)
- **데이터 무결성**: 저장된 데이터의 내용이 본래 의도했던 데이터의 형식, 범위를 준수해야 하는 성질
- DB에 저장된 데이터 값은 일정한 유형의 Integrity constraints을 만족해야 함.
- Ex) 학생 정보 파일에서 나이는 양의 Integer이어야 하는데 음수의 데이터가 저장되면 무결성에 위배
- DB 시스템에서는 DBMS가 이를 해결해 주지만, File System에서는 프로그래머가 무결성을 검사하는 기능을 구현해야 함
    ```
    if (나이 != 양수)
        error;
    ```

**5. Atomicity of updates** (원자성)
- 프로그램에서 장애가 발생하면 데이터가 이전에 존재했던 일관된 상태로 복원되는 것이 매우 중요
- ex) 500달러를 계좌 A에서 계좌 B로 이체할 때 장애가 발생.
    - A에서 500달러가 제거되었지만 B에 입금되지 않아서 일관성 없는 상태가 되었을 가능성이 있음
    - 자금 이체는 Atomic해야 함. 전체적으로 발생해야 하거나, 전혀 발생하지 않아야 함
    - 기존의 파일 처리 시스템에서는 원자성을 보장하기가 어려움

**6. Concurrent-access anomalies**
- 시스템의 전반적인 성능과 보다 빠른 응답을 위해 많은 시스템들이 여러 유저들이 동시에 데이터를 업데이트할 수 있도록 한다. 
- 동시 접속을 통한 업데이트들의 상호작용이 가능한데, 이는 데이터의 일관성을 해칠 수 있음
- ex) 은행원 두 명이 잔액이 $10,000인 계좌 A에서 거의 동시에 각각 $500, $100을 인출할 때, 동시에 실행된 결과가 부정확하거나 일관되지 않은 상태의 계좌 잔액을 남길 수 있음
    - 인출 프로그램(이전 잔액을 읽고 인출되는 금액만큼 그 값을 줄이고 다시 결과를 쓰는)이 동시에 두 번 실행된다면,
    - 각각 $10,000을 읽은 후 $500, $100을 인출해서 $9,400의 정확한 금액이 아닌 $9,500 또는 $9,900이라는 잘못된 잔액이 포함될 수 있음
- 이런 가능성을 방지하기 위해 시스템은 관리감독을 유지해야 함

**7. Security problems**
- DB 시스템의 모든 유저가 모든 데이터에 접근 가능해야 하는 것은 아님
- ex) 대학 급여 담당자는 재정 정보 DB 부분만 볼 수 있으면 됨. -> 학업 기록에 접근할 필요가 없음
- 하지만 임시방편으로 파일 처리 시스템에 추가된 프로그램들은 이런 보안 제약을 강제하기 어려움

#### 이러한 문제들은 1960~70년대 DB 시스템의 개발과 파일 기반 응용 프로그램의 DB 시스템으로의 전환을 촉발시켰음