# [PJT] 반응형 웹페이지 구성



## 1. 미디어 쿼리(Media Query)

> CSS에서 @media 키워드를 활용하여 브라우저 및 디바이스 등 환경에 따라 CSS를 적용할 수 있는 방법

- media-type: all, print, screen, speech
- media-feature-rule: orientation, width, height 등



### html에 작성

`!+tab` 

1번: `head` 부분에 `link css`

2번: body 부분에 작성

```html
# 1번 (link rel="stylesheet" href="01_media_query.css" ) 
# 2번 
  <h1>Media Query</h1>
  <h2>width!</h2>
  <h3>min-width 700px, max-width 600px</h3> 
	# 700px 이상인 경우, 다크카키 / 600px 이하인 경우, 핑크색 / 
	# 600~700px은 검정색(기본값)
  <h4>무지개</h4>
  <h5>500 and 500</h5>
  <p>500, 500</p>
```

3번: 



### query 파일

`01_media_query.css` 파일 생성

media_query.css에 작성

```html
@media (orientation: landscape) {  #가로모드 (너비>높이)
  hi {
	color: green;
  }
}

@media (orientation: portrait) { #세로모드 (높이>너비)
  hi {
    color: red;
  }
}

@media only print {
  * {
	color: black !important;
  }
}

/* 특정 너비일때만 적용 */
@media (width: 300px) { #개발자도구에서 네모디바이스 아이콘> 특정디바이스 크기
  h2 {
	color: cadetblue;
  }
}

@media (min-width: 700px) { 
  h3 {
	color: darkkhaki;
  }
}

@media (max-width: 600px) { 
  h3 {
	color: fuchsia;
  }
}

@media (min-width: 500px) { 
  h4 {
	color: red;
  }
}

@media (min-width: 600px) { 
  h4 {
	color: orange;
  }
}

@media (min-width: 700px) { 
  h4 {
	color: yellow;
  }
}

@media (min-width: 800px) { 
  h4 {
	color: green;
  }
}

/* 조건 */
/* 두 조건이 모두 만족할 때 : and */
@media (max-height: 500px) and (max-width: 500px) {
  h5 {
	color: rosybrown;
  }
}

/* 두 조건 중 하나라도 만족할 때 : or */
@media (max-height: 500px), (max-width: 500px) {
  p {
	color: palegreen;
  }
}
```



### bootstrap breakpoints (시험에 꼭 나옴)

`x-small` 은 없어짐

`col-12 col-sm-12 col-md-6 col-lg-6 col-xl-4 col-xxl-4` 이렇게 일일이 할 필요x

`.col-sm-6 .col-md-4 .col-lg-3` : 768px까지는 6칸, 992px까지는 4칸, 그 뒤는 3칸



### HTML / CSS 스타일 가이드 예시

- html에서는 `=` 붙여서 작성하기
- [구글 가이드](https://google.github.io/styleguide/)
- [네이버NHN]()
- 구글] `id` 는 자바스크립트를 위한 공간. styling을 하려면 `class`를 써라



- BEM 방법론 (Block Element Modifier)
  - Block: 어디서나 쓸 수 있는 개체, 재사용 가능, 기능적으로 독립적인 개체
  - Element: block의 구성요소, 독립적으로 활용되지 않고 블록 내에서만 사용
  - Modifier: block, element의 속성_ 다른 형태나 행동(disabled, checked)



 - `.block`
 - `.block__element`
 - `.block-mdifier block__elem--modifier`

```html
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
	class="form__submit form__submit--disabled"
    type="submit" />
</form>
```



### modifier 활용해서 nav bar 만들기

1. HTML 파일 + CSS 파일 만들기

2. HTML 작성해서 link

   ```HTML
   <link rel="stylesheet" href="02_BEM.css">
   
   <body>
     <!-- B: main-nav -->
     <nav class="main-nav" aria-label="Main">
       <!-- E: logo -->
       <div class="main-nav__logo">
         SAMSUNG
       </div>  
       <ul class="main-nav_list">
         <li class="main-nav__item">
           <a href="#" class="main-nav__link">Home</a>  
         </li>    
         <li class="main-nav__item">
           <a href="#" class="main-nav__link">Work</a>  
         <li class="main-nav__item">
           <a href="#" class="main-nav__link">About us</a>  
       </ul>
     </nav>
   ```

   ```html
   <body>
       nav>ul>li*3
   </body>
   ```

   

3.  logo SAMSUNG과 나머지 nav_item을 같은 줄로 위치  => CSS에서 'flex' 사용

   ```css
   .main-nav {
       display:flex;
       justify-content: space-between;
   }
   
   .main-nav__list {
       display: flex;
       margin: 0;
       padding: 0;
   }
   
   .main-nav__item {
       margin: 0 0.5rem; #상하- 좌우 순서
       list-style: none;
   }
   
   .main-nav_link {
       text-decoration: none;
   }
   ```





## 2. 웹페이지 추가 구성 요소



### Favicon (favorite icon)

