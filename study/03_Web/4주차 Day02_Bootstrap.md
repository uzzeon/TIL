# 1. 오전 내용 정리

```html
	.left {
		float: left;
	}
	
	.clear-left {
		clear: left;
	}
	.news-container {
		border: 10px solid hotpink;
	}
	.news-container::after{
		content: "";
		display: block;
		clear: both;
	}
	
	.required::after{
		content: "*";
		color: crimson;
	}

<body>
    <div>
    	<div class="box1 left">A일보</div>
  	  	<div class="box1 left">B일보</div>
    	<div class="box1 left">C일보</div>    
    </div>
    <div class="box2 clear-left">추천 블로그</div>
    
    <laber for="username">username</laber>
    <input type="text" id="username" required>
</body>
```

- news 박스 3개가 float 상태이기에 높이를 가질 수 없음 news-container가 제대로 안잡힘. 

  ▷ 가상의 컨텐츠 요소를 두고 걔한테 clear를 줌 `::after` 

### flex layout

- flex container 안에서는`margin auto`도 가능



# 2. Bootstrap



- 스크립트 파일은 일반적으로 body 닫는 태그 위에 



#### spacing (외우기)

- `.mt-1` 

  ```html
  .mt-1{
  	margin-top: 0.25rem !important;
  }
  ```

  - 0.25rem = 4px

- `.mx-0`

  ```html
  .mx-0{
  	margin-right: 0 !important;
  	margin-left: 0 !important;
  }
  ```

- `.mx-auto`

- `.py-0`

  ```html
  .py-0{
  	padding-top: 0 !important;
  	padding-bottom: 0 !important;
  }
  ```

#### color

#### Display



## Grid System (web design)

> 요소들의 디자인과 배치에 도움을 주는 시스템

- 기본 요소
  - column : 실제 컨테츠를 포함하는 부분
  - gutter: 칼럼과 칼럼 사이 간격
  - container: column들을 담고 있는 공간

- flexbox가 기본으로 제작됨
- 반드시 기억할 것: 12개의 column, 6개의 grid breakpoints



- script 링크를 곡 가지고 와야 한다.

- body

  ```html
  <body>
      <div class="container">
          <div class="row">
              <div class="col-3">1</div>
              <div class="col-6">2</div>
              <div class="col-3">3</div>
          </div>
      </div>
      
  </body>
  ```

  

- Grid system breakpoints: `xs - sm - md - lg - xl - xxl`

- 12개를 넘어가면 column이 다음줄로 넘어가게 된다.
  - `div.col-9+div.col-4.div.col-3` 단축키

- 항상 row를 먼저 잡아준 다음에 col

- `ctrl+alt 방향키(위아래)` multi line selector



```html
<!-- 총 4개>>> 가장 작은 2개, 그 다음은 3개, 그 다음은 4개 (sm, md, lg) -->
<div class="box col-6 col-sm-4 col-md-3">1</div>
<div class="box col-6 col-sm-4 col-md-3">1</div>
<div class="box col-6 col-sm-4 col-md-3">1</div>
<div class="box col-6 col-sm-4 col-md-3">1</div>
```

```html
<h2>김치냉장고 레이아웃</h2>
<div class="row">
    <div class="box col-6">
        <div class="row">
            <div class="col-6">1</div>
            <div class="col-6">1</div>
            <div class="col-6">1</div>
            <div class="col-6">1</div>
        </div>
    </div>
    <div class="box col-6">2</div>
</div>
```

- 김치냉장고 레이아웃에서 작은 칸 4개 만들때, <div class="col-6">1</div>  왜 "col-6"으로 쓰는지 설명을 듣고 싶습니다.. 12칸 중 절반에서 다시 칸을 나누는데 왜 6을 쓰는건가요?

  - 네모네모 구조에서 왼쪽 위로 쌓는 구조... 6 / 6 으로 나누고 오른쪽 6을 다시 각각 6으로 나누는 구조라고 생각하면 된다.

  

- `offset` 띄우고 싶을 때

- Container
  - row
    - col - breakpoint - 전체 12칸 중 숫자 몇칸 가져갈 것인지



- Accordion : 
- Alerts : 알람
- Badge: '가격', '특가 ', 쿠폰'
- Breadcrumb : 사이트 이동 경로를 헨젤과 그래텔의 빵부스러기처럼...
- modal: 갑자기 창 뜨면서 기존 페이지 클릭 안될 때
- navbar: 햄버거 바.. 너비가 줄어들면 어느 순간 글씨 없어지고 navbar로 줄여지는 것



## 기본 원칙

- 코드를 가지고 올때, `class` `stye` 
- 부트스트랩을 사용할 수 있다 = 디자인 프레임워크, 시스템이 있으면 이를 빠르게 잘 활용할 수 있음
- 