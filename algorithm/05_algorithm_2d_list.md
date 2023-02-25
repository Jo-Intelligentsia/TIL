# 이차원 리스트
- 리스트를 원소로 가지는 리스트
- 행렬(matrix)   
### 이차원 리스트 만들기
```python
	# for 문으로 작성 (100 x 100 행렬)
	matrix = []
	for _ in range(100):
		matrix.append([0]*100)
```
```python
	n = 4 # 행
	m = 3 # 열
	matrix = []
	for _ in range(n):
		matrix.append([0]*m)
	print(matrix)
	# [0,0,0],[0,0,0],[0,0,0],[0,0,0]]
```
```python
	n = 4 # 행
	m = 3 # 열
	martrix = [[0] * m for _ in range(n)]
	# n 행은 리스트내의 리스트 개수
	# m 열은 리스트내의 리스트 안에 인덱스 수
	print(matrix)
	# [0,0,0],[0,0,0],[0,0,0],[0,0,0]]
```

---
### 입력 받기
- 행렬의 크기가 미리 주어지는 경우
	```python
		matrix = []
		for _ in range(8): 
		# input 함수가 한 줄을 입력 받기 때문에 열의 크기는 사용 되지 않음
			line = list(input())
			matrix.append(line)
	```
	```python
		matrix = [list(input()) for _ in range(8)]
		# 리스트 컴프리핸션을 통해 이차원 리스트의 입력을 간단히 받을 수 있음
	```
	```python
		# 예제
		'''
		3 x 3 크기의 입력을 받아보자
		
		1 2 3
		4 5 6
		7 8 9
		'''
		# for 문
		matrix=[]
		for _ in range(3):
			line = list(map(int,input().split())
			matrix.append(line)
		# 리스트 컴프리핸션
		matrix = [list(map(int,input().split())) for _ in range(3)]
	```
- 행렬의 크기가 입력으로 주어지는 경우
	```python
		n,m = map(int,input().split()) # 8,7
		
		# for 문
		matrix = []
		for _ in range(n): # n 행 - 리스트내의 리스트 개수
			line = list(map(int,input().split()))
			matrix.append(line)
		
		# 리스트 컴프리핸션
		matrix = [list(map(int,input().split())) for _ in range(n)]
	```
	```python
		# 예제
		'''
		n x m 크기의 입력을 받아보자.
		3 4
		1 2 3 4
		5 6 7 8
		9 0 1 2
		'''
		n,m = map(int,input().split()) # 3 4
		
		# for 문
		matrix = []
		for _ in range(3):
			matrix.append(list(map(int,input().split()))

		# 리스트 컴프리핸션
		matrix = [list(map(int,input().split())) for _ in range(n)]
	```
---
### 순회
- 이중 for 문을 이용한 **행 우선 순회**
	```python
		matrix = [
			[1,2,3,4],
			[5,6,7,8],
			[9,0,1,2]
		]
		
		for i in range(3): # 3 = 행 리스트내의 리스트 개수
			for j in range(4): # 4 = 열 리스트내의 리스트 안의 인덱스 개수
				print(matrix[i][j], end =" ")
			print()
		# 1 2 3 4
		# 5 6 7 8
		# 9 0 1 2	
	```
- 이중 for 문을 이용한 **열 우선 순회**
	```python
		matrix = [
			[1,2,3,4],
			[5,6,7,8],
			[9,0,1,2]
		]
		
		for i in range(4): # 4 = 열 / 리스트내의 리스트 개수
			for j in range(3): # 3 = 행 / 리스트내의 리스트 안의 인덱스 개수
				print(matrix[j][i], end =" ")
			print()
		# 1 5 9
		# 2 6 0
		# 3 7 1
		# 4 8 2	
	```

- 행 우선 순회를 이용해 이차원 리스트의 총합 구하기
	```python
		matrix = [
			[1,1,1,1],
			[1,1,1,1],
			[1,1,1,1]
		]
		
		#방법 1
		total = 0

		for i in range(3):
			for j in range(4):
				total += matrix[i][j]
		print(total)
		# 12

		# 방법 2
		total = sum(map(sum,matrix))
		# 리스트내의 리스트 합을 구한후 리스트 합 구하기
		print(total)
		# 12
	```

- 행 우선 순회를 이용해 이차원 리스트의 최대값, 최소값 구하기
	```python
		matrix = [
			[0,5,3,1],
			[4,6,10,8],
			[9,-1,1,5]
		]
		
		# 방법 1
		max_value = 0
		min_value = 9999999

		for i in range(3):
			for j in range(4):
				if matrix[i][j] > max_value:
					max_value = matrix[i][j]
				elif matrix[i][j] < min_value:
					min_value = matrix[i][j]
		print(max_value,min_value)
		# 10 -1
		
		# 방법 2

		max_value = max(map(max, matrix))
		min_value = min(map(min, matrix))

		print(max_value,min_value)
		# 10 -1
	```
---
### 전치 (Transpose)
- 행렬의 행과 열을 서로 맞바꾸는 것을 의미
	```python
		matrix = [
			[1,2,3,4],
			[5,6,7,8],
			[9,0,1,2]
		]

		transposed_matrix = [[0] * 3 for _ in range(4)]

		for i in range(4): # 행 반복
			for j in range(3): # 열 반복
				transposed_matrix[i][j] = matrix[j][i]
				# 빈 리스트에 행, 열 바꿔서 대입

		'''
		transposed_matrix = [
			[1, 5, 9],
			[2, 6, 0],
			[3, 7, 1],
			[4, 8, 2]
		]	
		'''
	```
---
### 회전
- 왼쪽으로 90도 회전
```python
	matrix = [
		[1,2,3],		# [7,4,1]
		[4,5,6],		# [8,5,2]
		[7,8,9]			# [9,6,3]
	]

	n = 3	
	rotated_matrix=[[0] * n for _ in range(n)]
	# [0]으로 이루어진 빈 3 * 3 리스트 생성

	for i in range(n): # 세번 반복
		for j in range(n): # 세번 반복
			rotated_matrix[i][j] = matrix[j][n-i-1]
	# n-i-1 => n = 0 일때 
```

- 오른쪽으로 90도 회전
```python
	matrix = [
		[1,2,3],		# [3,6,9]
		[4,5,6],		# [2,5,8]
		[7,8,9]			# [1,4,7]
	]

	n = 3	
	rotated_matrix=[[0] * n for _ in range(n)]
	# [0]으로 이루어진 빈 3 * 3 리스트 생성

	for i in range(n): # 세번 반복
		for j in range(n): # 세번 반복
			rotated_matrix[i][j] = matrix[n-j-1][i]
	
```