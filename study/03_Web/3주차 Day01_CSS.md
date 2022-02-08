# 1. CSS

> cascading style sheets

- 선택자를 통해 스타일을 지정할 HTML 요소를 선택
- 중괄호 안에서는 속성과 값, 하나의 쌍으로 이뤄진 선언을 진행
- 각 쌍은 선택한 요소의 속성, 속성에 부여할 값을 의미



### 용어 정리

- 선택자(selector) : html 문서에서 원하는 것을 선택해서 스타일을 지정하기 위함
  - 기본 선택자 
  - 결합자(combinators)
  - 의사 클래스/요소
- 선언(declaration): 어떤 속성이랑 값을 매칭시켜서

```html
h1 {
	color: blue;
	font-size: 100px;	
}

h1 : 선택자 / 2번째 줄: 선언 / font-size : 속성 / 100px : 값
```



### 정의 방법

- 인라인: 해당 태그에 STYLE 속성을 활용 → 디버깅이 어려움
- 내부참조: 어떤 것을 선택한 다음
- 외부참조: CSS 파일을 별도로 만든다음 링크태그로 연결시킴 → 제일 많이 쓰임



### 선택자(selector) ★

- 전체 선택자 `*` : 모든 선택자를 지정
- 요소 선택자: html 태그 직접 선택. 지정을 한다면(더 좁은 범위 지정)  그걸로 ex. `h1` , `p`
- 클래스 선택자: `.class`
  - 클래스는 `.`으로 표현 ex. `.green {}` 
- id 선택자: `#id`



- 자식 결합자:

  - `.box > p`  클래스 box 자식 p _ 직접적으로 한단계 밑인 애만 지정
  - `div > .children` div태그 바로 밑에 있는 children 클래스를 가진 것

- 자손 결합자: 클래스 box 모든 하위 요소 중 p

  - `div .baby` div 태그 하위 모든 baby 클래스를 가진 것

- 형제 결합자 : `p ~ span` 이라하면 p 뒤에 나오는 span 들을 의미 (같은 level)

  ​						`p + span` 이라하면 p 바로 뒤에 붙어있는 span



#### 기본 선택자 우선순위

- `* * < element(tag) < .class < #id` < 인라인 <`!important` 
- id는 문서에서 하나, class는 문서에서 여러 번
- id가 puple, class가 green, h1은 violet, *는 red일 경우: id는 퍼플!
- ☆ 점수가 같으면 CSS 선언된 순서에 따라 지정_ 더 아래에 선언된 것이 우선 (not 적용순서)
- **일반적인 스타일링시 사용되는 것은 : class 선택자** - class를 부여하고 정의하는 것이 기본!



### CSS 상속

- 속성 중에서 상속이 되는 것과 상속되지 않는 것이 있다.
- 상속o : text관련 요소(font, color, text-align), opacity, visibility → style 상속 o
- 상속x :  box model 관련 요소 (border, box-sizing) & position 요소(top, bottom) 등 



## CSS 기본 스타일

### 1. 크기 단위

- px (픽셀), % (백분율)
- em : 바로 위, 부모 요소에 대한 상속의 영향을 받음 (부모에 따라 너무 많이 바뀜)
- rem : 바로 위, 부모 요소에 대한 상속의 영향을 받지 않음 (많이 씀) 
  - ★ em과 rem 구별하기 


 	ul 이 24px이면, 

​	1.5em은 부모(ul) 대비 1.5배 : 36px

​	1.5rem은 root(보통 16픽셀) 대비 1.5배 : 16의 1.5배 = 24px

☆ 10rem 은 16px * 10 = 160px



- viewport: 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨
  - vw, vh,



### 2. 색상 단위

- RGB 색상 / HSL / APLHA(투명도) / 색상 키워드



### 3. 문서 표현

- 텍스트

---

---



# 2. CSS BOX MODEL (레이아웃)

- 모든 요소는 네모네모 '멈뭄멈뭄'

- 구성

  - Content 가장 안쪽. 실제 내용

  - Padding : 테두리 안쪽의 내부 여백, 이미지는 padding까지 적용

  - Border: 테두리 영역

  - Margin : 테두리 바깥의 외부 여백. 배경색 지정 불가

    ```html
    .margin-padding{
    	margin: 10px;
    	padding: 30px;
    }
    # margin은 상하좌우 10픽셀, padding은 상하좌우 30픽셀
    
    .margin-2{
    	margin: 10px 20px;
    }
    # 상하는 10픽셀, 좌우는 20픽셀
    
    .margin-3{
    	margin: 10px 20px 30px;
    }
    # 상 10, 좌우 20, 하30
    
    4개인 경우: # 상 오 하 좌 (시계방향)
    ```



- box model의 너비를 지정  (`box-sizing`) ★

  > 너비를 지정할때 기준을 무엇으로 할 것인지?

  - content- box (기본 값)

  - border-box (일반적인 선호)

    → 이 경우 box-sizing을 border-box으로 설정해야 한다.

    

# 3. CSS Display

> display에 따라 크기와 배치가 달라진다.
>
> 기본 위치가 좌측 상단에



#### block 과 display 꼭 알기

- display: block 
  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로 폭을 차지한다 (한 줄을 다 먹음)
- display: inline
  - 기본 영역은 content
  - 줄 바꿈x
  - content 너비만큼 가로 폭을 차지한다
  - width, height, margin-top, margin-bottom 등을 지정할 수 없다. _ margin-left, margin-right는 줄 수 있다.



- 블록 레벨 요소와 인라인 레벨 요소

  - 블록레벨요소: div, ul, ol, li, p, hr, form 등
  - 인라인 요소: span, a, img, input, label, b, em, i, strong 등

  

- block: 너비를 가질 수 없다면 자동으로 부여된 margin

  - 중간정렬하는 법: `margin-right: auto; margin-left: auto;` (남은 영역을 배치함으로써)

  

- display: inline-block 
  - blcok과 inline 레벨 요소의 특징을 모두 가짐
  - inline 처럼 한 줄에 표시 가능하고, block 처럼 width, height, margin 속성을 모두 지정할 수 있음
  - 으로 바꿔서 1000픽셀 가지게끔... 

- display: none (영역을 차지하지도 않음. 숨겨짐)

- display: hidden (공간은 차지하지만 화면에서만 보이지 않음)



# 4. Display Position

> 문서 상에서 요소의 위치를 지정

- static: 모든 태그의 기본 값(기준 위치)
  - 일반적인 요소의 배치 순서에 따름 (좌측 상단)
  - 부모 요소 내에서 배치될 때에는 부모 요소의 위치를 기준으로 배치 됨

```html
.test{
	position: relative;
	left: 10rem;
	top: 10rem;
}
```

- relative: 상대 위치	
  - 자기 자신의 static 위치를 기준으로 이동 (normal flow 유지)
  - normal position 대비 offset (내 원래 위치 기준)
- absolute: 절대 위치
  - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음 (normal flow에서 벗어남)
  - static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동
- fixed: 고정 위치
  - normal flow에서 벗어남
  - viewport를 기준으로 이동 (내가보고 있는 브라우저 화면 기준)



### CSS 원칙

- CSS 원칙 Ⅰ, Ⅱ : Normal flow
  - 모든 요소는 네모, 좌측 상단에 배치
  - display에 따라 크기와 배치가 달라짐
- CSS 원칙 Ⅲ
  - position으로 위치의 기준을 변경
    - relative / absolute / fixed