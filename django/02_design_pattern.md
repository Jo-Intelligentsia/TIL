# Django - Django design pattern

-학습 목표
	- Django MTV 디자인 패턴의 개념과 구조를 이해할 수 있다.
	- Django URL 매핑을 이해하고 작성할 수 있다.
	- View 계층을 이해하고 HTTP 요청과 응답을 처리하는 뷰 함수를 구현할 수 있다.
	- Template 계층을 이해하고 템플릿을 작성하고 출력할 수 있다.

## django 프로젝트와 앱

### django project 
- 애플리케이션의 집합 
- DB 설정, URL 연결, 전체 앱 설정 등을 처리

### django application
- 독립적으로 작동하는 기능 단위 모듈
- 각자 특정한 기능을 담당하며 다른 앱들과 함께 하나의 프로젝트를 구성

### 앱 생성
```python
	$ python manage.py startapp articles
```

### 앱 등록
```python
	# settings.py	  
	# Application definition
	INSTALLED_APPS = [
	'articles', # 추가
	'django.contrib.admin',
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.messages',
	'django.contrib.staticfiles',
	]	

	# 반드시 앱을 생성한 후에 등록해야 함
	# 반대로 등록 후 생성은 불가능
```

## django 디자인 패턴

### 디자인 패턴
- 소프트웨어 설계에서 발생하는 문제를 해결하기 위한 일반적인 해결책
- 공통적인 문제를 해결하는데 쓰이는 형식화 된 관행

### MVC 디자인 패턴
- Model , View , Controller
- 애플리케이션을 구조화하는 대표적인 패턴
- 데이터, 사용자 인터페이스, 비즈니스 로직을 분리
- 시각적 요소와 뒤에서 실행되는 로직을 서로 영향없이, 독립적이고 쉽게 유지보수할 수 있는 애플리케이션을 만들기 위해

### MTV 디자인 패턴
- Model, Template, View
- django 에서 애플리케이션을 구조화하는 패턴
- 기존 MVC 패턴과 동일하나 명칭을 다르게 정의
- View -> Template
- Controller -> View

### 프로젝트 구조
- 현재 단계에서 수정
	- settings.py
		- 프로젝트의 모든 설정을 관리
	- urls.py
		- URL과 이에 해당하는 적절한 views를 연결

- 현재 단계에서는 수정하지 않음
	- __init__.py
		- 해당 폴더를 패키지로 인식하도록 설정
	- asgi.py
		- 비동기식 웹 서버와의 연결 관련 설정
	- wsgi.py
		- 웹 서버와의 연결 관련 설정
	- manage.py
		- Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인 유틸리티

### 앱 구조
- 현재 단계에서 수정
	- admin.py
		- 관리자용 페이지 설정
	- models.py
		- DB와 관련된 Model을 정의
		- MTV 패턴의 M
	- views.py
		- HTTP요청을 처리하고 해당 요청에 대한 응답을 반환
		- URL,mode, template 과 연계
		- MTV 패턴의 V

- 현재 단계에서는 수정하지 않음
	- apps.py
		- 앱의 정보가 작성된 곳
	- tests.py
		- 프로젝트 테스트 코드를 작성하는 곳

## 요청과 응답
### URLs

```python
	# urls.py
	
	from django.contrib import admin
	from django.urls import path
	
	from articles import views # 작성 해야함
	urlpatterns = [
		path('admin/', admin.site.urls), # 기존에 있던 admin으로 가는 주소
		path('articles/', views.index), # 새로 작성 , / 꼭 붙이기
		
```

- http://128.0.0.1:8000/articles/ 로 요청이 왔을 때 views 모듈의 index 뷰 함수를 호출한다는 뜻


### View
```python
	# views.py
	from django.shortcuts import render
	
	# 함수 생성 (사이트로 가기위한)
	def index(request):	# request 변경 X
		return render(request, 'articles/index.html')
```

- 특정 경로에 있는 template 과 request 객체를 결합해 응답 객체를 반환하는 index 뷰 함수 정의


### Template
- articles 앱 폴더안에 templates 폴더 작성
- templates 폴더 안에 템플릿 페이지 작성
- 반드시 templates 폴더명이어야 하며, 개발자가 직접 생성해야 함

### django에서 template을 인식하는 경로 규칙
- app폴더 / templates / articles / index.html
- app폴더 / templates / example.html
- django 는 app폴더 / templates / 지점까지 기본 경로로 인식
- 기본 경로 이후의 지점을 작성

### 데이터 흐름에 따른 코드 작성
1. URLs
	- path('articles/', views.index), 
2. View
	- def index(request):
		return render(request, 'articles/index.html')
3. Template
	- articles/templates/articles/index.html

## 참고
### render 함수
- `render(request, template_name, context)`
	- 주어진 템플릿을 주어진 컨텍스트 데이터와 결합하고 렌더링 된 텍스트와 함께 HttpResponse (응답) 객체를 반환하는 함수
	1. request
		- 응답을 생성하는데 사용되는 요청 객체
	2. template_name
		- 템플릿 이름의 경로
	3. context
		- 템플릿에서 사용할 데이터 (딕셔너리 타입으로 작성)