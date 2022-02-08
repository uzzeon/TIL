# 2주차 관통PJT

>  파이썬을 활용한 데이터 수집



### 요청과 응답 : HTTP(프로토콜)

- 우리(클라우드)는 주소URL로 요청을 하고, 서버로부터 문서(HTML, XML, JSON 등)를 받음

- 파이썬을 통해 주소로 요청을 보내고 파이썬으로 응답결과를 조작한다.



```python
 $ pip request install
```



### 정보 스크랩 단계

1. 요청 : 정보가 있는 사이트 url을 확인한다

2. 파싱 및 활용

   텍스트 데이터를 HTML 구조로 변환하고 (BeautifulSoup (text → 다른 객체: beautifulsoup객체로))

   원하는 정보를 뽑아서 출력한다.






### BeautifulSoup

> HTML 파일에 있는 데이터를 가지고 오는 파이썬 라이브러리

```python
$ pip install beautifulsoup4
```



### VSC

```python
# 0. 웹 사이트 정보를 가지고 온다.
import requests

# 1-1. 주소
URL = 'https// ___'

# 1-2. 요청
	# response(200): 성공적으로 가져왔다.
response = requests.get(URL).text  #text를 뒤에 붙이니 str으로 변화됨
# print(type(response)) #>> string


# 2-1. BeautifulSoup (text → 다른 객체로)
	# html 파일에 있는 데이터를 가져오기 위해 활용
from bs4 import BeautifulSoup
data = BeautifulSoup(response, 'html.parser')
# print(type(data), type(response)) #> bs4.Beautifulsoup, string

# 2-2. 내가 원하는 정보를 가지고 온다.
	# 선택자
kospi = data.select_one("KOSPI_now (#selector 경로)")
print(kospi.text)
```

```python

URL = '기본 주소만'
params = {
    'name':'michael'
}
response = requests.get(URL, params=params).json()
print(response.get('age'))

```





### API (Application Programming Interface)

> 컴퓨터나 컴퓨터 프로그램 사이의 연결

- 일종의 소트프웨어 인터페이스이며 다른 종류의 소프트웨어에 서비스를 제공

  

- 활용하는 법
  - 요청하는 방식에 대한 이해
    - 인증 방식
    - URL 생성
      - 기본 주소
      - 원하는 기능에 대한 추가 경로
      - 요청 변수 (필수와 선택)
  - 응답 결과에 대한 이해
    - 응답 결과 타입 (JSON)
    - 응답 결과 구조



```PYTHON
#0. IMPORT
import requests

#1. URL 및 요청변수 설정
	# http로 요청을 보낼거야, 주소가 있고 그 주소에 요청파라미터에 값이 있어. baseurl+path 하고 '?'붙인 다음 나머지 params 이어주기 'region=KR&'~~
BASE_URL = 'https://www.themoviedb.org/3'
path = '/movie/now_playing'
params = {
    'api key': '',
    'region': 'KR',
    'language': 'ko'
}

#2. 요청 보내고 보낸 결과 저장
response = requests.get(BASE_URL+path, params=params).json() #json을 주기로 약속했으니 
print(response.status_code, response.url)
data = response.json()

#3. 조작
print(response)


```

