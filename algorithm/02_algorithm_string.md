# 문자열 (String)
### 문자열 조작
---

- 문자열 슬라이싱

| |a|b|c|d|e|f|g|h|i|
|-|-|-|-|-|-|-|-|-|-|
|index|0|1|2|3|4|5|6|7|8|
|index|-9|-8|-7|-6|-5|-4|-3|-2|-1|
```python
	s = 'abcdefghi'
	s[2:5] # 'cde'	인덱스 2 부터 5 전 까지
	s[-6:-2] # 'defg' 인덱스 -6 부터 -2 전 까지
	s[2:5:2] # 'ce' 인덱스 2 부터 5전 까지 2칸 띄우기
	s[-6:-1:3] # 'dg' 인덱스 -6 부터 -1 전까지 3칸 띄우기
	s[:3] # 'abc' 처음부터 인덱스 3 전 까지
	s[5:] # 'fghi' 인덱스 5부터 끝까지
	s[:] # 'abcdefghi' 모두 출력
	s[::-1] # 'ihgfedcba' 거꾸로 모두 출력
```
---
### 문자열 메서드
---
- `.split(기준문자)`
	- 문자열을 일정 기준으로 나누어 리스트로 반환
	- 괄호 안에 아무것도 넣지 않으면 자동으로 공백을 기준으로 설정
	```python
		word = "I play the piano"
		print(word.split())
		# ['I','play','the','piano']

		word = 'apple,banana,orange,grape'
		print(word.split(',')
		# ['apple','banana','orange','grape']
	```
- `.strip(제거할 문자)`
	- 문자열의 양쪽 끝에 있는 특정 문자를 모두 제거한 새로운 문자열 반환
	- 괄호 안에 아무것도 넣지 않으면 자동으로 공백을 제거 문자로 설정
	- 제거할 문자를 여러 개 넣으면 해당하는 모든 문자들을 제거
	```python
		word = ' Hello World '
		print(word.strip())
		# Hello World

		word = 'aHello Worlda'
		print(word.strip('a'))
		# Hello World

		word = 'Hello Wordl'
		print(word.strip('Hd'))
		# ello Worl

		word = 'Hello Worlddddd'
		print(word.strip('d'))
		Hello Worl
	```
- `.find(찾는 문자)`
	- 특정 문자가 처음으로 나타나는 인덱스를 반환
	- 찾는 문자가 없다면 -1을 반환
	```python
		word = 'apple'
		print(word.find('p'))
		# 1

		word = 'apple'
		print(word.find('k'))
		# -1
	```
- `.index(찾는 문자)`
	- 특정 문자가 처음으로 나타나는 인덱스를 반환
	- 찾는 문자가 없다면 오류 발생
	```python
		word = 'apple'
		print(word.index('p'))
		# 1

		word = 'apple'
		print(word.index('k'))
		# Error
	```
- `.count(개수를 셀 문자)`
	- 문자열에서 특정 문자가 몇 개인지 반환
	- 문자 뿐만 아니라, 문자열의 개수도 확인 가능
	```python
		word = 'banana'
		print(word.count('a'))
		# 3

		word = 'banana'
		print(word.count('na'))
		# 2

		word = 'banana'
		print(word.count('ana'))
		# 1
		
	```
- `.replace(기존 문자, 새로운 문자)`
	- 문자열에서 기존 문자를 새로운 문자로 수정한 새로운 문자열 반환
	- 특정 문자를 빈 문자열('')로 수정하여 마치 해당 문자를 삭제한 것 같은 효과 가능
	```python
		word = 'happyhacking'
		print(word.replace('happy','angry'))
		# angryhacking

		word = 'happyhacking'
		print(word.replace('h','H'))
		# HappyHacking

		word = 'happyhacking'
		print(word.replace('happy',''))
		# hacking
	```
- `삽입할 문자.join(iterable)`
	- iterable 의 각각 원소 사이에 특정 문자를 삽입한 새로운 문자열 반환
	- 공백 출력, 콤마 출력 등 원하는 출력 형태를 위해 사용
	```python
		word = 'happyhacking'
		print(' '.join(word))
		# h a p p y h a c k i n g

		word = 'happyhacking'
		print(','.join(word))
		# h,a,p,p,y,h,a,c,k,i,n,g

		word = ['edu', 'hphk.kr']
		print('@'.join(word))
		# edu@hphk.kr

		words = ['h','a','p','p','y']
		print(''.join(words))
		# happy
	```

---
### 아스키 코드 (ASCII Code)
- 미국 정보교환 표준부호
	- American Standard Code for Information Interchange
- 알파벳을 표현하는 대표 인코딩 방식
- 각 문자를 표현하는데 1byte(8bits) 사용
	- 1bit : 통신 에러 검출용
	- 7bit : 문자 정보 저장 (총 128개)
- ord(문자)
	- 문자 -> 아스키코드로 변환하는 내장함수
	```python
		print(ord('A'))
		# 65

		print(ord('a'))
		# 97
	```

- chr(아스키코드)
	- 아스키코드 -> 문자로 변환하는 내장함수
	```python
		print(chr(65))
		# A

		print(chr(97))
		# a	
	```