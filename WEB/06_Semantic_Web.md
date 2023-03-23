# Web - Semantic Web

- 학습 목표
	- Web Semanics 에 대한 기본 개념과 원리를 이해하고, 이를 바탕으로 웹 컨텐츠에 의미를 부여할 수 있다.
	- 웹 기술의 발전에 대한 역사와 현재 동향을 파악하며, 웹의 미래 방향성을 이해할 수 있다.

- Semantic Web
	- 웹 데이터를 의미론적으로 표현하고 연결하는 개념
	- for 컴퓨터가 데이터의 내용과 문맥을 더 효율적으로 이해하고 더 지능적으로 활용

- HTML Semantic Element
	- 기본적인 모양과 기능 이외에 의미를 가지는 HTML 요소
	- 검색엔진 및 개발자가 웹 페이지의 콘텐츠를 이해하기 쉽게 만들어줌

- 페이지 구조화를 위한 대표적인 semantic element
	- header
	- nav
	- main
	- article
	- section
	- aside
	- footer

## Semantics in CSS
- OOCSS
	- Object-Oriented CSS
	- 객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론

- BEM
	- Block Element Modifier
	- 블록, 요소, 수정자를 사용해 클래스 이름을 구조화하는 방법론

	- Block
		- 문단 전체에 적용된 요소 또는 요소를 담고 있는 컨테이너
		- 재사용 가능한 독립적 블록, 가장 바깥쪽 상위요소
		- 재사용을 위해 margin 또는 padding을 적용하지 않음
	- Element
		- block이 포함하고 있는 한 조각
		- 블록을 구성하는 종속적인 하위요소
	- Modifier
		- block 또는 element의 속성

	```html
		.block {}
		.block__element {}
		.block--modifier {}
	```

- OOCSS & BEM 의 목적
	- 재사용 가능한 모듈로 분리함으로써 유지보수성과 확장성을 향상
	- 개발자 간의 협력이 향상되어 공통 언어와 코드 이해를 확립
