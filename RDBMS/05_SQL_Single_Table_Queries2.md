# SQL - Single Table Queries 2
- 학습목표
	- 단일 테이블 내에서 `SELECT `문을 사용하여 테이블의 특정 결과를 반환할 수 있다.
	- `SELECT` 문과 함께 다양한 절을 사용해 쿼리 결과를 정렬 및 필터링 할 수 있다.
	- `GROUP BY` 와 `Aggregation Function` 을 사용해 각 데이터 값에 대한 계산된 단일 값을 그룹화하여 반환할 수 있다.

## Filtering data 관련 Keywords
- Clause
	- `DISTINCT` clause
		- 조회 결과에서 중복된 레코드를 제거
		- `SELECT` 키워드 바로 뒤에 작성
		- `SELECT DISTINCT` 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드를 지정
		```sql 
			--DISTINCT syntax
			SELECT DISTINCT
				select_list
			FROM
				table_name;
		```
		
	- `WHERE` clause
		- 조회 시 특정 검색 조건을 지정
		- `FROM` clause 뒤에 위치
		- serch_condition은 `비교연산자` 및 `논리연산자(AND,OR,NOT등)`을 사용하는 구문이 사용됨
		```sql
			-- WHERE syntax
			SELECT
				select_list
			FROM
				table_name
			WHERE
				search_condition;
		```
	- `LIMIT` clause
		- 조회하는 레코드 수를 제한
		- `LIMIT` clause 는 하나 또는 두개의 인자를 사용 (0 또는 양의 정수)
		- row_count 는 조회할 최대 레코드 수를 지정
		```sql
			-- LIMIT syntax
			SELECT
				select_list
			FROM
				table_name
			LIMIT [offset,] row_count;
			-- LIMIT 3, 5;
			-- LIMIT 5 OFFSET 3;
			-- 1,2,3,4,5,6,7,8 중
			-- offset 이 3이면 4부터 5개의 숫자인 8까지
			-- 4,5,6,7,8
		```
- Operator
	- BETWEEN
	- `IN` operators
		- 값이 특정 목록 안에 있는지 확인
	- `LIKE` operator
		- 값이 특정 패턴에 일치하는지 확인 with Wildcards
			- `Wildcard Characters`
				- `%`
					- 0 개 이상의 문자열과 일치 하는지 확인
				- `_`
					- 단일 문자와 일치 하는지 확인
	- Comparison
	- Logical

- `GROUP BY`clause
	- 레코드를 그룹화하여 요약본 생성 with 집계 함수
	- 집계 함수 (Aggregation Functions)
		- 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
			- `SUM`, `AVG`, `MAX`, `MIN`, `COUNT`
	- `FROM` 및 `WHERE` 절 뒤에 배치
	- `GROUP BY` 절 뒤에 그룹화 할 필드 목록을 작성
	
		```sql
			-- GROUP BY syntax
			SELECT
				c1, c2, ...., cn, aggregate_function(ci)
			FROM
				table_name
			GROUP BY
				c1, c2, ...., cn;
		```
		- `HAVING` clause
			- 집계 항목에 대한 세부 조건을 지정
			- `GROUP BY` 뒤에 배치
			- 주로 `GROUP BY` 와 함께 사용되며, `GROUP BY` 가 없다면, `WHERE` 처럼 동작

- `SELECT statement` 실행 순서

```memaid	
	graph  LR;
	A(FROM)-->B(WHERE)-->C(GROUP BY)-->D(HAVING)-->G(SELECT)-->
	H(ORDER BY)-->I(LIMIT);
```


1. 테이블에서 `FROM`
2. 특정 조건에 맞춰 `WHERE`
3. 그룹화 하고 `GROUP BY`
4. 만약 그룹 중에서 조건이 있다면 맞추고 `HAVING`
5. 조회하여 `SELECT`
6. 정렬하고 `ORDER BY`
7. 특정 위치의 값을 가져온다 `LIMIT`