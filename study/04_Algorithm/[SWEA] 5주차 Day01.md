# SWEA SOLVING CLUB



## 10587 List2 연습2

```python
T = int(input())
for tc in range(1, T+1):
    N = 10
    A = list(map(int, input().split()))

    for i in range(1, 1<<N): #공집합을 제외하라고 했으니, 1부터 시작
        s = 0
        for j in range(N):
            if (i&(1<<j)): #j번 비트가 나타내는 원소가 포함된 경우
                s += A[j]

        if s == 0: # 합이 0이 되는 부분집합이면
            print(f'#{tc} 1')
            break
    else:
        print (f'#{tc} 0')
```

- 마지막에 `if ~ else` 위치 설정에서 많이 헤맴. 

  **`else` 위치** : for문 다 돌았어도 if 문에 안걸렸을때 else로 가도록!!



## 1209. 2일차 - SUM

```python
T = 10
for tc in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(100)]
    max_val = 0

    # 행 우선 순회... 각 행
    for i in range(100):
        total1 = 0
        for j in range(100):
            total1 += arr[i][j]
        if max_val < total1:
            max_val = total1

    # 열 우선 순회
    for i in range(100):
        total2 = 0
        for j in range(100):
            total2 += arr[j][i]
        if max_val < total2:
            max_val = total2

    # 대각선 합 중 가장 큰 값
    for i in range(100):
        total3 = 0
        total3 += arr[i][i]
        if max_val < total3:
            max_val = total3

    total4 = 0
    for i in range(99,-1,-1):
        total4 += arr[i][99-i]
        if max_val < total4:
            max_val = total4

    print(f'#{tc} {max_val}')
```

- 핵심
  - 2차 배열을 입력받는 것 
  - 입력 확인하기

```python
for tc in range(10):
    tc_num = input()    
    arr = [list(map(int, input().split())) for _ in range(100)]

    ans = 0             # 최대합을 저장하기 위한 변수
    diag1 = diag2 = 0
    for i in range(100):
        diag1 += arr[i][i]
        diag2 += arr[i][99 - i]

        rsum = csum = 0
        for j in range(100):
            rsum += arr[i][j]
            csum += arr[j][i]
        # ans = max(ans, rsum, csum)
        if ans < rsum:
            ans = rsum
        if ans < csum:
            ans = csum
    if ans < diag1:
        ans = diag1
    if ans < diag2:
        ans = diag2

    print(ans)
```


