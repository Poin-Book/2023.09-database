# SQL Data Types and Schemas

> 작성자: 최선규

## SQL Data Types

date:

- YYYY-MM-DD
- ex. 2021-01-01

time:

- HH:MM:SS
- ex. 12:30:00

timestamp:

- YYYY-MM-DD HH:MM:SS
- ex. 2021-01-01 12:30:00

interval:

- 시간 간격을 표현
- ex. 1 year 2 months 3 days 4 hours 5 minutes 6 seconds

## Index creation

```sql
create table student ( 
  ID varchar (5) primary key, 
  name varchar (20) not null, 
  dept_name varchar (20), 
  tot_cred numeric (3,0) default 0);

create index studentID_index on student(ID)
```
