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





