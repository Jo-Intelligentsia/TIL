# Django - ORM with view
- 학습 목표
	- Django View 함수를 사용하여 데이터베이스에서 가져온 데이터를 처리할 수 있는 능력을 가질 수 있다.
	- Django ORM과 View 함수를 결합하여 웹 애플리케이션의 데이터를 저장하고 렌더링 할 수 있다.


## 사전 준비
### app URLs 분할 및 연결
```python
	# articles/urls.py
	from django.urls import path

	app_name = 'articles'
	urlpatterns = [
	]

	# crud/urls.py
	from django.contrib import admin
	from django.urls import path, include

	urlpatterns = [
		path('admin/', admin.site.urls),
		path('articles/'. include('articles.urls')),
	]
```

### index 페이지 생성
```python
	# articles/urls.py
	from django.urls import path
	from . import views
	
	app_name = 'articles'
	urlpatterns = [
		path('',views.index, name = 'index'),
	]
	
	# articles/views.py

	def index(request):
		return render(request, 'articles/index.html')

	# articles/index.html
	<h1> Articles </h1>
```

## READ
### 전체 게시글 조회
```python
	# articles/views.py
	from .models import Article

	def index(request):
		articles = Article.objects.all()
		context = {
			'articles' : articles,
		}
		return render(request, 'articles/index.html')

	# articles/index.html

	<h1> Articles </h1>
	<hr>
	{% for article in articles %}
		<p>글 번호 : {{ article.pk }}</p>
		<p>글 제목 : {{ article.title }}</p>
		<p>글 내용 : {{ article.content }}</p>
		<hr>
	{% endfor %}

```

### 단일 게시글 조회
```python
	# articles/urls.py

	urlpatterns = [
		...
		path('<int:pk>/', views.detatil, name = 'detail'),
	]

	# articles/views.py

	def detail(request,pk):
		article = Article.objects.get(pk=pk)
		context = {
			'article' : article,
		}
		return render(request, 'articles/detail.html', context)

	# templates/articles/detail.html
		<h1>Detail</h1>
		<p>글 번호 : {{ article.pk }}</p>
		<p>제목 : {{ article.title }}</p>
		<p>내용 : {{ article.content }}</p>
		<p>작성일 : {{ article.created_at }}</p>
		<p>수정일일 : {{ article.updated_at }}</p>
		<a  href="{% url  'articles:index' %}">[back]</a>
```

### 제목을 누르면 해당 글의 상세 페이지로 이동
```python
	# templates/articles/detail.html
	<h1>Articles</h1>
		<a  href="{% url  'articles:new' %}">[NEW]</a>
		{% for  article  in  articles %}
			<p> 글 번호 : {{ article.pk }} </p>
			<a  href="{% url  'articles:detail'  article.pk %}">
				<p> 글 제목 : {{ article.title }}</p>
			</a>
			<p> 글 내용 : {{ article.content }}</p>
			<hr>
		{% endfor %}
```

## CREATE
### Creat 로직을 구현하기 위해 필요한 view 함수
- new ( 입력 받는 함수 )
	- 사용자의 입력을 받는 페이지를 렌더링
- create ( 입력값을 저장하는 함수 )
	- 사용자가 입력한 데이터를 받아 DB에 저장