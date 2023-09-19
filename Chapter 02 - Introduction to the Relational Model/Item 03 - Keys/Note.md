# Keys

> 작성자: 김나현

## 목차

- Key 모아보기
  - Super Key
  - Candidate Key
  - Primary Key
  - Foreign Key

## Keys 모아보기

![https://media.geeksforgeeks.org/wp-content/uploads/20230314174012/Different-types-of-keys.png](https://media.geeksforgeeks.org/wp-content/uploads/20230314174012/Different-types-of-keys.png)

| 키 이름       | 요약 설명                                                                                        |
| ------------- | ------------------------------------------------------------------------------------------------ |
| Super Key     | 데이터를 독특하게 구별할 수 있는 모든 조합                                                       |
| Candidate Key | 튜플을 유일하게 결정할 수 있는 최소 세트. 기본키가 될 수 있는 후보이기 때문에 후보키라고 불린다. |
| Primary Key   | 데이터베이스 디자이너에 의해 선택된, 후보키 중 하나                                              |
| Foreign Key   | 서로 다른 테이블을 연결할 수 있는 키                                                             |
| Alternate Key | 후보키 중 기본키로 선택되지 않은 키                                                              |

> Super Key

![[https://prepinsta.com/dbms/super-key/](https://prepinsta.com/dbms/super-key/)](https://prepinsta.com/wp-content/uploads/2023/01/Super-Key-in-DBMS.webp)

[https://prepinsta.com/dbms/super-key/](https://prepinsta.com/dbms/super-key/)

- 슈퍼 키는 테이블에서 행을 고유하게 식별하는 단일 또는 여러 키의 그룹
- 슈퍼 키는 고유 식별에 필요하지 않은 추가 속성을 가질 수 있음
- 어떤 속성끼리 묶던 중복값이 안나오고 서로 구별만 할 수 있으면 됨

> Candidate Key

![[https://prepinsta.com/dbms/candidate-key/](https://prepinsta.com/dbms/candidate-key/)](https://prepinsta.com/wp-content/uploads/2023/01/Candidate-Key-in-DBMS.webp)

[https://prepinsta.com/dbms/candidate-key/](https://prepinsta.com/dbms/candidate-key/)

- 슈퍼 키 중 중복 속성이 없는 것을 후보 키라 부름
- 기본 키가 될 수 있는 후보라는 의미
- 때문에 후보 키는 최소 슈퍼 키라고도 불림

> Primary Key

![[https://prepinsta.com/dbms/primary-key/](https://prepinsta.com/dbms/primary-key/)](https://prepinsta.com/wp-content/uploads/2023/01/Primary-Key-in-DBMS.webp)

[https://prepinsta.com/dbms/primary-key/](https://prepinsta.com/dbms/primary-key/)

- 후보키들 중에서 하나를 선택한 키로 최소성과 유일성을 만족하는 속성
- 때로는 데이터베이스 테이블의 모든 행을 고유한 것으로 유지해야 함. 이러한 목적은 해당 특정 열에 기본 키를 사용함으로써 충족됨
- 데이터베이스 디자이너에 의해 선택된, 후보키 중 하나
- 바뀌지 않는 값을 키로 설정하는 게 좋음
- 기본키는 \*\*\*\*NULL 값을 절대 가질수 없고, 중복된 값을 가질 수 없다.

> Foreign Key

![[https://prepinsta.com/dbms/foreign-key/](https://prepinsta.com/dbms/foreign-key/)](https://prepinsta.com/wp-content/uploads/2023/01/Foreign-Key-in-DBMS.webp)

[https://prepinsta.com/dbms/foreign-key/](https://prepinsta.com/dbms/foreign-key/)

- 외래키는 참조되는 테이블의 **기본키와 동일한 키 속성**을 가진다.
  - 다른 테이블의 attribute 데이터와 정확히 동일한 테이블의, 동일한 데이터만 유지 및 제한해야 하는 경우가 있음 → 외부 키를 사용하여 충족
- 일반적으로 한 테이블의 primary key로 지정된 키를 foreign key로 지정
- `참조하는`(Student_Mark): referencing relation (child),
  `참조되는`(Student_Details): referenced relation (parents) - 참조되는 부모 테이블이 먼저 생성된 뒤 데이터를 넣고, 참조하는 자식 테이블이 그 다음에 생겨야 함 - 부모 테이블 먼저 삭제될 수 없음. 왜냐하면 부모 테이블이 삭제되면 자식 테이블은 참조하는 것이 없어지기 때문에 외래키 오류가 발생함. 따라서 외래키 관계에서 부모 테이블을 삭제하려면 **자식 테이블 먼저 삭제**한 후 부모 테이블을 삭제해야한다.

[결론]

![[https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/](https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/)](https://media.geeksforgeeks.org/wp-content/uploads/20230314093236/keys-in-dbms.jpg)

[https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/](https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/)

- 슈퍼키가 minimal 하면 후보키가 되는 것. 그리고 후보키 중 DB 설계자(혹은 개발자)가 선택한 것이 기본키가 되는 것

[참고 자료]

[[DB] 📚 데이터베이스 키(KEY) 종류 🕵️ 정리](https://inpa.tistory.com/entry/DB-📚-키KEY-종류-🕵️-정리)
