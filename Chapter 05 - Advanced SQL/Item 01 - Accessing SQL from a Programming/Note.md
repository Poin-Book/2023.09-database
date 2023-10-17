# Accessing SQL from a Programming Language

> 작성자: 최선규

## API (Application Programming Interface)

- 프로그래밍 언어가 제공하는 기능을 제어할 수 있도록 하는 인터페이스
- application에서는 다음을 사용할 수 있도록 한다.
  - 데이터베이스 연결
  - 데이터베이스에 SQL command 전송
  - program variables와 SQL result 사이의 데이터 매핑

## JDBC (Java Database Connectivity)

- Java에서 SQL을 사용할 수 있도록 하는 API
- 데이터 query 및 update, query 결과 처리 등을 위한 다양한 기능 제공
- 메타데이터 검색 지원

## ODBC (Open Database Connectivity)

- C, C++, C#, Python, R 등의 프로그래밍 언어에서 SQL을 사용할 수 있도록 하는 API
- 데이터 query 및 update, query 결과 처리 등을 위한 다양한 기능 제공
- GUI 기반의 프로그램 개발에 적합

## Embedded SQL

- SQL을 프로그래밍 언어에 내장시키는 방법
