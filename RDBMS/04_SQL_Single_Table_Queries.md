# SQL - Single Table Queries 1
- 학습목표
    - 단일 테이블 내에서 SELECT 문을 사용하여 테이블의 특정 결과를 반환할 수 있다
    - SELECT 문과 함께 다양한 절을 사용해 쿼리 결과를 정렬 및 필터링 할 수 있다.
    - GROUP BY 와 Aggregation Function을 사용해 각 데이터 값에 대한 계산된 단일 값을 그룹화하여 반환할 수 있다.

---
## Querying data
---

- SELECT syntax
    - SELECT 키워드 다음에 데이터를 선택하려는 필드를 하나 이상 지정
    - FROM 키워드 다음에 데이터를 선택하려는 테이블의 이름을 지정

        ```sql
            SELECT
                select_list
            FROM
                table_name;
        ```

- 연산 가능 
    - `+`
        - 더하기
    - `-`
        - 빼기
    - `*`
        - 곱하기
    - `/`
        - 나누기

- keyword 
    - AS
        - 필드에 새로운 별칭을 지정
        
            ```sql
                SELECT
                    firstName AS '이름'
                -- firstName 필드를 이름 으로 변경후 출력
                FROM
                    employees;
            ```
    - `,`
        - 콤마로 테이블 및 필드를 나눠줌

    - `SELECT *`
        - 테이블의 모든 필드 선택


---
## Sorting data
---
- ORDER BY syntax
    - 조회 결과의 레코드를 정렬
    - FROM clause 뒤에 위치
    - 하나 이상의 컬럼을 기준으로 결과를 오름차순, 내림차순으로 정렬할 수 있음
        - ASC - 오름차순 (기본 값)
            - 기본값이므로 입력 안해도 적용
        - DESC - 내림차순

            ```sql
                SELECT
                    select_list
                FROM
                    table_name
                ORDER BY
                    column1 ASC,
                    column2 DESC;
                -- column1 을 오름차순
                -- column2 를 내림차순
            ```

- SELECT statement 실행 순서
    1. 테이블에서 (FROM)
    2. 조회하여 (SELECT)
    3. 정렬 (ORDER BY)

        ```mermaid
            graph LD;

            FROM--> SELECT -->ORDER_BY;
        ```