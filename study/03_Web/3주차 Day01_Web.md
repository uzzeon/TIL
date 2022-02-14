# HTML

>  Hyper Text Markup Language 웹페이지를 작성, ""구조화""하기 위한 언어

- Hyper Text : 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트 ex. 위키백과
- Markup Language : 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어`.html` 파일



## 기본구조

- html : 문서의 최상위(root) 요소

- head : 문서의 메타데이터 요소 (문서를 설명할 수 있는 데이터)
  - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등
  
  - 일반적으로 브라우저에 나타나지 않는 내용

  - ex. 사진을 찍었을 때 나오는 날짜, 조리개 값, gps 값 등 사진을 설명하기 위한 데이터
  
    ```html
    <title> : 브라우저 상단 타이틀
    <meta> : 문서 레벨 메타데이터 요소
    <link> : 외부 리소스 연결 요소 (CSS파일, favicon 등)
    <script> : 스크립트 요소 (JavaScript 파일/코드)
    <style> : CSS 직접 작성   
    ```
  
    
  
- body : 문서 본문 요소. 실제 화면 구성 내용

```html
<!DOCTYPE html> #관습적
<html lang="ko">
<head>
    <title>Document</title>
    <meta charset="UTF-8">
    <link href="" rel="">
    <script></script>
    <style>
        p{
            color: black;
        }
    </style>
</head>
<body>
</body>
</html>
```

- head의 예시 : Open Graph Protocol 메타데이터를 표현하는 새로운 규약
  - html 문서의 메타 데이터를 통해 문서의 정보를 전달
  - 메타정보에 해당하는 제목, 설명 등을 쓸 수 있도록 정의
  
  

#### DOM 트리 (Document Object Model)

>  텍스트 파일인 html 문서를 브라우저에서 렌더링 하기 위한 구조

- tap 은 2space

- `alt + b` 웹으로 보여줌

  

#### 요소 (element)

- 시작 태그, 종료 태그 그리고 태그 사이에 위치한 내용으로 구성
  - 태그(element, 요소)는 컨텐츠를 감싸는 것으로 그 정보의 성격과 의미를 정의
- **★ 내용이 없는 태그들( 닫는게 없음) : br (줄바꿈), hr (수평선), img (이미지_링크주소를 속성의 값으로 ), input, link, meta(관련된 것을 속성 값으로) ▶ 객관식 가능 **
- 요소는 중첩(nested)될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화 (DOM)
  - 여는 태그와 닫는 태그의 쌍을 잘 확인해야 함
    - 오류를 반환하는 것이 아닌 그냥 레이아웃이 깨진 상태로 출력되기 때문에 디버깅이 힘들..



#### 속성(attribute)

```html
<a href="https://google.com"></a> #구글로 연결. 파란색은 속성명, 빨간색은 속성값
```

- href는 속성: 공백은 없고, 쌍따옴표 사용
- 속성을 통해 태그의 부가적인 정보를 설정할 수 있음
- 요소는 속성을 가질 수 있으며 경로나 크기와 같은 추가적인 정보를 제공
- 요소의 시작 태그에 작성하며 보통 이름과 값이 하나의 쌍으로 존재
- global 속성: id, class, style, title, tabindex

  - id : 고유 식별자 지정 (문서 전체에서 유일)
  - class: 공백으로 구분된 해당 요소의 클래스의 목록, 요소들을 공통적으로 묶어가는
  - data-*
  - style: inline 스타일
  - title: 요소에 대한 추가 정보 지정
  - tabindex: 요소의 탭 순서
  

```html
<!DOCTYPE html>
<html lang="en">
<head>
</head>
<body>
    <!-- 이것은 주석입니다. -->
    <h1>나의 첫번째 html</h1>
    <p>이것은 본문입니다.</p>
    <span>이것은 인라인요소</span>
    <a href="https://www.naver.com">네이버로 이동!!</a>
</body>
</html>
```



#### 시맨틱 태그

- 기존 영역을 의미하는 `div 태그`를 대체하여 사용 
- 분석을 편하게 하려고.. header(머리말 부분), nav(내비게이션), aside(사이드에 취한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠), section(문서의 일반적인 구분, 컨텐츠의 그룹을 표현), article(문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역), footer(문서 전체나 섹션의 푸터) 등

| 태그              | 설명                                                       |
| ----------------- | ---------------------------------------------------------- |
| <a></a>           | href 속성을 활용하여 다른 url로 연결하는 하이퍼링크 생성   |
| <b></b>           | 굵은 글씨 요소                                             |
| <strong></strong> | 시맨틱_ 실제 스크린리더도 강조해서 읽음 ★ <i>와 비교하기   |
| <i></i>           | 기울임 글씨 요소                                           |
| <em></em>         | 시맨틱_ 실제 스크린리더도 강조해서 읽음 ★ <br>과  비교하기 |
| <br></br>         | 텍스트 내에 줄 바꿈 생성                                   |
| <img></img>       | src 속성을 활용하여 이미지 표현                            |
| <span></span>     | 의미 없는 인라인 컨테이너                                  |

