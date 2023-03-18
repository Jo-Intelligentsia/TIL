# Web - Fundamentals of HTML and CSS

- 학습 목표
	- HTML 문서의 구조를 이해하고, 태그를 사용하여 웹 페이지의 구조와 콘텐츠를 작성할 수 있다.
	- CSS 속성과 값의 구조를 이해하고, 스타일 시트를 사용하여 웹 페이지의 디자인과 레이아웃을 구성할 수 있다.
	- CSS 선택자를 이해하고, 스타일을 적용할 요소를 선택하는 방법을 익힐 수 있다.

## Introduction of web papg
- `World Wide Web`
	- 인터넷으로 연결된 컴퓨터들이 정보를 공유하는 거대한 정보 공간
- `Web site`
	- 인터넷에서 여러개의 `Web page` 가 모인것으로, 사용자들에게 정보나 서비스를 제공하는 공간
	- 여러 개의 `Web page`가 모여서 구성
- `Web page`
	- `HTML`,`CSS`,`JavaScript` 등의 웹 기술을 이용하여 만들어진, 하나의 인터넷 문서
	- `Web site`를 구성하는 하나의 요소

## Structuring the web
### Introduction to HTML
- `HTML`
	- `HyperText Markup Language`
	- 웹 페이지의 의미와 구조를 정의하는 언어
- `Hypertext`
	- 웹 페이지를 다른 페이지로 연결하는 링크
	- 참조를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
- `Markup Language`
	- 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어

### Structure of HTML
- `HTML` Element
	- 하나의 요소는 여는 태그와 닫는 태그 그리고 그 안의 내용으로 구성됨
	- 닫는 태그는 태그 이름 앞에 슬래시가 포함되며 닫는 태그가 없는 태그도 존재
	```html
		<p>My cat is vary grumpy</p>
		-> <p> Opening tag
		-> </p> Closing tag     
	```
- `HTML Attributes`
	- 규칙 
		- 요소 이름 다음에 바로 오는 속성은 요소 이름과 속성 사이에 공백이 있어야 함
		- 하나 이상의 속성들이 있는 경우엔 속성 사이에 공백으로 구분함
		- 속성값은 열고 닫는 따옴표로 감싸야 함
	- 목적
		- 나타내고 싶지 않지만 추가적인 기능, 내용을 담고 싶을 때 사용
		- CSS 가 해당 요소를 선택하기 위한 값으로 활용됨
	```html
		<p class="editor-note">My cat is very grumpy</p?
	```
- `HTML` 문서의 구조
	- `<!DOCTYPE html>`
		- 해당 문서가 html 문서라는 것을 나타탬
	- `<html></html>`
		- 전체 페이지의 콘텐츠를 포함
	- `<title></title>`
		- 브라우저 탭 및 즐겨찾기 시 표시되는 제목으로 사용
	- `<head></head>`
		- HTML 문서에 관련된 설명, 설정등
		- 사용자에게 보이지 않음
	- `<body></body>`
		- 페이지에 표시되는 모든 콘텐츠

### Text Structure
- `HTML Text structure`
	- `HTML`의 주요 목적 중 하나는 텍스트 구조와 의미를 제공하는 것
	```html
		<h1>Main Heading</h1>
		예를 들어 <h1> 은 단순히 텍스트를 크게 만드는 것이 아닌 
		해당 문서의 최상위 제목이라는 의미를 부여하는것
	```
- 대표적인 `HTML Text structure`
	- Heading & Paragraphs 
		- h1 ~ 6 , p
	- Lists 
		- ol, ul, li
	- Emphasis & Importance
		- em
		- strong

## Styling the web
### Introduction to CSS
- `CSS`
	- Cascading Style Sheet
	- 웹 페이지의 디자인과 레이아웃을 구성하는 언어
	```html
		h1{
		color: bule;
		font-size: 15px;
		}
		h1 -> 선택자 
		color:bule; -> 선언
		font-size -> 속성
		15px -> 값
	```
- `CSS` 적용 방법
	- 인라인 (Inline) 스타일
		- 코드 내부에 삽입하여 사용
	- 내부 (Internal) 스타일 시트
		- `<head>` 사이 `<style></style>` 사이에 넣어 사용 
	- 외부 (Extenal) 스타일 시트
		- 별도의 `CSS` 파일 생성 후 불러오기 
		- `<head>` 사이 넣어서 사용

### Select elements
- `CSS Selectors`
	- `HTML` 요소를 선택하여 스타일을 적용할 수 있도록 함
- `CSS Selectors` 종류
	- 기본 선택자
		- 전체(`*`) 선택자
		- 요소(`tag`) 선택자
		- 클래스(`class`) 선택자
		- 아이디(`id`) 선택자
		- 속성(`attr`) 선택자
	- 결합자 (Combinators)
		- 자손 결합자(`" "(space)`)
		- 자식 결합자 (`>`)
- `CSS Selectors` 특징
	- 요소 선택자
		- 지정한 모든 태그를 선택
	- 클래스 선택자
		- 주어진 클래스 속성을 가진 모든 요소를 선택
	- 아이디 선택자
		- 주어진 아이디 속성을 가진 요소 선택
		- 문서에는 주어진 아이디를 가진 요소가 하나만 있어야 함
	- 자손 선택자
		- 첫 번째 요소의 자손 요소들 선택
	- 자식 선택자
		- 첫 번째 요소의 직계 자식만 선택

```html
	<head>
		<style>
			- 전체 선택자 
			* {
				color: red;
			}
			- 타입 선택자
			h2 {
				color: orange;
			}
			h3,
			h4 {
				color: blue;
			}
			- 클래스 선택자
			.green {
				color: green;
			}
			#purple {
				color:purple;
			}
			- 자식 결합자
			.green > span {
				font-size: 50px;
			}
			- 자손 결합자
			.green li {
				color: brown;
			}
		</style>
	</head>
	<body>
		<h1 class="green">Heading</h1>
		<h2> 선택자 연습 </h2>
		<h3> Hello </h3>
		<h4> Nice to meet you </h4>
		<p id="puple"> 과목 목록 </p>
		<ul class="green">
			<li>파이썬</li>
			<li>알고리즘</li> 
			<li>웹
				<ol>
					<li>HTML</li>
					<li>CSS</li>
					<li>JS</li>
				</ol>
			</li>
		</ul>
		<p class="green">Lorem, <span>ipsum</span> dolr.</p>
	</body>
	
```

### Cascade & Specificity
- 동일한 요소에 적용 가능한 같은 스타일을 두 가지 이상 작성 했을때 어떤 규칙이 이기는지 결정하는 것

- Cascade (계단식)
	- 동일한 우선순위를 같은 규칙이 적용될 때 CSS에서 마지막에 나오는 규칙이 사용
- Specificity (우선순위)
	- 선택자 별로 정해진 우선순위 점수에 따라 점수가 높은 규칙이 사용
	- 우선순위가 높은 순
		1. Importance
			- Cascade의 구조를 무시하고 모든 우선순위 점수 계산을 무효화하는 가장 높은 우선순위
			- 반드시 필요한 경우가 아니면 절대 사용하지 않는 것을 권장
		2. 우선순위
			- 인라인 > id > class > 요소
		3. 소스 코드 순서

- 상속
	- 기본적으로 `CSS` 는 상속을 통해 부모 요소의 속성을 자식에게 상속함
	- 이를 이용해 코드의 재사용성을 높임
	- 상속 되는 속성
		- Text 관련 요소
	- 상속 되지 않는 속성
		- Box model 관련 요소
		- position 관련 요소