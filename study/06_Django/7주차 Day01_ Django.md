# 7주차 Day01_ Django

> high-level Python Web framework



- 클라이언트 / 서버 / 요청 / 응답
  - 클라이언트: 네트워크 시스템을 통해 서버에 접속할 수 있는 프로그램, 디바이스
  - 서버: 네트워크 환경을 통해 정보를 제공_ Django로 서버를 구축함



- 가상환경 생성 및 활성화 → Django 설치 → 프로젝트 생성 → 서버 켜서 로켓 확인하기 → 앱 생성 → 앱 등록



## 1. Web framework

- Static web page (정적 웹 페이지)

  - 서버에 미리 저장된 파일이 사용자에게 그대로 전달되는 웹페이지
  - 정적 웹페이지에 대한 요청을 받은 경우, 서버는 추가적인 처리 과정 없이 클라이언트에게 응답을 보냄
  - 모든 상황에서 모든 사용자에게 동일한 정보를 표시
  - html, css 등이 사용됨

- Dynamic web page (동적 웹 페이지)

  - 요청을 받은 경우, 서버는 추가적인 처리 과정 이후 클라이언트에게 응답을 보냄
  - 방문자와 상호작용하기 때문에 페이지 내용이 그때그때 다름
  - python, java, c++ 등이 사용됨

  

- Framework

  - 재사용할 수 있는 수많은 코드를 프레임워크로 통합함으로써 개발자가 새로운 어플리케이션을 위한 표준 코드를 다시 사용하지 않아도 같이 사용할 수 있도록 도움

- Framework Architecture
  - MVC Design Pattern (model-view-controller)
  - Django는 MTV Pattern 이라고 부른다.

- MTV Pattern

  - Model : 데이터베이스의 기록을 관리, 추가, 수정, 삭제
  - Template : 파일의 구조나 레이아웃을 정의, 실제 내용을 보여주는데 사용 (presentation)
  - View: HTTP 요청을 수신하고 HTTP 응답을 반환, Model을 통해 요청을 충족시키는데 필요한 데이터에 접근, template에게 응답의 서식 설정을 맡김

  - 요청을 받음 → view : 응답을 줌 (최종적으로) / template을 가져오거나 / model 과의 상호작용을 함



- 가상환경 만들고 활성화

  ```python
  $ python -m venv venv
  $ source venv/Scripts/activate
  ```

  - VS CODE : ctrl + shift+ p



```python
$ python manange.py startapp articles

```



## 2. Django Intro

- Project : application의 집합, 앱은 여러 프로젝트에 있을 수 있음 

- Application: 앱은 실제 요청을 처리하고 페이지를 보여주고 하는 등의 역할을 담당

  - 일반적으로 앱은 하나의 역할, 기능 단위로 작성함

  

- 앱 등록 :  앱은 반드시 생성 후 등록

  - setings.py 에서 `Installed_apps`에 등록
  - 보통 local apps > third part apps > django apps (원래 있던 앱) 순서로 등록하는 걸 추천



## 3. 요청과 응답

> 코드 작성 순서 : URL -> VIEW -> TEMPLATE (데이터의 흐름대로 작성하는 것)

### URL 

- URL :`/admin` 

```python
path('admin/', admin.site.urls)
# 요청 주소에 admin이 있어서 호출됨. 두번재꺼 'admin.site.urls'가 호출됨
# path() 함수는 admin에 대해 응답하는 함수
```



### View 

-  `index` 요청

```python
from articles import views

urlpatterns= [
    path('admin/', admin.ste.urls),
    path('index/', views.index),
]
```

```python
# views.py

from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
	# render()는 첫번째 인자로 request를 받음
    # render()는 template을 만들어서 return해준다.

```



### Template

- 파일 경로의 기본 값은 app폴더 안의 templates 폴더로 지정함



### Settings.py

- LANGUAGE_CODE = 'ko-kr'
- TIME_ZONE = 'UTC'
- USE_I18N = 국제화. 번역시스템
- USE-L10N = 지역화.
- USE_TZ = TRUE



## 4. TEMPLATE

> 데이터 표현을 제어하는 도구이자 표현에 관련된 로직

- DTL : Django Template Language 
  - 파이썬 코드로 실행되는 것은 아니다.
  - built-in template system
  - 프레젠테이션을 표현하기 위한 것



- Variable

  - `render()`를 사용하여 views.py에서 정의한 변수를 template 파일로 넘겨 사용하는 것

  - 변수명은 영어, 숫자, 밑줄의 조합으로 구성할 수 있으나 밑줄로는 시작할 수 없음

  - render()의 세번째 인자로, {'key':value}와 같이 딕셔너리 형태로 넘겨주며 여기서 정의한 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨

  - ex. `{{ name }}`

    ```python
    def greeting(request):
        foods = ['apple', 'banana', 'coconut',]
        info = {
            'name': 'Alice',
        }
        context = {
            'foods': foods,
            'info': info,
        }	#일반적으로 key, value 값을 똑같이 맞춘다. 왼쪽의 key이름을 써주는 것
        return render(request, 'greeting.html', context)
    ```

    ```python
    # greeting.html 에서
    <p>저는 {{ info.name }} 입니다.</p>
    <p>제가 가장 좋아하는 음식은 {{ foods }} 입니다.</p>
    <p>사실 가장 좋아하는 음식은 {{ foods.0 }} 입니다.</p>		# 인덱스 접근
    ```

    

- Filters : 표시할 변수를 수정할 때 사용

```python
{{ variable|filter }}
## ex. {{ info.name|lower }}
```

```python
#views.py
import random

def dinner(request):
    foods = ['족발', '햄버거', '치킨', '초밥']
    pick = random.choice(foods)
    context = {
        'pick': pick,
    }
    return render(request, 'dinner.html', context)
```



- Tags

  - 출력 텍스트를 만들거나 반복, 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
  - 일부 태그는 시작과 종료 태그가 필요

  ```html
  <ul>
   {% for food in foods %}
      <li>{{ food }}</li>
    {% endfor %}
  </ul>
  ```



- Comments
- `{# #}` 한 줄짜리 주석
- `드래그 + ctrl + /` 여러 줄 주석처리



#### TEMPLATE Inheritance 템플릿 상속 (이부분 유라 다시 보기)

```django
{% extends '' %} # 제일 위에 선언. 템플릿 최상단에 작성

{% block content %} {% endblock %}
```



- `BASE_DIR` : 장고 프로젝트를 가지고 있는 최상단 폴더



## TIP

- 구글 검색시		ex. `django settings language-code`





## 정리

- Django의 기본구조 : MTV (Model - Template - View) 패턴
  - model은 DB / template 은 보여지는 화면 / View는 조작, 처리

- 요청 처리 흐름: URL → VIEW → TEMPLATE
  - URL : 웹 서비스 모든 경로 + 처리할 view 지정
  - VIEW: 요청 정보 'request' + 처리 + 응답을 위해서 'render'
  - TEMPLATE: 순수 html x => django template language



