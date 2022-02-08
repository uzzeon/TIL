## chrome dev tools

- 검사 > 
  - `styles`
  - `computed` (현재 적용되고 있는 애)
  - `.cls` 클래스 추가해보기

- 마우스를 올렸을 때 변경되는 애 : `:hov` `hover`



- 검색할 때 `CSS` 앞에 붙여서 구글링하기



# 실습 풀이



## 1번 문제

- position 지정

  `absolute` 부모의 위치를 기준으로_ 아예 집을 나감. 원래있던 공간은 다른 밑에 있는 애들이 채운다.

  `relative` 원래의 위치를 기준으로_ 내 원래 위치에서 이동해있는 거뿐

  

- big box에 `position:relative'라고 해야 함!

  큰 박스를 기준으로 배치시키고 싶다면 큰 박스에 relative를 줘야한다.



## 2번 문제



- 테두리: line-style `dahsed` `dotted`
- card 가운데 정렬 : block 요소이기 때문에 `margin: 0 auto` 

```html
.card-header {
  padding: 18px;
  margin: 18px; 
}
# 둘은 background color를 줄때 다르게 나타난다. margin은 이상하게 나옴
```

- 이미지는 대체요소 : 기본적으로 display는 inline이지만 width, height 등을 지정할 수 있다.
  - `object-fit: cover` 이미지 비율을 살릴 수 있다
- '수직 가운데 정렬' 
  - `vertical-align: middle` 은 table에서..
  - `line-height: 35px;` 라인 박스의 높이를 지정한다. 텍스트 수직 가운데 정렬 ★★



##### 그림과 그림설명글 부분 사이에 여백 없애기

```html
<span>123 안녕하세요!</span>
<p>안녕하세요?</p>
```

- baseline이 있으면 그 밑에 살짝의 영역이 있다. (영어에서 p, q)
- 1번째 방법: .card-img의 `display: block;` 으로 
- 2번째 방법: .card-img의 margin을 마이너스로 주기
- 3번째 방법: .card-header의 `font-size: 0;` 으로  (baseline 이런 개념이 필요없어지면서)
- 4번째 방법: .card-header에서 `line-height: 0;` 으로



- 본문 중 특정 단어를 강조하고 싶다면? 마크업을 하고 선택자로 잡아서 스타일!
  - `span` 을 줘서 <span style=""> 이런식으로... 



## 3번 문제

- a 태그 기본속성 제거 : `text-decoration: none`

- 원형으로 깎기: `border-radius: 50%`

- position : absolute 하려면 부모도 생각해야한다.

  ```html
  .compare {
  	position: relative;
  }
  
  .compare-image {
  	position: absolute;
  }
  ```

- 완전히 정중앙으로 위치시키기

  - 기준점(박스의 좌측상단)이 중앙에 위치 (원의 중점은 그 기준점보다 밑에 있으니깐)

    => 위치를 해당 너비, 높이의 절반만큼 이동

    전체가 100px이면 margin-top: -50%, margin-left: -50% (올라간 것처럼 보이게끔)
  
  - `transform: translate(-50%, -50%)` (직접 계산하지 않고도 지정 가능)





docs.emmet

- `! + tab`

- `table>(thead>tr>th*3)+(tbody>tr>td*3)`
