# SQL - Basics
- 학습 목표
    - 데이터베이스에서 SQL 의 역활을 정의할 수 있다.
    - SQL 명령의 종류를 동작에 따라 3가지 이상 열거할 수 있다.
    - 표준 SQL 문법을 식별할 수 있다.

---
## Introduction to SQL
---
- SQL (Structure Query Language)
    - 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
    - 테이블의 형태로 구조화된 관계형 데이터베이스 에게 요청을 질의(요청)
    - 데이터베이스와 상호 작용하고, 데이터베이스에서 데이터를 반환하기 위한 언어

- SQL Syntax
    - SQL 키워드는 대소문자를 구분하지 않음
        - 대문자로 작성하는 것을 권장
    - 각 SQL Statements 의 끝에는 세미콜론(`;`)이 필요
        - 세미콜론은 각 SQL Statements 를 구분하는 방법

---
## SQL Statements
---
- SQL 언어를 구성하는 가장 기본적인 코드 블록

```SQL
    -- 예시
    SELECT column_name FROM table_name;
    -- 해당 예시 코드는 SELECT Statement 라 부름
    -- SELECT, FROM 2개의 keyword로 구성
```

- SQL Statements 유형
    - 데이터베이스에서 수행 목적에 따라 대체로 4가지 범주로 나뉨
        - DDL (Data Definition Language)
            - 데이터 정의
        - DQL (Data Query Language)
            - 데이터 검색
        - DML (Data Manipulation Language)
            - 데이터 조작
        - DCL (Data Control Language)
            - 데이터 제어

    | 유형 | 역할 | SQL키워드 |
    |:-:|:-:|:-:|
    |DDL<br>(Data Definition Language)| 데이터의 기본 구조 및 형식 변경| CREATE <br> DROP <br> ALTER|
    |DQL <br>(Data Query Language)|데이터 검색|SELECT|
    |DML (Data Manipulation Language)|데이터 조작 <br> (추가,수정,삭제)| INSERT<br>UPDATE<B>DELETE|
    |DCL (Data Control Language)|데이터 및 작업에<br> 대한 사용자 권한 제어 |COMMIT<br>ROLLBACK<BR>GRANT<BR>REVOKE|


## 용어 정리
- Query
    - 질의 , 질문
    - 데이터베이스로부터 정보를 요청하는 것
    - 일반적으로 SQL로 작성하는 코드를 쿼리문(SQL문)이라 함
- SQL 표준
    - SQL 은 미국 국립 표준 협회(ANSI)와 국제 표준화 기구(ISO)에 의해 표준이 채택됨
    - 널리 사용되는 모든 RDBMS에서 SQL 표준을 지원
    - 다만 RDBMS 별로 독자적인 기능에 따라 표준을 벗어나는 문법이 존재하니 주의