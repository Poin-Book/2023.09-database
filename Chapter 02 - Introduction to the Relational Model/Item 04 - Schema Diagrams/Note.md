# Schema Diagrams

> 작성자: 김나현

## 목차

- Schema Diagram의 예시
- 다이어그램 해석법

## Schema Diagrams의 예시

![[https://velog.io/@seyeop03/Chapter-3.-관계형-데이터-모델-DB-Sample](https://velog.io/@seyeop03/Chapter-3.-%EA%B4%80%EA%B3%84%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8-DB-Sample)](https://velog.velcdn.com/images/seyeop03/post/0b5381b6-bb9f-4bab-b4f3-6fcbdb45c3db/image-20211027172741110.png)

[https://velog.io/@seyeop03/Chapter-3.-관계형-데이터-모델-DB-Sample](https://velog.io/@seyeop03/Chapter-3.-%EA%B4%80%EA%B3%84%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8-DB-Sample)

**관계**(table)로 구성된 데이터베이스의 예시

## 다이어그램 해석법

- 각 relation에서 밑줄친 속성: `primary key`
  - 모든 테이블은 반드시 한 개 이상의 primary key가 필요
- **각 화살표**는 참조 무결성 제약을 나타냄
  - 예를 들어 teaches 관계의 cID 속성은 course 관계의 primary key 속성인 cID 속성을 참조하는 foreign key(외래 키)이다.
