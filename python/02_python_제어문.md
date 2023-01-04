# python 2

## fomat 함수
- format 이란?
    - 문자열 중간 중간에 특정 변수의 값을 넣어주기 위해 사용

- fotmat 함수 사용법
    1. print('{인덱스0}{인덱스1}'.format(값0,값1))
    2. print(f'{값0}{값1}')

    ```python
        a = 1 
        b = 2

        print('{0}는 {1}와 다르다.'.format(a,b))
            # 1는 2와 다르다.
        print(f'{a}는 {b}와 다르다.)
            # 1는 2와 다르다
    ```
---
## 자료형 변환 (Typecasting)
- 암시적 형 변환 (Implicit)
    - 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환 하는 경우
        - bool
        - Numeric type (int, float, complex)

        ```python
            True +3
            # 4
            3 + 5.0
            # 8.0
            3 + 4j + 5
            # (8+4j)
        ```
- 명시적 형 변환 (Explicit)
    - 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환 하는 경우
        - int
            - str*, float -> int
        - float
            - str* , int -> float
        - str
            - int, float, list, tuple, dict -> str
        - 형식에 맞는 문자열만 가능

        ```python
            '3 + 4
            # TypeError
            int('3') + 4
            # 7
            int('3.5) + 5
            # ValueError
            float('3.5) + 5
            # 8.5

        ```
---
## 레인지 (Range)
- 숫자이 시퀀스를 나태내기 위해 사용
    - 기본형 : range(n)
        - 0부터 n-1까지의 숫자의 시퀀스
    - 범위 지정 : range(n,m)
        - n부터 m-1까지의 숫자의 시퀀스
    - 범위 및 스텝 지정 : range(n,m,s)
        - n부터 m-1까지 s만큼 증가시키며 숫자의 시퀀스
- 변경 불가능하며, 반복 가능
    ```python
        range(4)
        # range(0, 4)
        list(range(4))
        # [0, 1, 2, 3]
        type(range(4))
        # <class 'range'>
    ```
    ```python
        # 0부터 특정 숫자까지
        list(range(3))
        # [0, 1, 2]

        # 숫자의 범위
        list(range(1, 5))
        # [1, 2, 3, 4]

        # step 활용
        list(range(1, 5, 2))
        # [1, 3]
    ```
    
    ```python
        # 역순
        list(range(6, 1, -1))
        # [6, 5, 4, 3, 2]

        list(range(6, 1, 1))
        # []
    ```
---
## 제어문 (Control Statement)
- 기본적으로 위에서부터 아래로 순차적으로 명령을 수행
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요함
- 제어문은 순서도(flow chart)로 표현이 가능

---
### 조건문 (Conditional Statement)
- 참/거짓을 판단할 수 있는 조건식과 함께 사용

- 기본형식 
    - expression 에는 참/거짓에 대한 조건식
        - 조건이 참인 경우 이후 들여쓰기 되어있는 코드 블럭을 실행
        - 이외의 경우 else 이후 들여쓰기 되어있는 코드 블럭을 실행
            - else 는 선택적으로 활용 가능

        ```python
            if expression:
                # Run this Code block
            else:
                # Run this Code block

        ```
        ```python
            num = int(input())
            if num % 2 == 1:
                print('홀')
            else:
                print('짝')

            # 입력값의 홀/짝 여부 출력
        ```
- 복수 조건문
    - 복수의 조건식을 활용할 경우 elif를 활용하여 표현

        ```python
            if expression:
                # Code block
            elif expression:
                # Code block
            elif ecpression:
                # Code block
            else:
                # Code block

        ```
- 중첩 조건문
    - 조건문은 다른 조건문에 중첩되어 사용될 수 있음
        - 들여쓰기를 유의하여 작성

        ```python
            if expression
                # Code block
                if expression
                    # Code block
            else:
                # Code block        
        ```
## 반복문 (Loop Statement)
- 특정 조건을 도달할 때까지, 계속 반복되는 일련의 문장
- 반복문의 종류
    - while 문
        - 종료조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
    - for 문
        - 반복가능한 객체를 모두 순회하면 종료 (별도의 종료조건이 필요 없음)
    - 반복 제어
        - break, continue, for-else

---

### while
- 조건식이 참인 경우 반복적으로 코드를 실행
    - 조건이 참인 경우 들여쓰기 되어 있는 코드 블록이 실행됨
    - 코드 블록이 모두 실행되고, 다시 조건식을 검사하며, 반복적으로 실행됨
    - 무한 루프를 하지 않도록 종료조건이 반드시 필요 
        - 무한 루프시 ctrl + c 로 탈출 가능
    ```python
        while expression:
            # Code block
    ```

    ```python
        # 예제
        # 1부터 사용자가 입력한 양의 정수까지의 총합을 구하시오.
        # 값 초기화
        n = 0
        total = 0
        A = int(input())

        while n <= A:
            total = total + n
            n = n + 1
        print(total)
    ```
---
### for
- 시퀀스(string, tuple, list, range)를 포함한 순회가능한 객체요소를 모두 순회함
    - 처음부터 끝까지 모두 순회하므로 별도의 종료조건이 필요하지 않음
    - 순회 가능한 객체 : 컨테이너형(string, tuple, list, range,dictionary)등

    ```python
        for 변수명 in iterable:
            # Code block
            
    ```

    ```python
        # 사용자가 입력한 문자를 한 글자씩 세로로 출력
        A = input() # hi 입력
        for B in A:
            print(B)
        # h
        # i
        # 출력
    ```
    ```python
        # 사용자가 입력한 문자를 range를 활용하여 한 글자씩 출력
        A = input() # hi 입력
        for B in range(len(A)):
            print(A[B])
        # h
        # i
        # 출력
    ```
---
### 반복문 제어
- break
    - 반복문 종료
        ```python
            n = 0
            while True:
                if n == 3:
                    break
                print(n)
                n = n + 1 # n += 1 로 표현 가능
            # 0
            # 1
            # 2 출력
        ```
        ```python
            for i in range(10):
                if i > 1:
                    print('0과 1만 필요해')
                    break
                print(i)
            # 0
            # 1
            # 0과 1만 필요해
        ```
- continue
    - continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행
        ```python
            for i in range(6):
                if i % 2 == 0:
                    continue
                print(i)
            # 1
            # 3
            # 5 출력
        ```
- for-else
    - 끝까지 반복문을 실행한 이후에 else문 실행
        - break를 통해 중간에 종료되는 경우 else 문은 실행되지 않음
        ```python
            for A in 'apple':
                if A == 'b':
                    print('b!')
                    break
            else:
                print('b가 없습니다.')
            # b가 없습니다. 출력
        ```
        ```python
            for A in 'banana':
                if A == 'b':
                    print('b!')
                    break
            else:
                print('b가 없습니다.')
            # b! 출력
        ```
