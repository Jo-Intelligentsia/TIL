# Django - Form
- Django Form 과 ModelForm 을 사용하여 사용자 입력 데이터를 수집하고 처리하는 방법을 이해할 수 있다.
- Django Form과 ModelForm 의 개념과 차이점을 설명 할 수 있다.
- ModelForm 을 사용하여 데이터를 데이터베이스 모델과 연결하고 저장하는 방법을 작성할 수 있다.
- Form과 ModelForm 에서 사용할 수 있는 다양한 필드 타입과 옵션을 활용 할 수 있다.

## 개요
### HTML form
- 사용자로부터 form 요소를 통해 데이터를 받고 있으나 비정상적 혹은 악의적인 요청을 확인하지 않고 모두 수용중
- 우리가 원하는 데이터 형식이 맞는지에 대한 '유효성 검증' 필요

### 유효성 검사
- 수집한 데이터가 정확하고 유효한지 확인하는 과정
- 입력 값, 형식, 중복, 범위 , 보안 등 부가적인 많은 것들을 고려해야 함
- 이런 과정과 기능을 제공해주는 도구가 필요

## Django Form
- 사용자 입력 데이터를 수집하고, 처리 및 유효성 검증을 수행하기 위한 도구
- 유효성 검사를 단순화하고 자동화 할 수 있는 기능을 제공

### Form class 선언
```python
	# articles/forms.py 생성
	from django import forms

	class ArticleForm(forms.Form):
		title = forms.CharField(max_length=10)
		content = forms.CharField()
```
### Form class 를 적용한 new 로직
```python
	# articles/views.py
	from .forms import ArticleForm

	def new(request):
		form = ArticleForm()
		context = {
			'form' : form,
		}
		return render(request, 'articles/new.html',context)
```
```html
	articles/new.html
	<form action="{% url 'articles:create' %}" method = "POST">
		{% csrf_token %}
		{{ form }} -> 추가된 내용 {{ form.ap_p }} -> 띄어쓰기 옵션
		<input type="submit">
	</form>
```

## Widgets
- HTML 'input' element의 표현을 담당
```python
	# articles/forms.py 생성
	from django import forms

	class ArticleForm(forms.Form):
		title = forms.CharField(max_length=10)
		content = forms.CharField(widget=forms.Textarea)
		
```
- widget 은 단순히 input 요소의 속성 및 출력되는 부분을 변경하는 것 (Textarea 로 변경)

## Django ModelForm

### Form
- 사용자 입력 데이터를 DB에 저장하지 않을 때
	- 로그인 기능 등
	- 
### ModelForm
- 사용자 입력 데이터를 DB 에 저장해야 할 때
	- 회원가입 기능 

### ModelForm class 선언
```python
	# articles/forms.py
	from django import forms
	from .models import Article # 추가

	class ArticleForm(forms.ModelForm): # ModelForm 으로 변경
		class Meta:
			model = Article
			fields = '__all__'
```

### Meta class 
- ModelForm의 정보를 작성하는 곳

### fields 및 exclude 속성
- `fields`
	- 포함하는 필드 지정
- `exclude`
	- 포함하지 않는 필드를 지정

### ModelForm 을 적용한 create 로직
```python
	# articles/views.py
	from .forms import ArticleForm

	def create(request):
		form = ArticleForm(request.POST)
		if form.is_valid():
			article = form.save()
			return redirect('articles:detail',article.pk)
		context = {
			'form' : form,
		}
		return render(request, 'articles/new.html, context)
```
### is_valid()
- 여러 유효성 검사를 실행하고, 데이터가 유효한지 여부를 boolean 으로 반환

### ModelForm을 적용한 edit 로직
```python
	# articles/views.py

	def edit(request,pk):
		article = Article.objects.get(pk=pk)
		form = ArticleForm(instance=article)
		context = {
			'article' : article,
			'form' : form,
		}
		return render(request, 'articles/edit.html, context)
```
```html
	<form action="{% url 'articles:update' article.pk%}" method = "POST">
		{% csrf_token %}
		{{ form.as_p }}
		<input type='submit'>
	</form>
```

### ModelForm을 적용한 update 로직
```python
	# articles/views.py
	
	def update(request,pk):
		article = Article.objects.get(pk=pk)
		form = ArticleForm(request.POST, instance=article)
		if form.is_valid():
			form.save()
			return redirect('articles:detail', article.pk)
		context = {
			'form' = form,
		}
		return render(request, 'articles/edit.html', context)
```

### `save()`
- 데이터 베이스 객체를 만들고 저장
- 키워드 인자 instance여부를 통해 생성할 지 , 수정할 지를 결