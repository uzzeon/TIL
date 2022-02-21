# [SWEA] 5주차 Day04.



## [0216 String] 과제 GNS 리뷰

> 카운팅 정렬을 써라

```python
T = int(input())

for tc in range(1, T+1):
    tc, length = input().split()
    str_list = input().split()

    num_dict = {"ZRO":0, "ONE":1, "TWO":2, "THR":3, "FOR":4, "FIV":5, "SIX":6, "SVN":7, "EGT":8, "NIN":9}
    nums = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]
    cnt = [0]*10 # 각 문자가 몇 번씩 나왔는지 기록
    ans = ''

    for i in str_list:
        cnt[num_dict[i]] += 1

    for h in range(10): #나오는 문자열은 10개로 한정되어있으니깐
        ans += (nums[h]+' ') * cnt[h]

    print(f'{tc} \n{ans}')
```



> 선택정렬

- 자리 교환은 for문이 끝난 다음에 해야 한다.

```python
for i in range(N-1):
    minIdx = i
    for j in range(i+1, N):
        if num[minIdx] > num[j]:
            minIdx = j
        num[i], num[minIdx] = num[minIdx], num[i]
```

```python
dict1={"ZRO":0, "ONE":1, "TWO":2, "THR":3, "FOR":4, "FIV":5, "SIX":6, "SVN":7, "EGT":8, "NIN":9}
dict2=dict(zip(dict1.values(), dict1.keys()))
#>> {0: 'ZRO', 1: 'ONE', 2: 'TWO', 3: 'THR', 4: 'FOR', 5: 'FIV', 6: 'SIX', 7: 'SVN', 8: 'EGT', 9: 'NIN'}
```

- `zip(seq1, seq2, seq3)` seq는 각각 시퀀스형 데이터 타입

  (seq1의 첫번째 element, seq2의 첫번째 element, seq3의 첫 번째 element), (seq1의 두번째 element, seq2의 두번째 element, seq3의 두 번째 element), (seq1의 세번째 element, seq2의 세번째 element, seq3의 세번째 element) ...



## [0215 List2실습] ladder

- 왼쪽/오른쪽 이 위쪽보다 우선되어야 한다.
- 제일 간단한 코드 : 지나가오면서 지운다.

```python
tc = int(input())
arr = [[0] + list(map(int, input().split()))+ [0] for i in range(100)]

for i in range(102):
    if arr[99][i] == 2:
        X = i
        
Y = 99
while Y > 0:
    if arr[Y][X+1] == 1:
        arr[Y][X] = 0 #올라가면서 지움. 지나온애 없앰
    elif arr[Y][X-1] == 1:
        arr[Y][X] = 0
    elif arr[Y-1][X] == 1: #가장 마지막에 위로가는길
        Y -= 1
```





---

---



## [0217 String 실습]

ⓐ글자수 - ok ⓑ회문 ★★★ ⓒ문자열 비교 - 다시!

### 회문 

```python
T = int(input())
for tc in range(1, T+1):
    N, M = map(int, input().split())
    data = [str(input()) for _ in range(N)]

    answer = ''
    # 행 우선순회
    for i in range(N):
        for j in range(N-M+1):
            ans_cnt = 0
            for half in range(M//2):
                if data[i][j+half] == data[i][j+M-half-1]: # 첫글자와 마지막 글자가 같으면, 앞에서 두번째 글자와 뒤에서 두번째 글자가 같은지,, 안으로 들어오면서 비교
                    ans_cnt += 1
                    # print(ans_cnt)
                else:
                    ans_cnt = 0
            if ans_cnt == (M // 2): #회문임. 출력ㄱ
                for l in range(M):
                    answer += data[i][j + l]

    # 열 우선순회
    for i in range(N):
        for j in range(N-M+1):
            ans_cnt = 0
            for half in range(M//2):
                if data[j+half][i] == data[j+M-half-1][i]: # 첫글자와 마지막 글자가 같으면, 앞에서 두번째 글자와 뒤에서 두번째 글자가 같은지,, 안으로 들어오면서 비교
                    ans_cnt += 1
                    # print(ans_cnt)
                else:
                    ans_cnt = 0
            if ans_cnt == (M // 2): #회문임. 출력ㄱ
                for l in range(M):
                    answer += data[j + l][i]

    print(f'#{tc} {answer}')
```

- 이 부분 만드는데 엄청 오래걸림...

  ```python
  for half in range(M//2):
                  if data[i][j+half] == data[i][j+M-half-1]:
  ```

  

---



## [0218] 문제풀이 Ⅰ



### 어디에 단어가 들어갈 수 있을까

- 틀린이유 :  블록 중간에 흰색 3개가 있어도 마지막에 검정색이 있으면 카운트가 안되기 때문

```python
  cnt = 0 # 단어가 들어갈 수 있는 자리 수 (찾고자 하는 답)
    for i in range(N):
        blank_cnt = 0
        for j in range(N):
            if arr[i][j] == 1:
                blank_cnt += 1
            else:
                blank_cnt = 0
    if blank_cnt == K: #빈칸 수 : 정확하게 K값이어야 한다.
        cnt += 1
```



pass 답 : blank_cnt가 K가 되었을때 다음이 벽이거나, 다음 블록이 검정색일때(=0) => cnt + 1

```python
T = int(input())
for tc in range(1,T+1):
    N, K = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]

    # 행 우선순회
    cnt = 0 # 단어가 들어갈 수 있는 자리 수 (찾고자 하는 답)
    for i in range(N):
        blank_cnt = 0
        for j in range(N):
            if arr[i][j] == 1:
                blank_cnt += 1
                if blank_cnt == K and (j == N-1 or arr[i][j+1] == 0): 
                    # blank_cnt가 K가 되었을때 다음이 벽이거나, 다음 블록이 검정색일때(=0) => cnt + 1
                    cnt += 1
            else:
                blank_cnt = 0

    # 열 우선순회
    for i in range(N):
        blank_cnt = 0
        for j in range(N):
            if arr[j][i] == 1:
                blank_cnt += 1
                if blank_cnt == K and (j == N - 1 or arr[j + 1][i] == 0):  
                    # blank_cnt가 3이되었을때 다음이 벽이거나, 다음 블록이 검정색일때(=0) => cnt + 1
                    cnt += 1
            else:
                blank_cnt = 0
    print(f'#{tc} {cnt}')
```

