# 4주차 Day_04



## 10565. 4828. min-max

```python
T = int(input())

for tc in range(1, T+1):
    N = int(input())
    ai = list(map(int, input().split()))

    min_num = ai[0]
    max_num = ai[0]
    for num in ai:
        if min_num > num:
            min_num = num
        if max_num < num:
            max_num = num

    print(f'#{tc} {max_num - min_num}')
```

- `maxV = 1e10`(10의 10승), `minV = -1e10` 로 정의할 수도 있다. _ int(1e10) 
  - cf. `1e4 = 10000`  



## 10567. 4835. 구간합

```PYTHON
T = int(input())

for tc in range(1, T+1):
    N, M = map(int, input().split())
    ai = list(map(int, input().split()))

    def bundle(x):
        total = 0
        for i in range(x, x+M):
            total += ai[i]
        return total

    min_val = bundle(0)
    max_val = bundle(0)

    for i in range(1, len(ai)-M+1):
        if bundle(i) < min_val:
            min_val = bundle(i)
        if bundle(i) > max_val:
            max_val = bundle(i)

    print(f'#{tc} {max_val - min_val}')
```

- 조건을 활용해서, maxV = 0 , minV = 1,000,000



```python
# 1. 첫 번째 구간의 합을 구한다.
# 2. 다음 구간의 합을 구할 때는, 첫 번째 구간의 첫번째 요소를 빼고, 첫 번재 구간 다음의 요소를 더한다.
# >>> 계산을 덜 하게 된다.

s = 0
for i : 0 → M-1
    S += a[i]
    # 첫번째 구간의 합을 구한 것을 초기값으로 설정
    maxV ← s
    minV ← s
    
    for i in range() #부분배열의 시작이 i
    	s = s - a[i] + a[i+M]
        
        if maxV < s:
            maxV = s            
        if minV > s:
            minV = s
```







## cf. 연습) 반복문 활용 구구단

```python
N = int(input())

# <FOR문 활용>
# for i in range(1, N+1):
#     for j in range(1, N+1):
#         print(f'{i}x{j} = {i*j}')

# <WHILE문 활용>
i = 1
while i <= N:
    j = 1
    while j <= N:
        print(f'{i}x{j} = {i*j}')
        j += 1
    print()
    i += 1
```





## 4834. 숫자카드

```python
T = int(input())
for tc in range(1, T+1):
    N = int(input())
    arr = list(map(int, input()))

    counts = [0] * 10
    for i in range(N):
        counts[(arr[i])] += 1

    max_jang, max_num = counts[0], 0

    for i in range(10):
        if counts[i] >= max_jang:
            max_jang = counts[i]
            max_num = i

    print(f'#{tc} {max_num} {max_jang}')
    
 # 모두 1장씩만 있을 경우에 굳이 따로 max_num을 안 찾아도 되는 이유: counts에서 가장 뒤로 갈 수록 숫자가 커지기 때문에 for-if 문에서 `>=` 을 사용하면 자동으로 max_num이 저장된다.
```

- 아이디어 : cnt 를 만들어서,,



## 4831. 전기자동차... ★

```python

T = int(input())
for tc in range(1, T+1):
    K, N, M = map(int, input().split())
    arr = [0] + list(map(int, input().split())) + [N]

    cnt = 1
    for i in range(len(arr)-1):
        if (arr[i + 1] - arr[i]) > K:
            answer = 0
            break

        else:
            if arr[i] < K * cnt <= arr[i+1]:
                cnt += 1
            answer = cnt - 1


    print(f'#{tc} {answer}')
```



교수님 해설

```python
T = int(input())
for tc in range(1, T+1):
    K, N, M = map(int, input().split())
    arr = [0] + list(map(int, input().split())) + [N]

    cnt = 0
    last = 0 # 마지막 충전 위치
    for i in range(1, M+2): # 도착확인할 정류장 인덱스
        if arr[i] - arr[i-1] > K:
            cnt = 0
            break
        elif arr[i] - last > K: #마지막 충전 위치치부터 너무 먼 경우
            last = arr[i-1]
            cnt += 1

    print(f'#{tc} {cnt}')
```





## 220209_List1. Flatten



```PYTHON
for tc in range(1, 11):
    N = int(input()) # 덤프 횟수 ( 1<= N <= 1000)
    arr = list(map(int, input().split()))

    # 각 상자의 높이에 따른 counts 박스
    counts = [0] * 100
    for i in arr:
        counts[i-1] += 1

    rev_counts = sorted(counts, reverse=True)
    print(rev_counts)

    total_dump = 0
    for i in range(100):
        for x in range(i+1):
            total_dump += rev_counts[i-x]
            if total_dump > N:
                max_height = 100 - i # 이때 counts의 i번재 인덱스에 해당하는 값이 최고 높이
                break

    print(max_height)
```

