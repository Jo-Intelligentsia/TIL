# Python

## Python 이란?

- 애플리케이션, 소프트웨어 개발, 데이터 과학, 기계 학습(ML)에 널리 사용되는 프로그래밍 언어 
- 효율적이고 배우기 쉬우며 여러 플랫폼에서 실행 가능
- 모든 유형의 시스템과 원활하게 통합되며, 개발 속도를 증가
---
## Python 역사
- 네덜란드의 컴퓨터 프로그래머인 `Guido Van Rossum` 가 1989년 네덜란드 국립 수학 정보과학 연구소(CWI)에서 취미 프로젝트로서 Python 개발을 시작
- 즐겨 시청하던 BBC의 TV 드라마인 Monty Python’s Flying Circus에서 이름을 따옴 
- `Python`의 출시 이력
    - 1991년 `Python 코드의 첫 번째 버전(버전 0.9.0)`을 발표
        - 일부 데이터 유형 및 오류 처리 함수와 같은 좋은 기능이 이미 포함 
    - 1994년 `Python 1.0 버전` 출시
        - map, filter, reduce와 같은 데이터 목록을 쉽게 처리할 수 있는 기능 함수 포함
    - 2000년 10월 16일 `Python 2.0 버전` 출시
        - 유니코드 문자 지원 및 목록을 루프 처리하는 더 간단한 방법과 같이 프로그래머를 위한 새로운 유용한 기능이 포함
    - 2008년 12월 3일 `Python 3.0 버전` 출시
        - print 함수와 숫자 나누기/오류 처리에 대한 추가 지원 등의 기능이 포함
---
## Python 특징
- 해석된 언어
    - 코드를 한 줄씩 직접 실행
    - 프로그램 코드에 오류가 있으면 실행이 중지 
    - 이로인해 프로그래머는 코드에서 오류를 빠르게 찾을 수 있음

- 사용하기 쉬운 언어
    - 영어와 유사한 단어를 사용
    - 다른 프로그래밍 언어와 달리 Python은 중괄호를 사용하지 않고 들여쓰기를 사용 

- 동적으로 유형이 결정되는 언어
    - 런타임에 변수 유형을 결정하기 때문에 프로그래머는 코드를 작성할 때 변수 유형을 선언할 필요가 없음
    - 이로인해 Python 프로그램을 더 빨리 작성할 수 있음

- 고급 언어
    - 다른 프로그래밍 언어보다 인간 언어에 더 가까움
    - 이로인해 프로그래머는 아키텍처 및 메모리 관리와 같은 기본 기능에 대해 걱정할 필요가 없음

- 객체 지향 언어
    - 모든 것을 `객체`로 간주하지만, 구조적 및 함수형 프로그래밍 등의 다른 프로그래밍 유형도 지원
        - 객체 : (숫자, 문자, 클래스 등 값을 가지고 있는 모든것)
---
## Python의 이점
- 기본적이고 영어와 유사한 구문을 가지고 있기 때문에 개발자가 쉽게 읽고 이해 가능 
- 다른 많은 언어에 비해 더 적은 코드 줄을 사용하여 Python 프로그램을 작성할 수 있기 때문에 개발자의 생산성을 높임
- 거의 모든 작업에 재사용 가능한 코드가 포함된 대규모 표준 라이브러리가 있어, 코드를 처음부터 작성할 필요가 없음
- 개발자는 Java, C 및 C++ 등의 다른 인기 있는 프로그래밍 언어와 함께 Python을 쉽게 사용할 수 있습니다.
- Windows, macOS, Linux 및 Unix와 같은 다양한 컴퓨터 운영 체제에서 호환 가능
---

## 변수 (Variable)
- 변수란 ?
    - 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름
    - 동일 이름에 다른 객체를 언제든 할당할 수 있음
- 할당 연산자 (=) 를 통해 값을 할당 (assignment) 
    - type()
        - 변수에 할당된 값의 타입
    - id()
        - 변수에 할당된 값(객체)의 고유한 아이덴티티(identity) 값이며, 메모리주소
    - 같은 값을 동시에 할당할 수 있음
    - 다른 값을 동시에 할당할 수 있음(multiple assignment)
