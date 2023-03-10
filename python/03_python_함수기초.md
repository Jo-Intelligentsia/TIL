# 함수 (function)

## 함수란?
- 특정한 기능을 하는 코드의 조각(묶음)
- 특정 명령을 수행하는 코드를 매번 다시 작성하지 않고, 필요 시에만 호출하여 간편히 사용
- 사용자 함수(Custom Function)
    - 구현되어 있는 함수가 없는 경우, 사용자가 직접 함수를 작성 가능

---
## 함수 기본 구조
- 선언과 호출 (define & call)
- 입력 (Input)
- 범위 (Scope)
- 결과값 (Output)

---
## 내장 함수
- print(*objects, sep=' ', end='\n')
    - 출력 함수
- len(s)
    - 객체의 길이를 반환
    - 인자는 시퀀스 또는 컬렉션일 수 있음
- sum(iterable, start = 0)
    - start 및 iterable 의 항목들을 왼쪽에서 오른쪽으로 합하고 합계를 돌려줌
    - iterable 의 항목은 일반적으로 숫자며 시작 값은 문자열이 될 수 없음
- max (iterable)
    - iterable에서 가장 큰 항목이나 두 개 이상의 인자 중 가장 큰 것을 반환
    - 여러 항목이 최댓값이면 함수는 처음 만난 항목을 반환
- min (iterable)
    - iterable에서 가장 작은 항목이나 두 개 이상의 인자 중 가장 작은 것을 반환
    - 여러 항목이 최솟값 함수는 처음 만난 항목을 반환
- abs(a)
    - 숫자의 절댓값을 반환
    - 인자는 정수, 실수 또는 `_abs_()`를 구현하는 객체
    - 인자가 복소수면 그 크기를 반환
- divmod(a,b)
    - 두 수를 받아 몫과 나머지를 반환
- pow(base, exp, mod=None)
    - base의 exp 거듭제곱을 반환
    - mod가 있는 경우, base의 exp 거듭제곱의 모듈로 mod를 반환
- round(number, ndigit=None)
    - number 를 소수점 다음에 ndigits 정밀도로 반올림한 값을 반환
    - ndigits 가 생략되거나 None 이면, 입력에 가장 가까운 정수를 반환

---
## 논리 관련 함수
- all (iterable)
    - iterable의 모든 요소가 참이면(또는 비어있으면) True를 반환
- any (iterable)
    - iterable 의 요소 중 어느 하나라도 참이면 True를 반환
    - 비어있으면 False를 돌려줌
---
## 기타 함수
- bin(x)
    - 정수를 '0b' 접두사가 붙은 2진수 문자열로 반환
- hex(x)
    - 정수를 '0x' 접두사가 붙은 16진수 문자열로 반환
- oct(x)
    - 정수를 '0o' 접두사가 붙은 8진수 문자열로 반환
- ord(c)
    - 유티코드 문자 c에 대응되는 유니코드 숫자로 반환
- chr(i)
    - 유니코드 숫자가 정수 i에 대응되는 문자를 반환

---
## map
- 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function) 적용
- 그 결과를 map object로 반환
- 알고리즘 문제 풀이시 input 값들을 숫자로 바로 활용하고 싶을 때