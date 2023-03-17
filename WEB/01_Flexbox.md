# Flexbox
- `Flexbox Layout`(Flexible Box) 
	- 크기를 알 수 없거나 동적인 경우에도 컨테이너의 항목 간에 공간을 배치, 정렬 및 분배하는 보다 효율적인 방법을 제공하는 것을 목표
	- 사용 가능한 공간을 가장 잘 채울 수 있도록 항목의 너비/높이(및 순서)를 변경할 수 있는 기능을 컨테이너에 제공하는 것
	- 플렉스 컨테이너는 항목을 확장하여 사용 가능한 여유 공간을 채우거나 항목을 축소하여 오버플로를 방지
	- 일반 레이아웃(수직 기반의 블록과 수평 기반의 인라인)과 달리 flexbox 레이아웃은 방향에 구애받지 않음
	
- 기본 사항 및 용어
				![enter image description here](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg)

	- `main axis`항목은 (`main-start` ~ `main-end`) 또는 교차 축(`cross-start` ~ `cross-end`) 을 따라 배치

		-   **주축** 
			-  플렉스 컨테이너의 주축은 플렉스 항목이 배치되는 기본 축입니다. 반드시 수평일 필요는 없음 (속성 에 따라 달라짐)
		-   **메인 시작 | main-end** 
			-  플렉스 아이템은 main-start에서 시작하여 main-end로 가는 컨테이너 내에 배치
		-   **기본 크기** 
			-  플렉스 항목의 너비 또는 높이 중 기본 치수에 있는 것이 항목의 기본 크기
			-  플렉스 아이템의 기본 크기 속성은 'width' 또는 'height' 속성 중 기본 차원에 있는 것
		-   **교차축** 
			-  주축에 수직인 축
			-  방향은 주축 방향에 따라 달라짐
		-   **교차 시작 | cross-end** 
			- 플렉스 라인은 항목으로 채워지고 플렉스 컨테이너의 교차 시작 쪽에서 시작하여 교차 끝 쪽으로 가는 컨테이너에 배치
		-   **교차 크기** 
			-  플렉스 항목의 너비 또는 높이 중 교차 차원에 있는 것
			-  교차 크기 속성은 교차 차원에 있는 '너비' 또는 '높이' 중 하나

## Flex Box 속성
- 부모 속성 (플렉스 컨테이너) 							
![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg)

- 컨테이너 정
```css
	.container {
		display: flex;
	}
```

- 컨테이너 방향
	![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)

	- 주축이 설정되어 플렉스 항목이 플렉스 컨테이너에 배치되는 방향을 정의
	-  Flexbox는 (선택적 래핑을 제외하고) 단방향 레이아웃 개념
	-  플렉스 아이템은 주로 가로 행이나 세로 열에 배치되는 것으로 생각

	```css
		.container {
		  flex-direction: row | row-reverse | column | column-reverse;
		}
	```

	-   `row`(기본값) 
		- 왼쪽에서 오른쪽으로 `ltr`; 오른쪽에서 왼쪽으로`rtl`
	-   `row-reverse`
		-  오른쪽에서 왼쪽으로 `ltr`; 왼쪽에서 오른쪽으로`rtl`
	-   `column`
		-  위에서 아래로
	-   `column-reverse`
		- `column` 과 반대 , 아래에서 위로

- 플렉스 랩
	![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg)

	- 기본적으로 플렉스 항목은 모두 한 줄에 맞추려고 함
	- 이를 변경하고 이 속성을 사용하여 필요에 따라 항목을 래핑하도록 허용 가능

	```css
	.container {
	 flex-wrap: nowrap | wrap | wrap-reverse;
	}
	```

	-   `nowrap`(기본값)
		- 모든 플렉스 항목이 한 줄에 표시
	-   `wrap`
		-  플렉스 항목은 위에서 아래로 여러 줄로 래핑
	-   `wrap-reverse`
		-  플렉스 항목은 아래에서 위로 여러 줄로 래핑