---
## 식별자 (Identifiers)

- 파이썬 객체(변수, 함수, 모듈, 클래스 등)를 식별하는데 사용하는 이름 (name)
- 규칙
    - 식별자의 이름은 영문 알파벳, 언더스코어(_), 숫자로 구성
    - 첫 글자에 숫자가 올 수 없음
    - 길이제한이 없고, 대소문자를 구별
    - 다음의 키워드는 예약어로 사용할 수 없음

      >  - False, None, True, and, as, assert, async, await, break, class, continue, def, del elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
    - 내장함수나 모듈 등의 이름으로도 만들 수 없음

---
## 자료형 (Data Type)
- 숫자
    - 수치형 (Numeric Type)
        - int (정수, integer)
            - 모든 정수의 타입
            - `오버플로우`가 발생하지 않음
                - 오버플로우 (overflow) : 데이터 타입별로 사용할 수 있는 메모리의 크기를 넘어서는 상황
        - float (부동소수점, 실수, floating point number)
            - 정수가 아닌 모든 실수
            - `부동소수점`
                - 실수를 컴퓨터가 표현하는 방법
                - 실수 연산 과정에서 발생 가능 한 예

                    ```python
                        # 아래는 참일까? 거짓일까?
                        3.14 - 3.02 == 0.12

                        3.14 - 3.02 
                        # 0.1200000000000001
                    ```
                - 매우 작은 수보다 작은지를 확인하거나 math 모듈 활용
        - complex (복소수, complex number)
            - 실수부와 허수부로 구성
                - 허수부를 j로 표현
                
                    ```python
                        a = 3+4j
                        type(a)
                        # <class 'complex'>
                        a.real
                        # 3.0
                        a.imag
                        # 4.0
                    ```
    - 불린형 (Boolean Type)
        - True / False 값을 가진 타입
            - True 는 1, False 는 0 에 해당함
        - 비교/논리 연산을 수행함에 있어서 활용
        - 모두 False 로 변환
            - 0, 0.0, (), [], {}, ", None

- 시퀀스 (Sequence)
    - 문자열 (String)
    - 튜플 (Tuple)
    - 리스트 (List)
    - 레인지 (Range)
- 컬렉션 (Collection)
    - 집합 (Set)
    - 딕셔너리 (Dictionary)
- None
---
## 연산자 (Operator)
- 산술 연산자 (Arithmetic Operator)
    - 사칙연산 및 수식
    
    | 연산자 | 내용 |
    |:-:|:-:|
    |+|덧셈|
    |-|뺄셈|
    |*|곱셈|
    |%|나머지|
    |/|나눗셈|
    |//|몫|
    |**|거듭제곱|

- 복합 연산자 (In-place Operator)
    - 연산과 할당이 함께 이뤄짐
    
    | 연산자 | 내용 |
    |:-:|:-:|
    | a += b | a = a + b |
    | a -= b | a = a - b |
    | a *= b | a = a * b |
    | a /= b | a = a / b |
    | a //= b | a = a // b |
    | a %= b | a = a % b |
    | a **= b | a = a ** b |

- 비교 연산자 (Comparison Operator)
    - 값을 비교하며, True / False 값을 리턴함

    | 연산자 | 내용 |
    |:-:|:-:|
    | < | 미만 |
    | <= | 이하 |
    | > | 초과 |
    | >= | 이상 |
    | == | 같음 |
    | != | 같지않음 |
    | is | 객체 아이덴티티(OOP) |
    | is not | 객체 아이덴티티가 아닌 경우 |

- 논리 연산자 (Logical Operator)
    - 논리식을 판단하여 참(True)와 거짓(False)를 반환함

    | 연산자 | 내용 |
    |:-:|:-:|
    | A and B | A와 B 모두 True시, True |
    | A or B | A와 B 모두 False 시 False |
    | Not | True를 False로, False를 True로 |
    
    - and
        - 모두 True인 경우 True, 그렇지 않으면 False

        | 논리연산자 and | 내용 |
        |:-:|:-:|
        | True and True | True |
        | True and False | False |
        | False and True | False |
        | False and False | False |
    
    - or
        - 둘 중 하나만 True이라도 True, 그렇지 않으면 False

        | 논리연산자 or | 내용 |
        |:-:|:-:|
        | True or True | True |
        | True or False | True |
        | False or True | True |
        | False or False | False |
    
    - not 
        - True , False 의 반대의 결과

        | 논리연산자 not | 내용 |
        |:-:|:-:|
        | not True | False |
        | not False | True |

