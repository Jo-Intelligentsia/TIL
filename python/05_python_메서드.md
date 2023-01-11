# 튜플 (Tuple)
## 튜플이란?
- 불변한 값들의 나열
- 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
- 변경 불가능, 반복 가능
- 소괄호 형태로 정의하며, 요소는 콤마로 구분
	- ex) (0, 1, 3)
---
## 생성과 접근
- 소괄호 혹은 tuple()을 통해 생성
- 값에 대한 접근은 리스트와 동일하게 인덱스로 접근
	- 값 변경은 불가능하여 추가/삭제도 불가능
	```python
		# 값 접근
		a = (1, 2, 3, 1)
		a[1]
		
		# 값 변경 -> 불가능
		a[1] = '3'

		TypeError Traceback (most recent call last)
		1 # 값 변경 -> 불가능 ---->
		2 a[1] = '3'
		TypeError: 'tuple' object does not support item assignment
	```
---
# 세트 (Set)
## 세트란?
- 유일한 값들의 모음
- 순서가 없고 중복된 값이 없음
	- 집합과 동일한 구조를 가지며, 집합 연산도 가능
- 변경 가능, 반복 가능
	- 단, 세트는 순서가 없어 반복의 결과가 정의한 순서와 다를수 있음
---
## 세트 생성
- 중괄호 혹은 set()을 통해 생성
	- 빈 Set을 만들기 위해서는 set()을 반드시 활용
- 순서가 없어 별도의 값에 접근할 수 없음
	```python
		{1, 2, 3, 1, 2}
		# {1, 2, 3}
	```
---
## 세트 추가/삭제
- 추가 - .add()를 활용
- 삭제 - .remove()를 활용
	```python
		# 세트 추가
		numbers = {1, 2, 3}
		numbers.add(5)
		numbers
		# -> {1, 2, 3, 5}
		numbers.add(1)
		numbers
		# -> {1, 2, 3, 5}
		
		# 세트 삭제
		numbers = {1, 2, 3}
		numbers.remove(1)
		numbers
		# -> {2, 3}
		numbers.remove(5)
		# Traceback (most recent call last):
		# File "<stdin>", line 1, in <module>
		# KeyError: 5
	```
---
## 세트 활용
- 세트를 활용하면 다른 컨테이너에서 중복된 값을 쉽게 제거할 수 있음
	- 단, 이후 순서가 무시되므로 순서가 중요한 경우 사용할 수 없음
	```python
		# 아래의 리스트에서 고유한 지역의 개수는?
		my_list = ['서울', '서울', '대전', '광주',
				   '서울', '대전', '부산', '부산']
		len(set(my_list))
		# 4
		set(my_list)
		# {'광주', '대전', '부산', '서울'}
	```
#### 세트 명령어
- .copy()
	-  세트의 얕은 복사본을 반환
- .add(x)
	- 항목 x가 세트에 없다면 추가
- .pop()
	- 세트에서 랜덤하게 항목을 반환하고, 해당 항목을 제거
	- 세트가 비어 있을 경우, KeyError
- .remove(x)
	- 항목 x를 세트에서 삭제
	- 항목이 존재하지 않을경우 , KeyError
- .discard(x)
	- 항목 x가 세트에 있는 경우, 항목 x를 세트에서 삭제
- .update(t)
	- 세트 t에 있는 모든 항목 중 기존세트에 없는 항목을 추가
- .clear()
	- 모든 항목을 제거
- .isdisjoint(t)
	- 세트가 세트 t의 서로 같은 항목을 하나라도 갖고 있지 않은 경우, True 반환
- .issubset(t)
	- 세트가 세트 t의 하위 세트인 경우 True반환
- .issuperset(t)
	- 세트가 세트 t의 상위 세트인 경우 True반환
---
# 메서드 (methods)
## 시퀀스
### 문자열
- 문자들의 나열
	- 모든 문자는 str 타입
