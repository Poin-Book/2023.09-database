# The Relational Algebra

> 작성자: 김나현

## 목차

- 관계 대수
- Operation 예시

## 관계 대수

- 관계 대수식이란 기존 relation(table)들로부터 새로운 relation을 생성하는 절차적 언어 문법이라고 보면 된다. relation에 대해 기본적인 연산자들을 적용하여 보다 복잡한 관계 대수식을 점차적으로 만들 수 있다.
- 절차적 언어는 하나 또는 두 개의 관계를 입력으로 받아들이고 그 결과로 새로운 관계를 생성하는 일련의 연산으로 구성됨
- 기본적인 6가지 연산자
  - select: **σ**
  - project: **∏**
  - union: **U**
  - set difference: **-**
  - cartesian product: **x**
  - rename: **ρ**
- 경우
  - tuple (unary): Selection, Projectino
  - set (binary): Union, Intersection, Difference
  - tuple (binary): Join, Division

![[https://velog.io/@ieed0205/관계대수-SQL-LEEToday](https://velog.io/@ieed0205/%EA%B4%80%EA%B3%84%EB%8C%80%EC%88%98-SQL-LEEToday)](https://velog.velcdn.com/images/ieed0205/post/74c8e8d9-1aed-4bf8-aa84-9eec08e269f8/123.PNG)

[https://velog.io/@ieed0205/관계대수-SQL-LEEToday](https://velog.io/@ieed0205/%EA%B4%80%EA%B3%84%EB%8C%80%EC%88%98-SQL-LEEToday)

![[http://itnovice1.blogspot.com/2019/08/database_29.html](http://itnovice1.blogspot.com/2019/08/database_29.html)](https://1.bp.blogspot.com/-s6QBJhFMTZo/XWd_rHvw-2I/AAAAAAAABnM/UGPGz-M2LZMZ129cs8fF-KUhQaIs2jkLQCLcBGAs/s640/%EC%BA%A1%EC%B2%98.JPG)

[http://itnovice1.blogspot.com/2019/08/database_29.html](http://itnovice1.blogspot.com/2019/08/database_29.html)

## Operation 예시

> Selection Operation (σ)

- 원하는 데이터를 **수평적**으로 도출
- 중복이 존재하지 않음

![Untitled](Image/Untitled%201.png)
</br>

> Projection Operation **(∏)**

- 원하는 데이터를 수직적으로 도출
- 중복이 나타날 수 있음

![Untitled](Image/Untitled%202.png)
</br>

> Union Operation (U)

- 합집합
- Union compatibility: 두 relation의 attribute 수가 같고, 대응되는 도메인도 같아야 함
- 합집합의 경우 위의 합칩합 호환 조건이 맞아야만 합칠 수 있음

![Untitled](Image/Untitled%203.png)
</br>

> Difference Operation (-)

- 차집합
- 위의 Union Operation과 같이 합집합 호환 조건이 맞아야만 뺼 수 있음

![Untitled](Image/Untitled%204.png)
</br>

> Intersection Operation (∩)

- 교집합
- r ∩ s = r - (r-s)

![Untitled](Image/Untitled%205.png)
</br>

> Cartesian Product (x)

- _Joining two relations_
- R과 S의 릴레이션에 속해있는 모든 경우의 수들을 테이블화 시켜줌
- 행렬의 곱과 비슷

![Untitled](Image/Untitled%206.png)
</br>

> Natural Join (∞)

- 두 relation을 join
- 두 테이블의 연관된 칼럼끼리 통합해주는 역할
- 상호 연산이 안된 데이터는 명시되지 않음

![Untitled](Image/Untitled%207.png)
</br>

> Division Operation (%)

![Untitled](Image/Untitled%208.png)

[참고 자료]
[📋 관계 대수 & 관계 해석 표현법 💯 총정리](https://inpa.tistory.com/entry/DB-📚-관계-대수-관계-해석-SQL-🕵️-정리)
[[SQL] 관계대수? SQL?](https://velog.io/@ieed0205/관계대수-SQL-LEEToday)