## 컨테이너 (Container)
- 컨테이너란?
    - 여러 개의 값을 담을 수 있는 것 (객체)

- 분류
    - 시퀀스 (Sequence Container)
        - 문자열 (immutable): 문자들의 나열
        - 리스트 (mutable) : 변경 가능한 값들의 나열
        - 튜플 (immutable) : 변경 불가능한 값들의 나열
        - 레인지 (immutable) : 숫자의 나열
    - 컬렉션 / 비시퀀스
        - 세트 (mutable) : 유일한 값들의 모음
        - 딕셔너리 (mutable) : 키 - 값들의 모음

- 시퀀스형 컨테이너 (Sequence Container)
    - 시퀀스형 주요 공통 연산자
        | 연산 | 결과 |
        |:-:|:-:|
        | s[i] | s 의 i 번째 항목, 0부터 시작 |
        | s[i:j] | s 의 i 에서 j 까지의 슬라이스 |
        | s[i:j:k] | s 의 i 에서 j 까지 스텝 k 의 슬라이스 |
        | s + t | s 와 t 의 이어 붙이기 |
        | s * n 또는 n * s | s 를 그 자신에 n 번 더하는 것 |
        | x not in s | s 의 항목 중 하나가 x 와 같으면 False, 그렇지 않으면 True |
        | len(s) | s 의 길이 |
        | min(s) | s 의 가장 작은 항목 |
        | max(s) | s 의 가장 큰 항목 |

- 문자열 (String Type)
    - 모든 문자는 str 타입
    - 문자열은 작은 따옴표(')나 큰 따옴표(")를 활용하여 표기
        - 문자열을 묶을 때 동일한 문장부호를 활용
        - PEP8 에서는 소스코드 내에서 하나의 문장부호를 선택하여 유지하도록 함

    - 중첩따옴표 (Nested Quotes)
        - 따옴표 안에 따옴표를 표현할 경우
            ```python
                print("문자열 안에 '작은 따옴표'가 들어있는 경우")
                print('문자열 안에 "큰 따옴표"가 들어있는 경우')
            ```
    - 삼중따옴표 (Triple Quotes)
        - 작은 따옴표나 큰 따옴표를 삼중으로 사용
            - 따옴표 안에 따옴표를 넣을 때
            - 여러줄을 나눠 입력할 때 편리
                ```python
                    print('''문자열 안에 '작은 따옴표'나 "큰 따옴표"를 사용할 수 있고 
                    여러 줄을 나눠 입력할 때도 편하다''')
                ```

    - 인덱싱
        - 인덱스를 통해 특정 값에 접근할 수 있음

        | | a | b | c | d | e|
        |-| -|-|-|-|-|
        |index|0|1|2|3|4|

        - s[1] => 'b'

    - 슬라이싱
        - 특정 범위의 인덱스 값을 구할수 있음
        - s[a:b] => a이상 b미만
        | | a | b | c | d | e|
        |-| -|-|-|-|-|
        |index|0|1|2|3|4|

        -s[2:4] => 'cd'
    
    - 결합 (Concatenation)
        ```python
            'hello, ' + 'python!'
            # 'hello, python!'
        ```
    - 반복 (Repetition)
        ```python
            'hi!' * 3
            # 'hi!hi!hi!'
        ```        
    - 포함 (Membership)
        ```python
            'a' in 'apple'
            # True
            'app' in 'apple'
            # True
            'b' in 'apple'
            # False
        ```

    - 이스케이프 시퀀스 (Escape sequence)
        - 문자열 내에서 특정 문자나 조작을 위해서 역슬래시(\)를 활용하여 구분

        |예약문자|내용(의미)|
        |-|-|
        |\n|줄바꿈|
        |\t|탭|
        |\r|캐리지리턴|
        |\\|\|
        |\'|단일인용부호(')|
        |\''|이중인용부호('')|
            ```python
                print('철수 \'안녕\'')
                # 철수 '안녕'
                print('이 다음은 엔터.\n그리고 탭\t탭')
                # 이 다음은 엔터.
                # 그리고 탭   탭
            ```

