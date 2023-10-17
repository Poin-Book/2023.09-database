# Join Expressions

> 작성자: 최선규

- [Join Expressions](#join-expressions)
  - [JOIN Conditions](#join-conditions)
    - [JOIN 조건으로 사용되는 연산자에 따른 분류](#join-조건으로-사용되는-연산자에-따른-분류)
    - [FROM 절의 JOIN 형태에 따른 분류](#from-절의-join-형태에-따른-분류)
    - [Inner / Outer 조인과 Equi 조인의 차이](#inner--outer-조인과-equi-조인의-차이)

## JOIN Conditions

[JOIN을 구별하는 두 가지 분류]

1. JOIN 조건으로 사용되는 연산자에 따른 분류
2. FROM 절의 JOIN 형태에 따른 분류

### JOIN 조건으로 사용되는 연산자에 따른 분류

- EQUI 조인
  - `=` 연산자를 사용하는 조인

```sql
SELECT column_list
FROM table1, table2 ...
WHERE table1.column_name = table2.column_name;

or -----------------------------

SELECT column_list
FROM table1
JOIN table2
ON (table1.column_name = table2.column_name);
```

- NON EQUI 조인
  - 두 테이블 간의 값들이 서로 일치하지 않는 경우, Join 조건으로 BETWEEN ~ AND 등의 범위 비교 연산자를 사용

```sql
SELECT column_list
FROM table1, table2 ...
WHERE table1.column_name BETWEEN table2.column_name1 AND table2.column_name2;

or -----------------------------

SELECT column_list
FROM table1
JOIN table2
ON (table1.column_name BETWEEN table2.column_name1 AND table2.column_name2);
```

### FROM 절의 JOIN 형태에 따른 분류

- INNER 조인 : Join 조건에서 값이 일치하는 행만 반환

- OUTER 조인 : Join 조건에서 한쪽 값이 없더라도 다른 한쪽 값이 존재하는 행을 반환
  - LEFT OUTER JOIN
  - RIGHT OUTER JOIN
  - FULL OUTER JOIN

```sql
SELECT column_list
FROM table1
INNER JOIN table2
ON (table1.column_name = table2.column_name);

-----------------------------

SELECT column_list
FROM table1
LEFT OUTER JOIN table2
ON (table1.column_name = table2.column_name);

-----------------------------

SELECT column_list
FROM table1
RIGHT OUTER JOIN table2
ON (table1.column_name = table2.column_name);
```

### Inner / Outer 조인과 Equi 조인의 차이

> 위 두 분류는 완전히 구분되는 개념이 아니다.

Equi 조인과 Inter 조인의 차이는 Join condition에 따라 달라진다. Inner 조인은 `=`, `<>`, `>`, `<` 같은 operator를 사용할 수 있는 반면 Equi 조인은 `=`만 사용할 수 있다.

- `=`만을 사용해 join query를 만들 경우 해당 쿼리는 Equi 조인이 된다.

즉, Equi 조인의 제약점은 조인을 생성하려는 두 테이블의 칼럼에서 공통된 값이 없다면 데이터를 반환할 수 없다는 것이다. 따라서 Outer 조인은 한쪽 값이 없더라도 행을 반한하기 때문에 Equi 조인이 될 수 없다.