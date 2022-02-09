# Flexbox Froggy

[Flex Froggy](https://flexboxfroggy.com/#ko)



### Justify-content 

> 개구리들을 가로 방향으로 배치, 재정렬

```html
flex-start: 요소들을 컨테이너의 왼쪽으로 정렬합니다.
flex-end: 요소들을 컨테이너의 오른쪽으로 정렬합니다.
center: 요소들을 컨테이너의 가운데로 정렬합니다.
space-between: 요소들 사이에 동일한 간격을 둡니다.
space-around: 요소들 주위에 동일한 간격을 둡니다.
```



### Align-items

> 개구리들을 세로 방향으로 배치, 재정렬

```html
flex-start: 요소들을 컨테이너의 꼭대기로 정렬합니다.
flex-end: 요소들을 컨테이너의 바닥으로 정렬합니다.
center: 요소들을 컨테이너의 세로선 상의 가운데로 정렬합니다.
baseline: 요소들을 컨테이너의 시작 위치에 정렬합니다.
stretch: 요소들을 컨테이너에 맞도록 늘립니다.
```



### Flex-direction

> 컨테이너 안에서 요소들이 정렬해야 할 방향을 지정

```html
row: 요소들을 텍스트의 방향과 동일하게 정렬합니다.
row-reverse: 요소들을 텍스트의 반대 방향으로 정렬합니다. (ex) a b c → c b a
column: 요소들을 위에서 아래로 정렬합니다.
column-reverse: 요소들을 아래에서 위로 정렬합니다.
```



예시) 

![](4%EC%A3%BC%EC%B0%A8%20Day02_Flexfroggy.assets/111.PNG)

```html
#pond {
	display: flex;
	flex-direction: row-reverse;
	justify-content: flex-end;
}
```



### Order

> 각 요소의 개별 순서 적용

- 기본 값은 0, 양수나 음수도 가능

  ```html
  order: -1;
  <!--해당 요소 순서 제일 앞으로-->
  ```

  

### Align-self

> 지정된 align-items 값을 무시하고 flex 요소를 세로선 상에서 정렬

```html
flex-start: 요소들을 컨테이너의 꼭대기로 정렬합니다.
flex-end: 요소들을 컨테이너의 바닥으로 정렬합니다.
center: 요소들을 컨테이너의 세로선 상의 가운데로 정렬합니다.
baseline: 요소들을 컨테이너의 시작 위치에 정렬합니다.
stretch: 요소들을 컨테이너에 맞도록 늘립니다.
```



### Flex-wrap

> flex 요소들을 한 줄 또는 여러 줄에 걸쳐 정렬

```html
nowrap: 모든 요소들을 한 줄에 정렬합니다.
wrap: 요소들을 여러 줄에 걸쳐 정렬합니다.
wrap-reverse: 요소들을 여러 줄에 걸쳐 반대로 정렬합니다.
```

- ex.`flex-wrap: wrap`



### Flex-flow

> flex-direction 과 flex-wrap 을 대신함

```html
flex-flow: row wrap 
요소들을 가로선 상의 여러 줄에 걸쳐 정렬
```



### Align-content

>세로선 상에 여분의 공간이 있는 경우 flex container 사이의 간격을 조절

```html
flex-start: 여러 줄들을 컨테이너의 꼭대기에 정렬합니다.
flex-end: 여러 줄들을 컨테이너의 바닥에 정렬합니다.
center: 여러 줄들을 세로선 상의 가운데에 정렬합니다.
space-between: 여러 줄들 사이에 동일한 간격을 둡니다.
space-around: 여러 줄들 주위에 동일한 간격을 둡니다.
stretch: 여러 줄들을 컨테이너에 맞도록 늘립니다.
```

- 한 줄만 있는 경우 align-content 는 효과를 보이지 않는다.
- `align-content`는 여러 줄들 사이의 간격을 지정하며, `align-items`는 컨테이너 안에서 어떻게 모든 요소들이 정렬하는지를 지정