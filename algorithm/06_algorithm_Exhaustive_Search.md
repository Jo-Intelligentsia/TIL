# 완전탐색 (Exhaustive Search)
### 브루트 포스(Brute-force)
---
- 모든 경우의 수를 탐색하여 문제를 해결하는 방식
	- 무식하게 밀어붙인다는 뜻
	- 가장 단순한 풀이 기법
	- 단순 조건문과 반복문을 이용해서 풀 수 있음
	- 복잡한 알고리즘 보다는, 아이디어를 어떻게 코드로 구현할 것인지가 중요함

---
### 델타 탐색 (Delta Search)
---
- 상하좌우 탐색
- 각 지점에서 상하좌우에 위치한 다른 지점을 조회하거나 이동하는 방식
- 이차원 리스트의 인덱스를 조작
	- 행과 열의 변량인 -1,+1을 델타 값이라고 함
	```python
		# 행을 x, 열을 y로 표현
		dx = [-1,1,0,0]
		dy = [0,0,-1,1]
		#    상 하 좌 우
		# 행을 r, 열을 c로 표현
		dr = [-1,1,0,0]
		dc = [0,0,-1,1]
	
	```
	```python
		# 상(x-1,y)
		nx = x + dx[0]
		ny = y + dy[0]
		# 하(x+1,y)
		nx = x + dx[1]
		ny = y + dy[1]
		# 좌(x,y-1)
		nx = x + dx[2]
		ny = y + dy[2]
		# 상(x,y+1)
		nx = x + dx[3]
		ny = y + dy[3]
	```
	```python
		# 상하좌우
		for i range(4):
			nx = x + dx[i]
			ny = y + dy[i]

			# 범위를 벗어나지 않으면 갱신
			if 0 <= nx < 3 and 0 <= ny <3:
				x = nx
				y = ny
	```
	```python
		# 델타값 정의(상하좌우)
		dx = [-1,1,0,0]
		dy = [0,0,-1,1]

		# 이차원 리스트 순회
		for x in range(n):
			for y in range(m):

			# 델타값을 이용해 상하좌우 이동
			for i in range(4):
			nx = x + dx[i]
			ny = y + dy[i]

			# 범위를 벗어나지 않으면 갱신
			if 0 <= nx < n and 0 <= ny <m:
				x = nx
				y = ny
	```