- 문자열은 작은 따옴표나 큰따옴표를 활용하여 표기
	- 문자열을 묶을 때 동일한 문장부호를 활용
	- PE8에서는 소스코드 내에서 하나의 문장보호를 선택하여 유지하도록 함

#### 문자열 탐색
- .find(x)
	- x의 첫 번째 위치를 반환. 없으면, -1을 반환함.
		```python
			print('apple'.find('p'))
			# 1
			print('apple'.find('k'))
			# -1
		```
- .index(x)
	- x의 첫 번째 위치를 반환. 없으면, 오류 발생
		```python
			print('apple'.index('p'))
			# 1
			'apple'.index(k)
			# -------------------------------
			# ValueError Traceback (most recent call last)
			# ----> 1 'apple'.index('k')
			# ValueError: substring not found
		```
	
- .isalpha()
	- 알파벳 문자 여부
	- 단순 알파벳이 아닌 유니코드 상 Letter (한국어도 포함)
- .isupper() / .islower()
	- 대문자 여부 / 소문자 여부
- .istitle()
	- 타이틀 형식 여부
---
#### 문자열 변경
- .replace(old, new[,count])
	- 바꿀 대상 글자를 새로운 글자로 바꿔서 변환
	- count를 지정하면, 해당 개수만큼만 시행
		```python
		print('coone'.replace('o','a'))
		# caane
		print('wooooowoo'.replace('o','!',2))
		# w!!ooowoo
		```
- .split(sep=None, maxsplit=-1)
	- 문자열을 특정한 단위로 나눠 리스트로 반환
		- sep이 None이거나 지정되지 않으면 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음.
		- maxsplit이 -1인 경우에는 제한이 없음
			```python
			print('a,b,c'.split('_'))
			#['a,b,c']
			print('a,b,c'.split())
			#['a','b','c']
			```
- 'separator'.join([iterable])
	- 반복가능한 컨테이너 요소들을 구분자로 합쳐 문자열 반환 
		- iterable 에 문자열이 아닌 값이 있으면 TypeError 발생
			```python
			print('',joing(['3','5'])
			#35
			```

---
### 리스트 (List)
#### 리스트란?
- 변경 가능한 값들의 나열된 자료형
- 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
- 변경 가능, 반복 가능
- 대괄호 형태로 정의, 요소는 콤마로 구분
	- [0, 1, 2, 3, 4, 5, 6 ]

#### 리스트 값 추가 / 삭제
- .append(x)
	- 리스트에 값을 추가함
		```python
		cafe = ['starbucks', 'coffeebean', 'hollys']
		print(cafe)
		# ['starbucks', 'coffeebean', 'hollys']
		cafe.append('megacoffee')
		print(cafe)
		# ['starbucks', 'coffeebean', 'hollys', 'megacoffee']
		```
- .extend(iterable)
	- 리스트에 iterable의 항목을 추가함
		```python
		cafe = ['starbucks', 'coffeebean', 'hollys']
		print(cafe)
		# ['starbucks', 'coffeebean', 'hollys']
		cafe.extend(['cafe','test'])
		print(cafe)
		# ['starbucks', 'coffeebean', 'hollys', 'cafe', 'test']
		```
- .insert(i, x)
	- 정해진 위치 i에 값을 추가함
		```python
		cafe = ['starbucks', 'coffeebean']
		print(cafe)
		# ['starbucks', 'coffeebean']
		cafe.insert(0, 'start')
		print(cafe)
		# ['start', 'starbucks', 'coffeebean']
		```
- .remove(x)
	- 리스트에서 값이 x인 것 삭제
		```python
		numbers = [1, 2, 3, 'hi]
		print(numbers)
		# [1, 2, 3, 'hi']
		numbers.remove('hi')
		print(numbers)
		# [1, 2, 3]
		```
- .pop(i)
	- 정해진 위치 i에 있는 값을 삭제하고, 그 항목을 반환함
	- i가 지정되지 않으면, 마지막 항목을 삭제하고 반환함
		```python
		numbers = ['hi', 1, 2, 3]
		print(numbers)
		# ['hi', 1, 2, 3]
		pop_number = numbers.pop()
		pirnt(pop_number)
		# 3
		print(numbers)
		# ['hi', 1, 2]
		pop_number = numbers.pop(0)
		print(pop_number)
		# 'hi'
		print(numbers)
		# [1, 2]
		```
