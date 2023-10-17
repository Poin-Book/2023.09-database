# Integrity Constraints

> 작성자: 최선규

## Not Null

`NOT NULL` 제약 조건은 특정 컬럼에 `NULL` 값을 허용하지 않는다는 것을 의미한다.

ex)

  ```sql
  CREATE TABLE table_name (
      column_name1 datatype NOT NULL,
      column_name2 datatype,
      ...
  );
  ```

## Unique

'UNIQUE' 제약 조건은 특정 컬럼에 중복된 값을 허용하지 않는다는 것을 의미한다.

ex)

  ```sql
  CREATE TABLE table_name (
      column_name1 datatype UNIQUE,
      column_name2 datatype,
      ...
  );
  ```

## Check clause

`CHECK` 제약 조건은 특정 컬럼에 특정 조건을 만족하는 값만 허용한다는 것을 의미한다.

ex)

  ```sql
  CREATE TABLE table_name (
      column_name1 datatype,
      column_name2 datatype,
      ...
      CHECK (column_name1 > 0)
  );
  ```
