# Overview of the SQL Query Language

> 작성자: 김나현

## 목차

- 역사
- MySQL
- SQL 실습
  <br/><br/>

## **[Overview of the SQL Query Language](https://github.com/Poin-Book/2023.09-database/blob/main/Chapter%2003%20-%20Introdution%20to%20SQL/Item%2001%20-%20Overview%20of%20the%20SQL%20Query%20Lanuage/Note.md#overview-of-the-sql-query-language)**

> 역사

- IBM San Jose Research Laboratory에서 System R 프로젝트의 일환으로 개발된 IBM Sequel 언어
- Structured Query Language (SQL)로 이름이 바뀜
- ANSI와 ISO가 SQL을 표준화함
- 상용 시스템은 대부분의 SQL-92 기능들을 제공함

참고 자료: [http://soen.kr/book/sql/book/122.htm](http://soen.kr/book/sql/book/122.htm), [https://dinae.tistory.com/28](https://dinae.tistory.com/28)

<br/>

> MySQL

- 무료 오픈소스 데이터베이스 관리 시스템 (DBMS)
  - “시퀄” 또는 철자 그대로 “에스큐엘”이라고 읽음
- 웹 애플리케이션(LAMP의 구성 요소)과 함께 사용하기 위한 데이터베이스 시스템으로서 대중적인 선택
- 다양한 웹 사이트에 널리 사용됨

<br/>

> SQL 실습

<aside>
💡 MySQL 명령 및 SQL 데이터베이스/테이블/속성 이름은 대소문자를 구분하지 않음

</aside>

1. DB 생성

   ```sql
   create database mydb;
   ```

   → `mydb`라는 이름으로 데이터 베이스를 만들어라

2. 생성한 DB 사용

   ```sql
   use mydb;
   ```

3. DB 관리

   ```sql
   show database; // DB들의 리스트를 표시ㅏ라
   use mydb; // mydb DB를 사용한다
   delete database mydb;
   drop database mydb;
   ```

   - `DELETE`: DB 내부의 데이터만 없어짐
   - `DROP`: attribute까지 없어짐

   참고자료: [https://developer-talk.tistory.com/258](https://developer-talk.tistory.com/258)
