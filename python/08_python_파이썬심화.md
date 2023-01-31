# 파이썬 심화
## 클래스
- 클래스 속성 (attribute)
	- 한 클래스의 모든 인스턴스라도 똑같은 값을 가지고 있는 속성
	- 클래스 선언 내부에서 정의
	- `<classname>.<name>`으로 접근 및 할당
	```python
		class Circle:
			pi = 3.14 
		c1 = Circle()
		c2 = Circle()
		print(Circle.pi)
		print(c1.pi)
		print(c2.pi)
		# 3.14
		# 3.14
		# 3.14
	```
- 클래스 메서드
	- @classmethod 데코레이터를 사용하여 정의 
		- 데코레이터 : 함수를 어떤 함수로 꾸며서 새로운 기능을 부여
	- 호출 시, 첫번째 인자로 클래스(cls)가 전달됨
	```python
		class MyClass

			@classmethod
			def class_method(cls,arg1, ...)
	```

- 스태틱 메서드

	- 인스턴스나 클래스를 사용하지 않는 메서드
	- @staticmethod 데코레이터를 사용하여 정의
	- 호출 시, 어떠한 인자도 전달되지 않음 (클래스 및 인스턴스 정보에 접근/수정 불가)

	```python
		class MyClass

			@staticmethod
			def class_method(arg1, ...)
	```

- 메서드 정리
	- 인스턴스나 클래스를 활용하거나 조작하지 않는 경우
		- 스태틱 메서드로 정의
		- 전달되는 인자는 없음
	- 인스턴스를 활용하거나 조작하는 경우
		- 인스턴스 메서드로 정의하고, 첫번째 인자로 전달된 인스턴스를 조작(일반적으로 self)
	- 클래스를 활용하거나 조작하는 경우
		- 클래스 메서드로 정의
		- 첫번째 인자로 전달된 클래스를 조작 (일반적으로 cls)

---
## 상속
- 상속
	- 두 클래스 사이 부모 - 자식 관계를 정립하는 것
	- 부모에 정의된 속성이나 메서드를 활용하거나 오버라이딩(재정의)를 하여 활용
		- 코드의 재사용성을 높이고 클래스 간의 계층적 관계를 활용함
- 다중 상속
	- 두개 이상의 클래스를 상속 받을수 있음
	- 상속 받은 모든 클래스의 요소를 활용 가능함
	- 중복된 속성이나 메서드가 있는 경우 상속 순서에 의해 결정


---
## 추가 문법
- 조건 표현식
	- 조건 표현식을 일반적으로 조건에 따라 값을 할당 할 때 사용
	```python
		<True인 경우 값> if <expression> else <False 인 경우 값>
	```

- enumerate()
	- 인덱스와 객체를 쌍으로 담은 열거형 객체 반환
		- (index,value) 형태의 tuple로 구성된 열거 객체를 반환

		```python
			# 예시
			members = ['민수','영희','철수']
			
			for i in range(len(members)):
				print(f'{i} {members[i]}')
			
			for i, member in enumerate(members):
				print(i,member)

			enumerate(members)
			# <enumerate at 0x105d3e100>
			list(enumerate(members))
			# [(0,'민수'),(1,'영희),(2,'철수')]
			list(enumerate(members, start = 1))
			# [(1,'민수'),(2,'영희),(3,'철수')]
		```

- List comprehension
	- 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법
	```python
		[값 for x in range()]
		[값 for x in range() if 조건식]
	```
	
	```python
		{key: value for 변수 in range()}
		{key: value for 변수 in range() if 조건식}
	```
- lambda [parameter] 표현식
	- 표현식을 계산한 결과값을 반환하는 함수
	- 이름없는 함수여서 익명함수로 불림
	- 특징
		- return 문을 가질 수 없음
		- 간편 조건문 외 조건문이나 반복문을 가질 수 없음
	- 장점
		- 함수를 정의해서 사용하는 것보다 간결하게 사용 가능
		- def 를 사용할 수 없는 곳에서도 사용가능