# 컬렉션
## 딕셔너리 (Dictionary)
- 키-값 (key-value) 쌍으로 이루어진 모음(collection)
	- 키 (key)
		- 불변 자료형만 가능 (리스트, 딕셔너리 등은 불가능함)
	- 값 (values)
		- 어떠한 형태든 관계 없음
- 키와 값은 : 로 구분  
- 개별 요소는 , 로 구분
- 변경 가능하며 (mutable), 반복 가능함 (iterable)
	- 딕셔너리는 반복하면 키가 반환
		```python
		fruit = {'apple':500,'banana':1000}
		fruit['apple']
		# 500
		```
- 딕셔너리 (Dictionary) 키-값 추가 및 변경
	- 딕셔너리에 키와 값의 쌍을 추가할 수 있음
	- 이미 해당하는 키가 있다면 기존 값이 변경
		```python
		fruit = {'apple':500,'banana':1000}
		fruit['apple'] = 400
		# {'apple':400,'banana':1000}
		fruit['melon'] = 2000
		# {'apple':400, 'banana':1000, 'melon': 2000}
		```

- 딕셔너리 (Dictionary) 키- 값 삭제
	- 키를 삭제하고자하면 .pop()을 활용하여 삭제하고자 하는 키를 전달

		```python
		fruit = {'apple':500,'banana':1000}
		fruit.pop('apple')
		fruit
		# {'banana':1000}
		```
	- 키가 없는 경우는 KeyError 발생
		```python
		fruit = {'apple':500,'banana':1000}
		fruit.pop('melon')
		Traceback (most recent call last):
			File "<stdin>", line 1, in <module>
		KeyError: 'melon'
		```

- 딕셔너리 (Dictionary) 순회
	- 기본적으로 key를 순회하며, key를 통해 값을 활용
		```python
		fruit = {'apple' : 500, 'banana' : 1000}
			for A in fruit:
			print(A)
		# apple
		# banana
		```
		```python
		fruit = {'apple' : 500, 'banana' : 1000}
			for A in fruit:
			print(A,fruit[A])
		# apple 500
		# banana 1000
		```
	- 추가 메서드를 활용하여 순회할 수 있음
		- key() : Key로 구성된 결과
		- values() : value로 구성된 결과
		- items() : (Key, value)의 튜플로 구성된 결과
			```python
			fruit = {'apple' : 500, 'banana' : 1000}
			print(fruit.keys())
			print(fruit.values())
			print(fruit.items())
			# dict_keys(['apple','banana'])
			# dict_values([500, 1000])
			# dict_items(['apple',500),('banana',1000)])
			```
			```python
			fruit = {'apple' : 500, 'banana' : 1000}
			for A,B in fruit.items():
				print(A,B)
			# apple 500
			# bananan 1000
			```

