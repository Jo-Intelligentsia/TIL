# SQL - Nested Queries
- 학습 목표
	- `SQL subquery` 가 무엇인지 이해하고, 조건에 따라 하나 이상의 테이블에서 데이터를 검색할 수 있다.
	- `SELECT`, `FROM`,` WHERE` 절 등 다양한 맥락에서 사용하는 subquert 를 작성할 수 있다.

## Subquery
- 단일 쿼리문에 여러 테이블의 데이터를 결합하는 방법
- 특징
	- 조건에 따라 하나 이상의 테이블에서 데이터를 검색하는데 사용
	- `SELECT`,`FROM`,`WHERE`,`HAVING` 절 등에서 다양한 맥락에서 사용

	```sql
		-- Subquery 예시
		-- table1 에서 가장 나이가 어린 사람을 삭제해야 한다면?
		SELECT MIN(age)
		FROM table1;
			+
		DELETE FROM table1
		WHERE age = 위에서 찾은 최소값;
			
		-- Subquery 로 변경
		DELETE FROM table1
		WHERE age = (
			SELECT MIN(age) FROM table1
		);
	```
## EXISTS 
- 쿼리 문에서 반환된 레코드의 존재 여부를 확인
- `subquert` 가 하나 이상의 행을 반환하면 `EXISTS` 연산자는 true를 반환하고 그렇지 않으면 false 를 반환
- 주로 `WHERE` 절에서 subquery 의 반환 값 존재 여부를 확인하는데 사용
	```sql
	-- EXISTS syntax
	SELECT
		select_list
	FROM
		table
	WHERE
		[NOT] EXISTS (subquery);
	```
## CASE
- SQL 문에서 조건문을 구성
- `case_value` 가 `when_value` 와 동일한 것을 찾을 때까지 순차적으로 비교
- `when_value` 와 동일한 `case_value` 를 찾으면 해당 `THEN` 절의 코드를 실행
- 동일한 값을 찾지 못하면 `ELSE` 절의 코드를 실행
	- `ELSE` 절이 없을 때 동일한 값을 찾지 못하면 오류 발생

	```sql
		-- CASE syntax
		CASE case_value
			WHEN when_value1 THEN statements
			WHEN when_value2 THEN statements
			...
			[ELSE else-statements]
		END CASE;
	```