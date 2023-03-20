# Web Positioning for CSS layout

- 학습 목표
	- position 속성을 이용해 HTML 요소의 위치와 레이아웃을 조작할 수 있다.
	- static, relative, absolute, fixed, sticky 의 특징과 사용 방법을 이해하고 상황에 맞게 적용할 수 있다.
	- z-index 속성을 이용해 요소의 쌓임 순서를 변경할 수 있다.

- CSS Layout
	- 각 요소의 위치와 크기를 조정하여 웹 페이지의 디자인을 결정하는 것
	- Display, Position, Floats, Flexbox...

- CSS Position
	- Normal Flow 에서 요소를 끄집어내서 다른 위치로 배치하는 것
		- Normal Flow
			- CSS를 적용하지 않았을 경우 웹페이지 요소가 기본적으로 배치되는 방향
	- 다른 요소 위에 놓기, 화면 특정 위치에 고정시키기 등

- Position 유형
	- `static`
		- 기본 값
		- 요소를 Normal Flow 에 따라 배치
	- `relative`
		- 요소를 Normal Flow 에 따라 배치
		- 자기 자신을 기준으로 이동
		- 요소가 차지하는 공간은 static 일 때와 같음
	- `absolute`
		- 요소를 Normal Flow 에서 제거
		- 가장 가까운 relative 부모 요소를 기준으로 이동
		- 문서에서 요소가 차지하는 공간이 없어짐
	- `fixed`
		- 요소를 Normal Flow 에서 제거
		- 현재 화면영역(viewport)을 기준으로 이동
		- 문서에서 요소가 차지하는 공간이 없어짐
	- `sticky`
		- 요소를 Normal Flow 에 따라 배치
		- 가장 가까운 block 부모 요소를 기준으로 이동
		- 요소가 특정 임계점에 스크롤 될때 그위치에서 고정됨
		- 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky 요소의 자리를 대체
			- 이전 sticky 요소가 고정되어 있던 위치와 다음 sticky 요소가 고정되어야 할 위치가 겹치게 되기 때문

- `z-index`
	- 요소가 겹쳤을 때 어떤 요소 순으로 위에 나타낼 지 결정
		- z축 (스크린 표면으로부터 사용자 얼굴 쪽으로 향하는 라인) 기준 정렬
	- 정수 값을 사용해 Z축 순서를 지정
	- 더 큰 값을 가진 요소가 작은 값의 요소를 덮