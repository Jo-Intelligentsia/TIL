# Web - Fundamentals of Bootstrap
- 학습 목표
	- Bootstrap을 설치하고 기본 구성 요소, UI 요소 및 컴포넌트 사용방법에 대해 숙지할 수 있다.
	- Bootstrap을 이용하여 웹 프로젝트를 구현하는 방법을 익히고, 실습에 적용할 수 있다.

## Bootstrap
- 프론트엔드 라이브러리 ( Toolkit )
- 반응형 웹 디자인 & CSS 및 JS 기반의 컴포넌트와 스타일 제공

## Typography
- 문서 상에 제목, 본문 텍스트, 목록등

### Headings
- HTML h1 ~ h6 태그와 스타일을 일치 시키고 싶지만 관련 HTML 태그를 더 사용할 수 없는 경우

### Dispay headings
- 기존 Heading 보다 더 눈에 띄는 제목이 필요할 경우 ( 더 크고 약간 다른 스타일 )

### Inline text elements
- HTML inline 요소에 대한 스타일

### List
- Html list 요소에 대한 스타일

### Bootstrap Color system
- Bootstrap이 지정하고 제공하는 색상 시스템

### Colors
- Text, Border, Background 및 다양한 요소에 사용하는 Bootstrap의 색상 키워드

### Bootstrap 실습
- 너비와 높이가 각각 200px 인 정사각형 작성
- 너비와 높이를 제외한 값은 모두 bootstrap 으로 작성

```html
	.box {
		width: 200px;
		height: 200px;
		}
	<div class="box border border-2 border-dark bg-info text-white m-3"></div>

```


## Component
### Bootstrap Component
- Bootstrap에서 제공하는 UI 관련 요소
- 버튼, 폼, 카드, 드롭다운, 네비게이션 바 등
- for 일관된 디자인, 쉬운 프로토타입 제작 및 사용자 경험

### 대표 Component 사용해보기
- Alerts
- Badges
- Buttons
- Cards
- Navbar

### CDN (Content Delivery Network)
- 지리적 제약 없이 빠르고 안전하게 콘텐츠를 전송할 수 있는 전송 기술
- 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간을 최소화함
	- 웹 페이지 로드 속도를 높임