- 그룹 컨텐츠

| 태그                      | 설명                                                         |
| ------------------------- | ------------------------------------------------------------ |
| <p></p>                   | 하나의 문단 (paragraph)                                      |
| <hr>                      | 문단 레벨 요소에서의 주제의 분리를 의미하며 수평선으로 표현됨(a horizontal rule) |
| <ol></ol>                 | 순서가 있는 리스트 (ordered)                                 |
| <ul></ul>                 | 순서가 없는 리스트 (unordered)                               |
| <pre></pre>               | html에 작성한 내용을 그대로 표현. 보통 고정폭 글꼴이 사용되고 공백문자를 유지 |
| <blockquote></blockquote> | 텍스트가 긴 인용문. 주로 들여쓰기를 한 것으로 표현됨         |
| <div></div>               | 의미없는 블록 레벨 컨테이너                                  |



#### Table

> 각 영역을 명시하기 위해 <thead><tbody><tfoot>요소를 활용

- 행은 `th` 로 묶고..
- <caption>을 통해 표 설명 또는 제목을 나타냄
- 태그 기본 구성 
  - thead: tr > th
  - tbody: tr > td
  - tfoot: tr > td
  - caption
- `(tr>th*3)*2` 를 누르면 한번에 뜸. 핵편리
- `colspan="2"` 열로 2칸 먹을래 / `rowspan`



#### form ★★

- `<form>` 은 정보(데이터)를 서버에 제출하기 위한 영역
- 기본 속성
  - action: form을 처리할 서버의 url
  - method: form을 제출할 때 사용할 http 메서드 (GET 혹은 POST)
  - enctype: method가 post인 경우 데이터의 유형
    - application/x-222-form-urlencoded : 기본값
    - multipart/for-data : 파일전송시
- 구글설문 폼 을 생각해볼것
- `<label>` : `label for ="name"` 은 `id="name"`이랑 연결되어있을 때 label을 오롯이 사용할 수 있음
- `checkbox` 는 복수 선택 가능 / `radio button` 은 하나만 선택 가능 ▷ `name`이 동일하게 부여되어있어야 한다.
  - 서버에 어떤 이름으로 value를 보낼지 직접 지정해야 한다.

- `autofocus` 는 바로 커서가 들어가 있음. 없으면 내가 입력칸을 누른다음 작성해야 함



#### input

- 다양한 타입을 가지는 입력 데이터 유형과 위젯이 제공됨
- <input> 대표적인 속성
  - name: form control에 적용되는 이름(이름/값 페어로 전송됨)
  - value: form control에 적용되는 값(이름/값 페이로 전송됨)
  - required, readonly, autofocus, autocomplete, disabled 등
  - `<input type="text" name="q">` 



##### input label

- label을 클릭하여 input 자체의 초점을 맞추거나 활성화 시킬 수 있음

```html
<label for="agreement">개인정보 수집에 동의합니다.</label>
<input type="checkbox" name="agreement" id="agreement">
# <input> id 속성을, <label>에는 for 속성을 활용하여 상호 연관을 시킴
```



###### input 유형

- text : 일반 텍스트 입력
- password : 입력 시 값이 보이지 않고 문자를 특수기호(*)로 표현
- email : 이메일 형식이 아닌 경우 form 제출 불가
- number : min, max, step 속성을 활용하여 숫자 범위 설정 가능
- file : accept 속성을 활용하여 파일 타입 지정 가능
- 동일 항목에 대해서는 name을 지정하고 선택된 항목에 대한 value를 지정해야 함
  - `checkbox` : 다중 선택
  - `radio` : 단일 선택

- 다양한 종류의 input을 위한 picker 제공
  - `color picker`, `date picker`







## Q&A

- name과 value
  - name은 변수의 이름 (parameter)
  - value는 사용자 입력값(직접 입력)
  
- heaer, section, footer, caption 모두 구분하기 위함 <div>와 차이가 없는데 의미를 알 수 있게 표기한 것

- 이미지 태그

  ```html
  <img src="" width="" height="" alt="">
  ```

  - src 속성은 이미지 파일 이름을 지정하는 것 (파일의 상대경로나 절대경로를 입력)
  - alt속성은 웹 상에서 이미지가 나오지 않을 경우 해당 이미지가 어떤 이미지인지 확인하게끔