> 사이트를 대표하는 아이콘으로 브라우저 주소창, 탭, 북마크 바 등에 표시됨

```html
<head>
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-con.png">
</head>
```

- Favicon 생성기 [생성기](https://favicon.io/)

   - 사이트에서 만들어 다운받고

   - 페이지에서 코드 복사

   - images 폴더 만들어서 거기에 넣은 다음에 

   - `icon_font.html` 만들어서 `! + tab` → link tag 붙여넣기 : href 앞에 `images/` 폴더 경로 추가

     ```html
     <link rel= ....... href="images/favicon-..."
     
     <!-- 상대경로를 가져갈 수 있게끔 앞에 / 제거해야 함. `/images` (x) -->
     ```



### Icon

> 일반적인 웹 사이트에서 활용되는 아이콘은 이미지가 아닌 i태그로 구성되어 있음

- `Font Awesome` _ kit 다운보다는 cdn 활용 >> icon 주소 복붙

  ```html
  <head>
      ...
    <link rel=......   cdn 붙여넣기>
  </head>
  <body>
    <h1>내 홈페이지</h1>  
      <i class= ... style="color: orange; font-size: 3rem;"></i> >>> 복붙 
  </body>
  ```

  - style 활용해서 사이즈, 색상 변경 가능
  - 또는, head에서 `hover`

  ```html
  <head>
    <style>
        .fa-python:hover {
            color: green;
        }  
    </style>  
  </head>
  <body>
    <i class="fa-brands fa-python"></i>
  </body>
  ```



### Font

- Google Fonts 활용하기 

  ```html
  <head>
    <link> 사이트에서 복붙    
   
    <style>
        body {
          font-family: 'Noto Sans KR', sans-serif; 복붙
        }
        
        h1 {
          font-family: 'Gugi', cursive; 복붙
        }
        
    </style>  
  
  </head>
  
  <body>  
  </body>
  ```

  - 폰트가 로드가 안될 경우 순차적으로 쓴것 
    - `sans-serif: 고딕` `serif: 명조`



## 3. Bootstrap 으로 웹 개발 - SCSS



- `SCSS`: css를 만들기 위한 도구로 변수, 상속, mixin 등의 개념을 통해 가독성과 재사용성을 높여 유지보수가 쉽도록 함
- `코드 경량화(minify)` : 모든 소스코드는 네트워크를 통해 전소되므로 더욱 빠른 다운로드를 위해 파일의 공백 및 개행 문자를 제거하여 경량화

- `reboot.css / reset.css / normalize.css` : 스타일을 기본으로 초기화해서 사용할 수 있도록하는 행위...





### 4. [실습] Bootstrap 활용한 레이아웃 구성

[링크](https:// getbootstrap.com/docs/5.1/examples/carousel/)



1. html 문서 만들고, 링크 cdn

   - css 랑 js 모두 복사해야 한다. css는 <head>에, js <body>에 복붙해넣기

2. nav 스타일 중 마음에 드는 것 복붙

   - navbar-dark, bg-dark 등으로 변경
   - `active class` 내가 현재 있는 위치를 나타내는 class_ ex. class=" 여기에 active"
   - sticky top은 마진을 안줘도 되는데 fixed top은 normal flow를 벗어나 말려올라간다. => sticky 더 많이 사용

3.  carousel 스타일 복붙

   - image 넣기

4. 반응형 카드

   ```html
   <body>
     <!-- Grid System-->
     <h1>냉장고 제품</h1>
       
     <!-- .container > .row > .col -->  
     section.container>div.row>article.col*4
       <!--article 안에 card를 넣어주면 된다-->
   </body>    
   ```

   - 기본적으로 `article class="col-sm-6 col-md-4 col-lg-3 my-1"` 반응형 + 마진 간격



## Modal ux

- components > modal

  - `data-bs-target="#exampleModal"` `id="exampleModal"` 

    - ★`data-bs-target` & `id` 가 일치해야 한다.
    - ★data-bs-target에서 `#` 반드시 있어야 한다.
    - ★`data-bs-toggle="modal"` 이 있어야 한다.

    

  - modal 코드 그대로 복붙해서 ☆★ `body 태그 안에` 넣어주기 

    - position: fixed... top level

  - 버튼 눌렀을 때 동작하는 것이므로 버튼과 연결 작업

    ```html
    data-bs-toogle="modal" data-bs-target="#exampleModal"
    ```

    - modal ... 버튼에서 위 코드 복사해서 article. card <a> 뒤에 붙여넣기

      ```html
      <article>
        <div>
          <img>
          <div class="card-body">
            <h5></h5>
            <p></p>
            <a href="#" class="btn btn-primary" data-bs-toogle="modal" data-bs-target="#exampleModal"> Go somewhere</a>
          </div>
        </div>
      </article>
      ```

    - modal의 id 변경 작업 = 각각 & card button에서 data-bs-target 부분 똑같이 변경

    - CF. modal에서 div class 하위 클래스로 폼 복붙해도 되고... 위치만 잘 찾아서 넣어주기 

  

