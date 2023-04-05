# Django - Django Model
- 학습 목표
	- Model 클래스를 정의하고, 데이터베이스에 테이블을 생성하는 방법을 익힐 수 있다.
	- django의 Model에서 제공하는 다양한 필드 타입을 이해하고, 각가의 필드 타입을 적절히 사용할 수 있다.
	- Migration 작동 방식을 이해하고, Migration을 적용하여 데이터베이스 스키마를 관리할 수 있다.
	- Migration 파일을 생성하여 변경사항을 데이터베이스에 적용할 수 있다.


## 개요
- Model 을 통한 DB 관리
- SQLite
	- 오픈소스 RDBMS 중 하나이며 django 의 기본 DB 로 사용됨
	- DB 파일로 존재하며 가볍고 호환성이 좋음

## Model
### django Model
- DB의 테이블을 정의하고 데이터를 조작할 수 있는 기능들을 제공
- 테이블 구조를 설계하는 청사진(blueprint)

### model 클래스 작성
```python
	# articles/models.py
	
	class Article(models.Model):
		title = models.CharField(max_length=10)
		content = models.TextField()
```
- `	class Article(models.Model):`
	- django.db.models 모듈의 Model이라는 부모 클래스를 상속받아 작성
	- model 기능에 관련된 모든 설정이 담긴 클래스
	- 개발자는 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위함
- `title`,`content`
	- 클래스 변수명
		- 테이블의 각 "필드이름"
- `CharField`, `TextField`
	- model Field 클래스
		- 테이블 필드의 "데이터 타입"
- `max_length=10`
	- model Field 클래스의 키워드 인자 (필드 옵션)
		- 테이블 필드의 "제약조건" 관련 설정

## Migrations
- model 클래스의 변경사항(필드 생성, 추가 수정 등)을 DB에 최종 반영하는 방법

### Migrations 과정
1. model class (설계도 초안)
2. migration 파일 (최종 설계도)
3. db.sqlite3

### Migrations 핵심 명령어
- `$ python manage.py makemigrations`
	- model class 를 기반으로 설계도(migration) 작성
- `$ python manage.py migrate`
	- 만들어진 설계도를 DB에 전달하여 반영

### migrate 후 DB 내에 생성 된 테이블 확인
- 최종적으로 만들어진 articles_article 테이블

### 생성된 테이블에 필드 추가
```python
	# articles/models.py
	
	class Article(models.Model):
		title = models.CharField(max_length=10)
		content = models.TextField()
	# 필드 추가
		created_at = models.DateTimeField(auto_now_add=True)
		updated_at = models.DateTimeField(auto_now=True)
```

- `$ python manage.py makemigrations`
	```You are trying to add a non-nullable field 'category' to todo without a default; we can't do that (the database needs something to populate existing rows). 
		Please select a fix:
		 1) Provide a one-off default now (will be set on all existing rows with a null value for this column)
		 2) Quit, and let me add a default in models.py
	```
	- 이미 기존 테이블이 존재하기 때문에 필드를 추가 할 때 필드의 기본 값 설정이 필요
	- 1번은 직접 기본 값을 입력하는 방법
	- 2번은 현재 대화에서 나간 후 models.py 에 기본 값 관련 설정을 하는 방법
	
- 추가하는 필드의 기본값을 입력해야 하는 상황
- 날짜 데이터이기 때문에 직접 입력하기 보다 django 가 제안하는 기본 값을 사용하는 것을 권장
- 아무것도 입력하지 않고 enter 를 누르면 django 가 제안하는 기본 값으로 설정 됨
	- timezone.now

- migrations 과정 종료 후 2번째 migration 파일이 생성됨을 확인
- 이처럼 django는 설계도를 쌓아두면서 추후 문제가 생겼을 시 복구용으로 사용 할수 있도록 함

- migrate 후 필드가 추가 되었는지 확인

#### model class 에 변경사항이 생겼다면, 반드시 새로운 설계도를 생성하고, 이를 DB 에 반영해야 한다.
1. model class 작성 및 수정 
2. makemigrations
3. migrate


### CharField()
- 길이의 제한이 있는 문자열을 넣을 때 사용
- 필드의 최대 길이를 결정하는 max_length는 필수 인자

### TextField()
- 글자의 수가 많을 때 사용

### DateTimeField()
- 날짜와 시간을 넣을 때 사용

#### DateTimeField()의 선택인자
- `auto_now`
	- 데이터가 저장될 때마다 자동으로 현재 날짜시간을 저장 (글 수정)
- `auto_now_add`
	- 데이터가 처음 생성될 때만 자동으로 현재 날짜를 저장 (글쓰기)

## Admin site
### Automatic admin interface
- django 는 추가 설치 및 설정 없이 자동으로 관리자 인터페이스를 제공
- 데이터 관련 테스트 및 확인을 하기에 매우 유용

### admin 계정 생성
- `$ python manage.py createsuperuser`
- email은 선택사항이기 때문에 입력하지 않고 진행 가능
- 비밀번호 생성 시 보안상 터미널에 출력되지 않으니 무시하고 입력을 이어가도록 함

### DB 에 생성된 admin 계정 확인
- db.sqlite3 에 auth_user 에서 확인 가능

### admin 에 모델 클래스 등록
```python
	# articles/admin.py
	from django.contrib import admin
	from .models import Article
	
	admin.site.register(Article)
```

## 참고
### 데이터베이스 초기화
1. migration 파일 삭제
2. db.sqlite3 파일 삭제
- migrations 폴더를 지우지 않도록 주의

### Migrations 기타 명령어
- `$ python manage.py showmigrations`
	- migrations 파일들이 migrate 됐는지 안됐는지 여부를 확인하는 용도
	- `[X]` 표시가 있으면 migrate 가 완료되었음을 의미

- `$ python manage.py sqlmigrate articles 0001`
	- 해당 migration 파일이 SQL 문으로 어떻게 해석 되어 DB에 전달되는지 확인하는 용도
	- 