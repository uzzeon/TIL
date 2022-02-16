# SWEA SOLVING CLUB



## 1208. [S/W 문제해결 기본] 1일차 - Flatten

```python
<<아이디어>>

while dump > 0:
    최대 최소 검색 =>
    box[maxIdx]-box[minIdx] >= 2:
        box[maxIdx] -= 1
        box[minIdx] += 1
        dump -= 1
       
    else: # 덤프횟수가 없을때 & 최대최소 차이가 2보다 작을때 빠져나와야 함
        최대, 최소 검색    
```

- 카운트배열 사용법

  - cnt 배열....  → 0이 아닌 애= 가장 낮은 애 , ← 0이 아닌애= 가장 높은 애

    [DUMP] 가장 낮은애 하나씩 빼고 0이 되면 다음애를 빼기... 높은애도 마찬가지



답

```python
def max_i(arr):
    tmp = arr[0]
    result = 0
    for i in range(len(arr)):
        if tmp < arr[i]:
            tmp = arr[i]
            result = i
    return result


# 배열 내 최소값의 인덱스를 반환
def min_i(arr):
    tmp = arr[0]
    result = 0
    for i in range(len(arr)):
        if tmp > arr[i]:
            tmp = arr[i]
            result = i
    return result


for t in range(1, 11):
    dump = int(input())
    box = list(map(int, input().split()))
    cnt = 0
    while dump:
        if box[max_i(box)] - box[min_i(box)] <= 1:
            break
        box[max_i(box)] -= 1
        box[min_i(box)] += 1
        dump -= 1
    print(f'#{t} {box[max_i(box)] - box[min_i(box)]}')
```





## 달팽이

```python
<아이디어>
ⓐ 델타 배열: 영역을 벗어나거나 0이 아니면, 진행방향의 90도 꺾어라
    (k+1) % 4
ⓑ
```



미친 달팽이놈

```python
### 틀린 코드 주의 ######

T = int(input())
for tc in range(1, T+1):
    N = int(input())
    arr = [[0] * N for _ in range(N)]

    i = 0 #행
    j = 0 #열
    arr[0][0] = 1
    x = 1 #이동거리 (~N*N까지)
    di = [0,1,0,-1] # 우하좌상
    dj = [1,0,-1,0]
    d = 0 #di와 dj 인덱스 지정 (0~3까지 가짐) 일단 가장먼저 우측으로 이동하기때문에 0으로 초기값 설정

    while x < N*N:
        ni, nj = i+di[d], j+dj[d]
        if 0<= ni < N and 0<= nj < N and arr[i][j] == 0 : #유효범위 내에 있어야 한다.
            x += 1
            i, j = ni, nj
            arr[i][j] = x

        else: #범위 밖으로 나가면 방향 바꿔야 함
            d = (d + 1) % 4  # 우하좌상 한바퀴 돌면 direc 도 초기화 되어야 함. 0 1 2 3 0 1 2 3 0 1 2 3...

    print("#{}".format(tc))
    for i in range(N):
        print(*i)
        # for j in range(N):
        #     print(arr[i][j], end=" ")
        # print()
```

```python
    num = 1
    row, col = 0, -1
    # 진행방향 설정 바꾸기
    trans = 1

    while n > 0:
        for _ in range(n):
            col += trans
            arr[row][col] = num
            num += 1
        n -= 1
        for _ in range(n):
            row += trans
            arr[row][col] = num
            num += 1
        # 방향 바꾸기
        trans *= -1
```



** 교수님 정답 참고하기



-----

---



## 4836. 색칠하기

```python
T = int(input())

for tc in range(1, T+1):
    arr = [[0] * 10 for _ in range(10)]

    N = int(input()) #칠할 영역의 개수 i (0~N-1)
    answer = 0  # 보라색 영역의 수
    for _ in range(N):
        color = list(map(int, input().split())) #이 리스트 원소 수는 무조건 5개 _ i1 j1 i2 j2 color
        for i in range(color[0], color[2]+1):
            for j in range(color[1], color[3]+1):
                if arr[i][j] == 0 or arr[i][j] != color[4]:
                    arr[i][j] += color[4]
                if arr[i][j] == 3:
                    answer += 1

    print(f'#{tc} {answer}')
```



## 4843. 2일차 - 특별한 정렬

```python
T = int(input())
for tc in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))
    
    for i in range(N-1, 0, -1): #버블정렬
        for j in range(0, i):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

    ans = [0] * 10

    for i in range(10): # i는 ans의 인덱스
        if i % 2: #홀수번째 인덱스에는 최소값
            ans[i] = arr[(i+1)//2 - 1]
        else:
            ans[i] = arr[N-((i//2)+1)]

    print(f'#{tc}', end=' ')
    print(*ans)
```

- 마지막 format 조정 : list를 풀어서 쓸때 `*` unpacking 연산자 활용



#### 선택정렬 활용해서 풀어보기

```python
for i in range(10):
    if i % 2 == 0:
        maxIdx = i
        for j in range(i+1, N):
            if arr[maxIdx] < arr[j]:
                maxIdx = j
        att[i], arr[maxIdx] = arr[maxIdx], arr[i]
    else:
        minIdx = i
        for j in range(i+1, N):
            if arr[minIdx] > arr[j]:
                minIdx = j
        att[i], arr[minIdx] = arr[minIdx], arr[i]
```



## 4839. 이진탐색

```python
print(-7/2) = -3.5
print(-7//2) = -4

print(int(-7/2)) = -3
print(int(-7//2)) = -4
print(int(7/2)) = 3
print(7//2) = 3
```

- while문 안에서 if에 걸리지 않았을 때는 오류가 있다는 의미로  `return -1`



## 4837. 부분집합의 합





## ladder

```python
T = 10
for tc in range(1, 11):
    N = int(input())
    data = [list(map(int, input().split())) for _ in range(100)]

    # 역진귀납 이용
    # 문제에서 data[x][y] : x가 열, y가 행 ... 일단 data[i][j] 로 생각하고 마지막에 바꾸기...

    di = [-1, 0, 1, 0]  # 상좌하우
    dj = [0, -1, 0, 1]
    direction = 0
    # 1만 따라가고, 진행방향과 다른 방향의 1을 만나면 방향을 바꾼다.
    # y == 0 일때 break >> 그때의 x값을 구해라.

    # 1. 99번째 행에서 숫자 2가 쓰인 칸을 찾는다. (양측에 0이 하나씩 붙어서 열이 102개)
    j =0 # 도착지 행.... data[99][x]
    for start in range(100):
        if data[99][start] == 2:
            break
    # 2. 이동 시작. 이동칸수는 고려사항x 이동방향과 좌표만 따지면 된다. x,y, direction
    i = 99
    j = start
    while i > 0:
        i += di[direction]
        j += dj[direction]
        if direction == 0 and data[i][j-1] == 1:   # 위로 가다가 왼쪽에서 1을 만난 경우
            direction = (direction + 1) % 4
        elif direction == 3 and data[i-1][j] == 1 and (i-1)<100:  #오른쪽으로 가다가 왼쪽에서 1만나면 (다시 위로)
            direction = (direction + 1) % 4
        elif direction == 0 and data[i][j+1] == 1: #위로 가다가 오른쪽에서 1을 만난 경우
            direction = (direction - 1) % 4
        elif direction == 1 and data[i-1][j] == 1 and (i-1)>=0: # 왼쪽으로 가다가 오른쪽에서 1을 만난 경우 (다시 위쪽으로)
            direction == (direction - 1) % 4

    print(j-1)

```

