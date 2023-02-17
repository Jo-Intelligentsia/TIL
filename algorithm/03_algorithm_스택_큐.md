# 스택 (Stack)
### 스택이란?
- 데이터를 한쪽에서만 넣고 빼는 자료구조

- LIFO(Last-in First-out, 후입선출)
---
### 스택의 사용
- 뒤집기
- 되돌리기
- 되돌아가기
---
### Stack 함수

-   `empty()`
	-  스택이 비었는지 참/거짓을 반환
-   `size()`
	-  스택의 사이즈, 크기를 반환
-   `push(a)`
	- `a`를 스택의 마지막에 삽입
-   `pop()`
	-  스택의 마지막 요소(Last in)을 반환하고 제거  
- 모두 시간 복잡도(Time Complexity)  O(1)
---
### Stack 구현하기
-   List
-   Collections.deque
-   queue.LifoQueue
---
#### List
- 리스트로 스택 구현 가능
- push() -> append()  로 대체
- 속도 문제 발생
	```python
		stack = []

		stack.append('a')
		# ['a']
		stack.append('b')
		# ['a','b']
		stack.append('c')
		# ['a','b','c']

		stack.pop()
		# ['a','b']
		stack.pop()
		# ['a']
		stack.pop()
		# []
	```
---
#### collections.deque
- collections 모듈의 deque 클래스를 이용하여 스택 사용가능
- list 보다 더 빠른 연산이 필요할 때 사용
- deque `append()`, `pop()` 시간복잡도 O(1)  
- list `append()`, `pop()`시간복잡도 O(n)

```python
	from collections import deque
	stack = deque()
	# collections 모듈로 스택 생성
```
---
# 큐 (Queue)
### 큐 란?
- 한 쪽 끝에서 데이터를 넣고, 다른 한 쪽에서만 데이터를 뺄수 있는 구조
- FIFO (First-in First-out, 선입선출)x