# Web - Fundamentals of Grid system
- 학습 목표
	- Grid system 의 클래스 및 기본 구조를 사용하는 방법을 이해할 수 있다.
	- Grid system을 사용하여 이미지와 텍스트를 조합한 카드 레이아웃을 구성할 수 있다.
	- Grid 구성 안에 중첩된 Grid 행을 구성할 수 있다.

## Bootstrap Grid system
- 웹 페이지의 레이아웃을 조정하는 데 사용되는 12개의 칼럼으로 구성된 시스템
- 반응형 디자인을 지원해 웹 페이지를 모바일, 테블릿, 데스크탑 등 다양한 기기에서 적절하게 표시할 수 있도록 도움

## Grid system 핵심 클래스
- 1개의 row 안에 12칸의 column 영역이 구성
- 각 요소는 12칸 중 몇 개를 차지할 것인지 지정됨
```html
	<div class="container">
		<div class="row">
			<div class="col-4"></div>
			<div class="col-4"></div>
			<div class="col-4"></div>
		</div>
	</div>
```

## offset
```html
	<div class="container">
		<div class="row">
			<div class="col-4"></div>
			<div class="col-4 offset-4"></div>
			# offset 만큼 간격을 벌림
		</div>
	</div>
```

## Gutters
- Gird system 에서 column 사이에 padding 영역
- `gx-1`
	- 수평
- `gy-1`
	- 수직
- `g-1`
	- 수평수