- 리스트 (List)
    - 변경 가능한 값들의 나열된 자료형
    - 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
    - 변경 가능하며(mutable), 반복 가능함(iterable)
    - 항상 대괄호 형태로 정의하며, 요소는 콤마로 구분
    - 대괄호([]) 혹은 list() 를 통해 생성
    - 순서가 있는 시퀀스로 인덱스를 통해 접근 가능

        - 리스트 생성

            ```python
                # 생성
                my_list = []
                another_list = list()
                type(my_list)
                # <class 'list'>
                type(another_list)
                # <class 'list'>
            ```
        - 리스트 접근과 변경
            ```python
                # 값 접근
                a = [1, 2, 3]
                print(a[0])
                # 1

                # 값 변경
                a[0] = '1'
                print(a)
                # ['1', 2, 3]
            ```
        - 리스트 값 추가/삭제

            - 값 추가 .append() 활용 (맨 뒤 인덱스로 추가)
            - 값 삭제 .pop() 활용

            ```python
                # 값 추가
                numbers = [2, 4, 6, 8]
                numbers.append(10)
                print(numbers)
                # [2, 4, 6, 8, 10]
                
                # 값 삭제
                numbers = [2, 4, 6, 8]
                numbers.pop(0)
                print(numbers)
                # [4, 6, 8]
            ```

        - 예제

            ```python
                city = ['seoul', 'busan']

                len(city)
                # 2
                city[1]
                # 'busan'
                city[1][0]
                # 'b'

            ```
- None
    - 파이썬 자료형 중 하나
    - 값이 없음을 표현하기 위해 None 타입이 존재
    - 일반적으로 반환 값이 없는 함수에서 사용하기도 함

        ```python
            print(type(None))
            # <class 'NoneType'>
            a = None
            print(a)
            # None
        ```

- 주석 (Comment)
 - 코드에 대한 설명 
    - 중요한 점이나 다시 확인하여야 하는 부분을 표시
    - 컴퓨터는 주석을 인식하지 않음 사용자만을 위한 것
- 주석으로 처리될 내용 앞에 '#'을 입력
    - 한 줄을 온전히 사용할 수도 있고, 그 줄 코드 뒷부분에 작성 할 수 있음
    - VS Code에서는 단축기(ctrl+/)를 활용하여 주석 처리를 할 수 있음

        ```python
            # 주석(comment) 입니다.

            #print('hello')
            print('world') # 주석
        ```

- 사용자 입출력
    - input([prompt])
        - 사용자로부터 값을 즉시 입력 받을 수 있는 내장함수
            - 대괄호 부분에 문자열을 넣으면 입력 시, 해당 문자열을 출력할 수 있음
        - **반환값은 항상 문자열의 형태로 반환**

            ```python
                name = input('이름을 입력해주세요 : ')
                print(name)
                # 이름을 입력해주세요 : 
                type(name)
                # str
            ```

    - print()
        - 모니터 화면에 결과물을 출력하기 위하여 활용
        - 변수의 경우 변수의 값을 출력하며, 객체별 표현 방식에 다라 출력하게 됨

            ```python
            print(123)
            # 123
            city = 'seoul'
            print(city)
            # seoul
            ```

- 코드 작성 주의 사항
    - 대소문자 구분
    - 띄어쓰기, 문자부호 등 주의 깊게 활용
    - 들여쓰기 (Identation)
        - 문장을 구분할 때, 들여쓰기를 사용
        - 들여쓰기를 할 때는 4칸 (space키 4번) 혹은 1탭 (Tab키 1번)을 입력
            - 한 코드 안에서는 반드시 한 종류의 들여쓰기를 사용
                - Tab으로 들여쓰면 계속 탭으로 들여써야 함
                - 원칙적으로는 공백 (space) 사용을 권장