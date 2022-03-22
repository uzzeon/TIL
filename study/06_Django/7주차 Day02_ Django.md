# 7주차 Day02_ Django

https://docs.djangoproject.com/en/3.2/ref/templates/builtins/



## 1. Django 처음 시작하기 



1. 가상환경 생성 : venv 폴더

```python
$ python -m venv venv
```

2. 가상환경 실행 : venv 실행

```python
$ source venv/Scripts/activate
(venv)
```

3. Django 설치

```python
$ pip install django==3.2.12
```

4. 프로젝트 생성

```python
$ django-admin startproject pjt .
```

5. 서버 실행

```python 
$ python manage.py runserver
```



※ 시험 빈출 : `settings.py` 에서  

```django
LANGUAGE_CODE = 'ko-kr'
TIME_ZONE = 'Asian/Seoul'
USE_I18N = TRUE
USE_L10N = TRUE
USE_TZ = TRUE
```



6. 앱 생성 : articles 앱 생성 + Template 폴더는 직접 만들기

```python
$ python manage.py startapp articles
```

7. settings.py에 `Installed_APPS` 에 articels 추가하기

```python
INSTALLED_APPS = [
    'articles',
    ...
]
```



8. `url.py` 에서 경로, view 매핑

​	- 하나의 경로에는 view 하나만 연결시킬 수 있다.

9. `views.py` 에서 

```python
def lunch(request):
    return render(request, 'lunch.html', context)
```

10. `lunch.html`을 만들어서 사용자에게 보일 화면 만들기



![image-20220303095546629](7%EC%A3%BC%EC%B0%A8%20Day02_%20Django.assets/image-20220303095546629.png)



---

---



## 2. 요청과 응답



#### 반복문

```django
{% for menu in lunch_box %}

{% endfor %}
```



#### 기본 개발 흐름

> URL - VIEWS - TEMPLATE





## 3. Form

- 기본적으로 `action 과 method` 로 구성된다 (핵심 속성)
  - action : form을 처리할 URL
  - method : 입력 데이터 전달 방식 GET/POST
- `input` 요소 : 다양한 type이 있음 (radio, text, email, password 등) _사용자로부터 데이터를 입력받기 위해 사용됨
- `name` 요소: 값(value)을 담는 이름(변수 이름)
- `label` : for 속성 필요, input에 id 연결_ 설명(caption)을 나타냄

```python
<form action="" method="GET">
  <label for="message">메시지 : </label>
  <input type="text" id="message" name="message">
  <input type="submit" value="">
</form>
```



#### HTTP (HyperText Transfer Protocol)

- GET, POST, PUT ...
- GET : 서버로부터 정보를 조회하고 데이터를 가져올 때만 사용함



#### 'GET' - request method & Throw/Catch

- 2개가 필요함

```bash
/throw/ - Form
/catch/ - Form에 담긴 내용을 전달
```

1. throw 만들기 

   ```python
   ## url
   path('throw/, views.throw')
   
   ## views.py
   def throw(request):
       return render(request, 'throw.html')
   
   ## throw.html
   <form action="/catch/" method="GET">
     <label for="message">메시지 : </label>
     <input type="text" id="message" name="message">
     <input type="submit" value="뿡">
   </form>
   ```

2. catch 만들기

   ```python
   ## url.py
   path('catch/', views.catch),
   
   ## views.py
   def catch(request):
       message = request.GET.get('message')
       #request에서 온 것을 받겠다는 GET과 딕셔너리에서의 get
       #error message를 띄우기보다는 빈값으로 보여주려고 get을 쓴다
       context = {
           'message': message
       }
       return render(request, 'catch.html', context)
   
   ## catch.html
   <h1>{{ message }}</h1>
   <a href="/throw/">다시 던지기</a>
   ```

   - `action="/catch/"` `name="message"` 가 합쳐져서
   - context dictionary에서 message라는 키를 줘서, html에서 message를 쓸 수 있는 것

![image-20220303104831926](7%EC%A3%BC%EC%B0%A8%20Day02_%20Django.assets/image-20220303104831926.png)

- request... 요청된 객체들을 하나로 묶어놓는 것



#### 'id' 속성

- [주소](http://127.0.0.1:8000/blog/8/) 이렇게 쓰면 id가 화면에 받아짐

![image-20220303110938178](7%EC%A3%BC%EC%B0%A8%20Day02_%20Django.assets/image-20220303110938178.png)



## 4. URL 



#### App URL 매핑 (앱별로 url 분리해서 연결)

```django
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
```

```PYTHON
### 앱 이름 저장해서 사용하기 ##
app_name = 'articles'	# 앱이름 지정
urlpatterns = [
    path('throw/', views.throw, name='throw'),	#url 이름 throw로 지정
]

## catch.html에서
<a href="{% url 'articles:throw' %}">다시 던지기</a>

## throw.html에서
<form action="{% url 'articles:catch' %}" method="GET">
```



#### Variable Routing

> url 주소 자체를 변수로 사용하는 것
>
> URL 주소로 들어오는 값을 변수로 지정하여 views.py 함수의 인자로 넘겨준다.

```django
path('accouts/user/<int:user_pk>/', ...)
# accounts/user/1 → 1번 user 관련 페이지
# accouts/user/2 → 2번 user 관련 페이지
```



#### render(request, template_name, context)

```python
```

- Request object를 받아서 template과 context를 결합하여 하나의 html 파일을 만들어주고, HttpResponse object를 반환한다.



#### 상속

- 어느 템플릿을 상속할 것인지
- 그 템플릿에 어느 블록에 넣을 것인지

```python
##views.py
{% block content %}
{% endblock %}

##base.html
<ul>
  {% for n in lotto %}
    <li> {{ n }}</li>
  {% endfor %}
</ul>

## base.html에서 템플릿을 다 만들고 이를 views에서 가져와서 사용함
```

- `APP_DIRS` : 등록된 앱에 있는 모든 템플릿 폴더를 내가 관리하겠다.
- `DIRS = [BASE_DIR/ 'templates']` : 'Base_dir'은 django_first 폴더(root project), templates는 그 속의 템플릿 폴더 _ 추가할 디렉토리
  - 

## Template 활용하기

- 템플릿 설정

- 템플릿 태그 : 출력을 위해 사용

  ```django
  {{ lunch_menu }}
  ```

  ```django
  {% for ___ in ____ %}
  {% endfor %}
  ```

- 템플릿 필터

  ```django
  {% lunch_box|length %}
  ```

  

## App 단위 설정하기

- app_name과 urlpattern의 이름을 바탕으로 url을 활용할 수 있다.





## Error 종류

- ModuleNotFoundError : 가상환경 활성화 오류

```python
ModuleNotFoundError: No modeul named 'django'
```

- AttributeError : 





## Git

#### gitignore

> git은 해당 저장소가 있는 폴더의 모든 파일의 변경 사항을 추적

- 폴더 중에서 특정 파일, 폴더 확장자는 git으로 관리하고 싶지 않을 때 사용

  보통 os, 특정 언어, 개발환경(IDE, text editor), 특정 프레임워크에서 버전관리에 사용하지 않는 파일들이 있다. `http://gitignore.io`

```bash
# python 가상환경
venv/
# pycharm
.idea/
# visual Studio Code
.vscode/
```

