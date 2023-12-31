# Transaction

> 작성자: 최선규

- [Transaction](#transaction)
  - [Transaction이란?](#transaction이란)
  - [트랜잭션 특징](#트랜잭션-특징)

## Transaction이란?

> "더이상 분할이 불가능한 업무처리의 단위"

하나의 작업을 위해 더이상 분할될 수 없는 명령들의 모음, 즉 한꺼번에 `수행되어야 할 일련의 연산모음`을 의미하다.

예를 들어 계좌이체 라는 행위는 `인출`과 `입금` 두 과정으로 이루어진다.

만약 인출에는 성공했는데, 입금에 실패하면 치명적인 결과가 나온다.

따라서 이 두 과정은 동시에 성공하던지 동시에 실패해야 한다. (이런 특성을 `Atomic`이라고 한다.)

```sql
START TRANSACTION
    -- 이 블록안의 명령어들은 마치 하나의 명령어 처럼 처리됨
    -- 성공하던지, 다 실패하던지 둘중 하나가 됨.
    A의 계좌로부터 인출;
    B의 계좌로 입금;
COMMIT
```

이와 같이, 데이터베이스와 어플리케이션의 데이터 거래(Transaction)에 있어서 안전성을 확보하기 위한 방법이 트랜잭션이다.

따라서 데이터베이스에서 테이블의 데이터를 읽어 온 후 다른 테이블에 데이터를 입력하거나 갱신, 삭제하는 도중에 `오류`가 발생하면, `결과를 재반영 하는 것이 아니라` `모든 작업을 원상태로 복구`하고, 처리 과정이 `모두 성공하였을때 만 그 결과를 반영`한다.

## 트랜잭션 특징

- 원자성(Atomicity)
  - 원자성은 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다는 것이다.  
  - 트랜잭션은 사람이 설계한 논리적인 작업 단위로서, 일처리는 작업단위 별로 이루어 져야 사람이 다루는데 무리가 없다.
  - 만약 트랜잭션 단위로 데이터가 처리되지 않는다면, 설계한 사람은 데이터 처리 시스템을 이해하기 힘들 뿐만 아니라, 오작동 했을시 원인을 찾기가 매우 힘들어질것이다.

- 일관성 (Consistency)
  - 일관성은 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다는 것이다.
  - 트랜잭션이 진행되는 동안에 데이터베이스가 변경 되더라도 업데이트된 데이터베이스로 트랜잭션이 진행되는것이 아니라, 처음에 트랜잭션을 진행 하기 위해 참조한 데이터베이스로 진행된다.
  - 이렇게 함으로써 각 사용자는 일관성 있는 데이터를 볼 수 있는 것이다.

- 독립성 (Isolation)
  - 독립성은 둘 이상의 트랜잭션이 동시에 실행되고 있을 경우 어떤 하나의 트랜잭션이라도, 다른 트랜잭션의 연산에 끼어들 수 없다는 점을 가리킨다.
  - 하나의 특정 트랜잭션이 완료될때까지, 다른 트랜잭션이 특정 트랜잭션의 결과를 참조할 수 없다.

- 영구성 (Durability)
  - 지속성은 트랜잭션이 성공적으로 완료됬을 경우, 결과는 영구적으로 반영되어야 한다는 점이다.