- 플렉스 흐름
	- 플렉스 컨테이너의 기본 축과 교차 축을 함께 정의 
	- `flex-direction`및 속성

		```css
			.container {
			  flex-flow: column wrap;
			}
		```

- 정당화 내용
	![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)

	- 기본 축을 따라 정렬
	-  한 줄의 모든 플렉스 항목이 유연하지 않거나 유연하지만 최대 크기에 도달한 경우 남은 여유 공간을 분산하는 데 도움
	-  항목이 줄을 넘을 때 항목의 정렬을 일부 제어

	```css
		.container {
		  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
		}
	```

	-   `flex-start`(기본값)
		- flex-direction의 시작 부분으로 패킹
	-   `flex-end`
		-  flex-direction의 끝으로 패킹
	-   `start`
		-  방향의 시작을 향해 아이템이 포장 `writing-mode`.
	-   `end`
		-  아이템은 끝 방향으로 포장 `writing-mode`.
	-   `left`
		-  컨테이너의 왼쪽 가장자리 쪽으로
	-   `right`
		-  컨테이너의 오른쪽 가장자리를 향해 패킹 
	- `center`
		-  선을 따라 중앙에 정렬
	- `space-between`
		-  라인에 고르게 분포
		-  첫 번째 항목은 시작 줄, 마지막 항목은 끝 줄
	-   `space-around`
		-  주위에 동일한 간격으로 줄에 고르게 분포 
		- 모든 항목의 양쪽에 동일한 공간이 있으므로 시각적으로 공간이 동일하지 않음
		-  첫 번째 항목에는 컨테이너 가장자리에 대해 1단위의 공간이 있지만 다음 항목에는 적용되는 자체 간격이 있으므로 다음 항목 사이에는 2단위의 공간이 있음
	-   `space-evenly`
		-  두 항목 사이의 간격(및 가장자리까지의 공간)이 동일하도록 항목이 분산

- 정렬 항목
	![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg)

	- 플렉스 아이템이 현재 라인의 **교차축을** 따라 배치되는 방식
	- `justify-content`교차축 버전(주축에 수직) 

	```css
		.container {
		  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
		}
	```

	-   `stretch`(기본값)
		-  컨테이너를 채울 때까지 늘림(여전히 최소 너비/최대 너비 준수).
	-   `flex-start`/ `start`/ `self-start`
		-  교차축의 시작 부분에 배치 
	-   `flex-end`/ `end`/ `self-end`
		-  교차축 끝에 배치 
	-   `center`
		- 항목이 교차축 중앙에 정렬됨
	-   `baseline`
		-  기준선 정렬과 같이 항목이 정렬

- 정렬 내용
	![enter image description here](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg)

	- `justify-content`주축 내 에서 개별 항목을 정렬하는 방법과 유사하게 교차축에 추가 공간이 있을 때 내에서 플렉스 컨테이너의 선을 정렬

	- **참고:** 이 속성은 `flex-wrap`로 설정된 여러 줄의 유연한 컨테이너에만 적용
	-  한 줄짜리 유연한 컨테이너(즉, 기본값으로 설정된 경우 )는 를 반영하지 않음 
	- `wrap``wrap-reverse``flex-wrap``no-wrap``align-content`

	```css
	.container {
	  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
	}
	```

	-   `normal`(기본값)
		-  값이 설정되지 않은 것처럼 항목이 기본 위치에 패킹
	-   `flex-start`/ `start`
		-  컨테이너 시작 부분에 패킹
	-   `flex-end`/ `end`
		-  컨테이너 끝까지 포장된 아이템
	-   `center`
		-  컨테이너 중앙
	-   `space-between`
		-  항목이 고르게 분포됨
		-  첫 번째 줄은 컨테이너의 시작 부분에 있고 마지막 줄은 끝
	-   `space-around`
		-  각 줄 주위에 동일한 간격으로 고르게 분포
	-   `space-evenly`
		-  항목 주위에 동일한 공간을 두고 고르게 분포
	-   `stretch`
		-  선이 늘어나 나머지 공간을 차지함