- .clear()
	- 모든 항목을 삭제함
		```python
		numbers = [1, 2, 3]
		print(numbers)
		# [1, 2, 3]
		print(numbers.clear())
		# []
		```
---
#### 탐색 및 정렬
- .index(x)
	- x 값을 찾아 해당 index 값을 반환
		```python
		numbers = [1, 2, 3, 4]
		print(numbers)
		# [1, 2, 3, 4]
		print(numbers.index(3))
		# 2
		```
- .count(x)
	- 원하는 값의 개수를 반환함
		```python
		numbers = [1, 2, 3, 1, 1]
		print(numbers.count(1))
		# 3
		print(numbers.count(100))
		# 0
		```
- .sort()
	- 원본 리스트를 정렬함 None 반환
	- sorted 함수와 비교
		```python
		numbers = [3, 2, 5, 1]
		result = numbers.sort()
		print(numbers, result)
		# [1, 2, 3, 5] None
		```
		```python
		numbers = [3, 2, 5, 1]
		result = sorted(numbers)
		print(numbers, result)
		# [3, 2, 5, 1] [1, 2, 3, 5]
		```
- .reverse()
	- 순서를 반대로 뒤집음(정렬하는 것이 아님) None 반환
		```python
		numbers = [3, 2, 5, 1]
		result = numbers.reverse()
		print(numbers,result)
		# [1, 5, 2, 3] None
		```
---
### 딕셔너리(Dictionary)
#### 딕셔너리란?
- 키, 값 쌍으로 이뤄진 모음
	- 키(key)
		- 불변 자료형만 가능 (리스트, 딕셔너리 등은 불가능함)
	- 값(values)
		- 어떠한 형태든 관계 없음
- 키와 값은 : 로 구분 , 개별요소는 , 로 구분
- 변경 가능, 반복 가능
	- 딕셔너리는 반복하면 키가 반환

#### 딕셔너리 메서드
- .clear() 
	- 모든 항목을 제거
- .keys()
	- 딕셔너리의 모든 키를 담은 뷰를 반환
		```python
		dict = {'홍길동' : 30, '각시탈' : 20}
		print(dict.keys())
		# dict.keys(['홍길동', '각시탈'])
		```
- .values()
	- 딕셔너리의 모든 값을 담은 뷰를 반환
		```python
		dict = {'홍길동' : 30, '각시탈' : 20}
		print(dict.values())
		# dict.values([30, 20]
		```
- .items()
	- 딕셔너리의 모든 키,값의 쌍을 담은 뷰를 반환
		```python
		dict = {'홍길동' : 30, '각시탈' : 20}
		print(dict.items())
		# dict.items([('홍길동', 30),('각시탈', 20)])
		```
- . get(key[,default])
	- key를 통해 value를 가져옴
	- KeyError가 발생하지 않으며, default 값을 설정할 수 있음 (기본 : None)
		```python
		dict = {'홍길동' : 30, '각시탈' : 20}
		print(dict.get('임꺽정'))
		# None
		print(dict.get('홍길동'))
		# 30
		print(dict.get('임꺽정', 10))
		# 10
		```
- .pop(key[,default]
	- key가 딕셔너리에 있으면 제거하고 해당 값을 반환
	- 그렇지 않으면 default를 반환
	- default값이 없으면 KeyError
		```python
		dict = {'홍길동' : 30, '각시탈' : 20}
		data = dict.pop('홍길동')
		print(data, dict)
		# 30 {'각시탈' : 20}
		```
- .update([other])
	- 값을 제공하는 key, value로 덮어씀
		```python
		dict = {'홍길동' : 0, '각시탈' : 20}
		dict.update(홍길동=30)
		print(dict)
		# {'홍길동': 30, '각시탈' : 20}
		```

