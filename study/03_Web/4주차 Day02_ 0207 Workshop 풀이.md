# 4주차 Day02_ 0207 Workshop 풀이 

- user agent stylesheet : chrome 기본 설정
- 개발자 도구를 꼭 확인해야! 공식문서 많이 확인해봐야!



### Nav

####  (1) 배치

- 상황) `ul` 태그가 block 요소라소 `a` 태그 밑에 배치되어 있음

- 해결 방법

  - Inline으로 만들기 (어려움) : `d-inline` 한 줄 배치는 가능한데 좌측, 우측으로 배치시키는 것이 어렵기 때문

  - `a` 태그와 `ul` 태그를 각각 `div`(부모태그)로 묶고 이것을 좌우측으로 배치하는 방법

  - Float 

    ```html
    <nav>
        <a href="#" class="float-start">
            <img src="" alt="">
        </a>
        <ul class="flaot-end">
            <li></li>
        </ul>
    ```

    - 문제점

      

  - Flex : 

    - ① 부모 요소에 컨테이너로 지정 : **Flex-direction의 기본이 `row` **라서, 한 줄로 보이게 되는 것!

    ```html
    <nav class="d-flex"></nav>
    ```

    - ② 양 끝 배치: main-axis가 row니까 `justify-content` 메인축 배치를 사용 _ justify-content-between

    

#### (2) 목록 스타일링

- list-unstyled 
- text-decoration-none : 상속x. a태그에 일일이 적용해줘야 한다



#### (3) 가로 배치

- `d-inline` 적용한 후에 `line-height` 맞추기
- 부모 영역(ul)에 `d-flex` 주고 수직, 수평 배치 `justify-content-around align-items-center`
- 사이 간격 조절 : `mx-3`은 좌우측 margin 1rem씩



- nav bar를 만들때 왜 <ul><li> 태그로 만드냐? 목록을 의미하는 것이기 때문에 이렇게 만드는게 일반적!
- `gnb` global nav bar (해당 홈페이지 전체에서의 nav bar이다)



## Header

```html
<h1>Cinema<br> Community</h1>
```

####  (1) 수직, 수평 가운데 정렬

- ① 부모 요소에 `flex` :  `justify-content-center align-items-center`
- ② 축을 바꾼다. `flex-column`
- ③ text align을 조정 : `text-center`



### Section

####  (1) 정렬

- ① 영역 전부를 FLex로 가져갈 것이냐 ② 그림부분만 flex로 가져갈 것이냐

  ```html
  <section>
      <h2 class="text center">Used Skills</h2>
      <article class="d-flex justify-content-around">
      	<div></div>
          <div></div>
      </article>
  ```

