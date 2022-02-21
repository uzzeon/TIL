# [SWEA] 5주차 Day03.



## 0216_String(4)



### 점점 커지는 당근의 개수 

- 틀린 이유: 연속되는 숫자가 앞에 3개가 있고, 뒤에 2개가 있을 수 있는데 이부분을 무시함.  (논리 접근 잘못됨)
- 무조건 제일 마지막에 연속되는 숫자의 갯수가 출력되게 함



### 고대 유적

- 아직 이게 능숙하게 안 쳐짐

  ```python
  ruins = [list(map(int, input().split())) for _ in range(N)]
  ```

- n x m 행렬의 경우 (특히 n, m이 다른 경우) 하나로 합치기 어렵다.



### 과제 5일차 - GNS

> 카운팅 정렬을 써라

```python
A = [0, 4, 1, 3, 1, 2, 4, 1]
N = len(A)
K = 4               # 최대값
C = [0] * (K + 1) # 최대값이 마지막 인덱스

for val in A:
    C[val] += 1
B = []

for i in range(K + 1):
    B += [i] * C[i]
print(B)
=======================================
nums = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]
tc_num, N = input().split()
arr = input().split()

ans = tc_num   # '#번호'
for n in nums:
    ans += (' ' + n) * arr.count(n)
print(ans)
#=====================================================
nums = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]
tc_num, N = input().split()
arr = input().split()

cnt = [0] * 10
# 무식하게 하지 뭐~
for x in arr:
    for i in range(10):
        if x == nums[i]:
            cnt[i] += 1
            break

ans = tc_num   # '#번호'
for i in range(10):
    ans += (' ' + nums[i]) * cnt[i]
print(ans)
#=======================================================
# 딕셔너리를 사용
nums = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]
nums_dict = {"ZRO":0, "ONE":1, "TWO":2, "THR":3, "FOR":4, "FIV":5, "SIX":6, "SVN":7, "EGT":8, "NIN":9}
tc_num, N = input().split()
arr = input().split()

cnt = [0] * 10
# 무식하게 하지 뭐~
for x in arr:
    cnt[nums_dict[x]] += 1

ans = tc_num   # '#번호'
for i in range(10):
    ans += (' ' + nums[i]) * cnt[i]
print(ans)
```

