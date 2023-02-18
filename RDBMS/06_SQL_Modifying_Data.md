# SQL - Modifying Data
- 학습 목표
	- `INSERT`, `UPDATE` 그리고 `DELETE statement`의 각 역할을 설명할 수 있다.
	- 주어진 예시에 맞추어 테이블에 새로운 정보를 쓰거나 기존 레코드를 수정 및 삭제 할 수 있다.

## Insert data into table
- `INSERT` statemaent
	- 테이블 레코드 삽입
	- `INSERT INTO` 절 다음에 테이블 이름과 괄호 안에 필드 목록을 작성
	- `VALUES` 키ㅣ워드 다음 괄호 안에 해당 필드에 삽입할 값 목록을 작성
	```sql
		-- INSERT syntax
		INSERT INTO table_name (c1, c2, ...)
		VALUES (v1, v2, ...)
	```
- `CURDATE()`
	- 현재 날짜를 반환
	- Date Functions 중 하나

## Update data in table
- `UPDATE`statement
	- 테이블 레코드 수정
	- `SET` 절 다음에 수정 할 필드와 새 값을 지정
	- `WHERE` 절에서 수정 할 레코드를 지정하는 조건 작성
		- `WHERE` 절을 작성하지 않으면 모든 레코드를 수정

	```sql
		-- UPDATE syntax
		UPDATE table_name
		SET column_name = expression,
		[WHERE
			condition];
	```
	- `REPLACE`
		- 지정된 문자열 변경
		- String Functions 중 하나

## Delete data from table
- `DELETE` statement
	- 테이블 레코드 삭제
	- `DELETE FROM` 절 다음에 테이블 이름 작성
	- `WHERE` 절에서 삭제할 레코드를 지정하는 조건 작성
		- `WHERE` 절을 작성하지 않으면 모든 레코드를 삭제

	```sql
		-- DELETE syntax
		DELETE FROM table_name
		[WHERE
			condition];
	```