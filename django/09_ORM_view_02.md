# Django - ORM with view
- 학습 목표
	- HTTP request methods를 사용해 클라이언트가 서버로 보내는 요청의 종류를 나타낼 수 있다.
	- HTTP response status codes를 사용해 서버가 클라이언트에 반환하는 응답의 상태를 올바르게 나타낼 수 있다.
	- Django View 함수를 사용하여 데이터베이스에서 가져온 데이터를 삭제 및 수정 할 수 있다.

## HTTP request methods
### `redirect()`
- 인자에 작성된 주소로 다시 요청을 보냄

```python
	from django.shortcuts import render, redirect

	def create(request):
		title = request.GET.get('title')
		content = request.GET.get('content')
		article = Article(title=title, content=content)
		article.save()

		return redirect('articles:detail', article.pk)

	# create view 함수 수정
	# redirect 함수 적용
```

### HTTP
- 네트워크 상에서 데이터를 주고 받기위한 약속

### HTTP request methods
- 데이터(리소스)에 어떤 요청(행동)을 원하는지를 나타내는 것
- GET & POST

### 'GET' Method
- 특정 리소스를 조회하는 요청
- GET 으로 데이터를 전달하면 Query String 형식으로 보내짐

### 'POST' Method
- 특정 리소스에 변경사항을 만드는 요청
- POST 로 데이터를 전달하면 HTTP Body 에 담겨 보내짐

### POST method 적용
```html
	# templates/articles/new.html
	
	<h1>NEW</h1>
	<form action="{% url 'articles:create' %}" method='POST">
		<div>
			<label for='title'>Title: </label>
			<input type='text' name='title' id='title'>
		</div>
		<div>
			<label for='content'>Content: </label>
			<textarea name='content' id='content'></textarea>
		</div>
		<input type='submit'>
	</form>
	<hr>
	<a href='{% url 'articles:index' %}'>[back]</a>
		
```
```python
	# articles/views.py

	def create(request):
		title = request.POST.get('title')
		content = request.POST.get('content')
```

### HTTP response status code
- 특정 HTTP 요청이 성공적으로 완료되었는지 알려줌
- 5개의 그룹으로 나뉘어짐(1xx,2xx,3xx,4xx,5xx)

### 403 Forbidden
- 서버에 요청이 전달되었지만, 권한 때문에 거절되었다는 것을 의미
- CSRF token 이 누락

### CSRF (Cross-Site-Request-Forgery)
- 사이트 간 요청 위조
- 사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여 특정 웹 페이지를 보안에 취약하게 하거나 수정, 삭제 등의 작업을 하게 만드는 공격 방법

### Security Token (CSRF Token)
- 대표적인 CSRF 방어 방법
1. 서버는 사용자 입력 데이터에 임의의 난수 값(token)을 부여
2. 매 요청마다 해당 token을 포함시켜 전송 시키도록 함
3. 이후 서버에서 요청을 받을 때마다 전달된 token 이 유효한지 검증

- DTL 의 csrf_token 태그를 사용해 사용자에게 토큰 값을 부여 요청 시 토큰 값도 함께 서버로 전송될 수 있도록 함
- POST Method는 데이터베이스에 대한 변경사항을 만드는 요청이기 때문에 토큰을 사용해 최소한의 신원 확인을 하는 것
- 게시글 생성 후 개발자 도구를 사용해 Form Data가 전송되는 모습 확인

## DELETE
### DELETE 로직 작성
```python
	# articles/urls.py

	urlpatterns = [
		...
		path('<int:pk>/delete/', views.delete, name = 'delete'),
	]
	
	# articles/views.py

	def delete(request,pk):
		article = Article.objects.get(pk=pk)
		article.delete()
		return redirect('articles:index')
```
```html
	articles/detail.html

	<form action="{% url 'articles:delete' article.pk %}" method="POST">
	{% csrf_token %}
```

## Update
### Update 로직을 구현하기 위해 필요한 view 함수
- edit
	- 사용자의 입력을 받는 페이지를 렌더링
- update
	- 사용자가 입력한 데이터를 받아 DB 에 저장

### edit 로직 작성
```python
	# articles/urls.py
	
	urlpatterns = [
		...
		path('<int:pk>/edit/', views.edit, name='edit'),
	]

	# articles/views.py

	def edit(request, pk):
		article = Article.objects.get(pk=pk)
		context = {
			'article' : article,
		}
		return render(request, 'articles/edit.htm;', context)
```
```html
	<body>
	<h1>New</h1>
	<form  action="{% url  'articles:create' %}"  method='POS'>
	{% csrf_token %}
	<div>
		<label  for="title_id">제목</label>
		<input  type="text"name="title"  id='title_id' value="{{ article.title }}">
	</div>
	<div>
		<label  for="content_id">내용</label>
		<textarea  name="content"  id="content_id" {{ article.content }}></textarea>
	</div>
		<input  type="submit">
	</form>
	<a  href="{% url  'articles:index' %}">[back]</a>
	</body>
```

### edit 페이지로 이동하기 위한 하이퍼링크 작성
```html
	<body>
		<a href="{% url 'articles:edit' article.pk %}">EDIT</a><br>
		<form action="{% 'articles:delete' article.pk %}" method="POST">
			{% csrf_token %}
			<input type="submit" value ="DELETE">
		</form>
		<a href="{% url 'articles:index' %}">[back]</a>
	</body>
```

### update 로직 작성
```python
	# articles/urls.py
	urlpatterns = [
		...,
		path('<int:pk>/update/', views.update, name = 'update'),
	]

	# articles/views.py
	def update(request, pk):
		articles = Article.objects.get(pk=pk)
		article.title = request.POST.get('title')
		article.content = request.POST.get('content')
		article.save()
		return redirect('articles:detail',article.pk)
```

```html
	<form action = "{% url 'articles:update' article.pk %}" method ="POST">
```