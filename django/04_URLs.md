# django - django URLs

- 학습 목표
	- Dispatcher 로서의 django URL 을 정의하고 어떻게 작동하는지 이해할 수 있다.
	- URL 패턴 작성 방법을 이해하고, URL의 변수를 추출하는 방법을 사용할 수 있다.
	- URL에 이름을 붙여 별칭을 사용하여 쉽게 참조할 수 있다.
	
## 개요
### URL disatcher
- URL 패턴을 정의하고 해당 패턴이 일치하는 요청을 처리할 view 함수를 연결 (매핑)

## 변수와 URL
### Variable Routing
- URL 일부에 변수를 포함시키는 것
- 변수는 view 함수의 인자로 전달 할 수 있음

#### Variable routing 작성법
- `<path_converter:variable_name>`
- `<타입 : 변수명>`
- `path('articles/<int:num>/',views.hello)`
- `path('hello/<str:name>/',views.greeting)`


### Variable routing 실습
1.
```python
	# urls.py
	urlpatterns = [
		path('articles/<int:num>/',views.detail),
	]

	# views.py
	# request 옆에 urls에서 넘어온 변수명 넣기
	def detail(request, num):
		context = {
			'num'=num,
		}
	return render(request,'articles/detail.html, context)
		
```
```django
	detail.html
	{% extends 'base.html' %}

	{% block content %}
		<h1>Detail</h1>
		<h3>{{ num }}번 글 입니다.</h3>
	{% endblock content %}
```

2.
```python
	# urls.py
	urlpatterns = [
		path('hello/<str:name>/',views.greeting),
	]

	# views.py
	# request 옆에 urls에서 넘어온 변수명 넣기
	def detail(request,	name):
		context = {
			'name'=name,
		}
	return render(request,'articles/greeting.html, context)
		
```
```django
	detail.html
	{% extends 'base.html' %}

	{% block content %}
		<h1>Greeting</h1>
		<h3>{{ name }}님 안녕하세요.</h3>
	{% endblock content %}
```

## App의 URL

### App URL mapping
- 각 앱에 URL 을 정의하는 것
- 프로젝트와 각각의 앱이 URL을 나누어 관리하여 주소 관리를 편하게 하기 위함

### include()
- 다른 URL들을 참조할 수 있도록 돕는 함수
- URL의 그 시점까지 일치하는 부분을 잘라내고, 남은 문자열 부분을 후속 처리를 위해 include된 URL로 전

```python
	# firstpjt/urls.py
	
	from django.urls import path,include

	urlpatterns = [
		path('admin/', admin.site.urls),
		path('articles/', include('articles.urls')),
		path('pages/', include('pages.urls')),
	]
```


## URL 이름 지정
### Naming URL patterns
- URL 에 이름을 지정하는 것
- path 함수의 name 인자를 정의해서 사용

### name 인자 작성

```python
	# articles/urls.py

	from django.urls import path
	from . import views

	urlpatterns = [
		path('index/', views.index, name='index'),
		path('dinner/', views.dinner, name='dinner'),
		path('search/', views.search, name='search'),
		path('throw/', views.throw, name='throw'),
		path('catch/', views.catch, name='catch'),
		path('articles/<int:num>/', views.detail, name='detail'),
	]


	# pages/urls.py
	
	from django.urls import path
	from . import views

	urlpatterns = [
		path('index/', views.index, name = 'index'),
		path('hello/<str:name>/', views.greeting, name='greeting'),
	]
```

### URL 표기 변화
```django
	articles/index.html
	{% extends 'base.html' %}
	
	{% block content %}
		<h1>Hello, {{ name }}</h1>
		<a href="/dinner/">dinner</a>
		<a href="/search/">search</a>
		<a href="/throw/">throw</a>
	{% endblock content %}

	articles/index.html
	{% extends 'base.html' %}
	
	{% block content %}
		<h1>Hello, {{ name }}</h1>
		<a href="{% url 'dinner' %}">dinner</a>
		<a href="{% url 'search' %}">search</a>
		<a href="{% url 'throw' %}">throw</a>
	{% endblock content %}
```

### url tag
- 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환
- `{% url 'url-name' arg1 arg2 %}`

## URL Namespace
### app_name 속성 지정
- url 이름 + app 이름표 붙이기

```python
	# articles/urls.py

	app_name = 'articles'
	urlpatterns = [
	...,
	]

	# pages/urls.py

	app_name = 'pages'
	urlpatterns = [
	...,
	]
```


### URL tag 의 변화
- `{% url 'index' %}` -> `{% url 'articles:index' %}`

## 참고
### app_name 지정 후 주의사항
- app_name 을 지정한 이후에는 url 태그에서 반드시 app_name:url_name 형태로만 사용할 수 있음
- 그렇지 않으면 NoReverseMatch 에러가 발생
- 즉, app_name 지정 후 다음과 같은 표기는 사용 불가
- `{% url 'index' %}`

### Trailing Slashes
- django는 URL 끝에 '/' 가 없다면 자동으로 붙임
- django 의 URL 설계 철학
	- 기술적인 측면에서, foo.com/bar 와 foo.com/bar/는 서로 다른 URL 이다
- 검색 엔진 로봇이나 웹 트래픽 분석 도구에서는 이 두 주소를 서로 다른 페이지로 봄
- 그래서 django는 검색 엔진이 혼동하지 않게 하기 위해 사용
- 그러나 모든 프레임워크가 이렇게 동작하는 것은 아