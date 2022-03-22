## 스택

> 물건을 쌓아 올리듯 자료를 쌓아 올린 형태의 자료구조

- 스택에 저장된 자료는 선형 구조를 갖는다. = 1대1의 관계 ↔ 비선형구조: 트리
- 스택에 자료를 삽입하거나 스택에서 자료를 꺼낼 수 있다.
- 마지막에 올려놓은 자료를 가장 먼저 꺼낸다. "<u>후입선출(LIFO)</u>"



- 자료구조: 자료를 선형으로 저장할 저장소
  - 배열을 사용할 수 있다.
  - 저장소 자체를 스택이라 부르기도 한다.
  - 스택에서 마지막 삽입된 원소의 위치를 top이라 부른다.

- 연산

  - 삽입(`push`): 자료를 저장한다 

    - ⑴ top을 증가시키고 ⑵ 데이터 저장

    ```python
    def push(item):
        s.append(item) #좀 느리다
        
    ## ======== ##
    
    def push(item, size):
        global top #최대 사이즈를 알아야 한다. (넘치지 않게 하려고)
        top += 1
        if top == size:
            print('overflow') #디버깅용
        else:
            stack[top] = item
            
    ## ======== ##  
    
    size = 10 #크기를 정하기
    stack = [0] * size #스택 만들기
    top = -1
    
    push(10, size)
    top += 1
    stack[top] = 20
    ```

    

  - 삭제(`pop`): 자료를 꺼낸다. 삽입한 자료의 역순으로 꺼낸다.

    - ⑴top이 가리키고 있는 애를 꺼내고  ⑵ ~~굳이 지울 필요~~ (어차피 덮어쓸것)

    ```python
    def pop():
        if len(s) == 0:
            return
       	else:
            return s.pop(-1); #좀 느리다
        
    ## ===== ##
    
    def pop():
        global top
        if top == -1:
            print('underflow')
            return 0
        else:
            top -= 1
            return stack[top+1]
    print(pop())
        
    ## ===== ##
    
    if top > -1: #pop()
        top -= 1
        print(stack[top+1])
        
    ## ===== ##
    
    while top >= 0:
        n = stack[top]
        top -= 1
    ```

  - 스택이 공백인지 아닌지 확인: `isEmpty`

  - 스택의 top에 있는 item(원소)을 반환하는 연산: `peek`



- 스택의 응용 : 괄호검사
  - `&&` : and
  - `(`는 스택에 삽입하고, `)`는 스택에서 top괄호를 삭제하고 짝이 맞는지 검사



- 스택의 응용2 : function call



## 재귀호출 

> 자기 자신을 호출하여 순환 수행되는 것
>
> ⓐ 팩토리얼 ⓑ 피보나치 ⓒ 재귀 복사

- 보다 프로그램의 크기를 줄이고 간단하게 작성

```python
def fact(n):
    if n == 1:
        return 1
    else:
        return n*fact(n-1)    	
```

- 호출될 때마다 함수는 자기가 사용할 고유 영역을 가짐. 메모리영역이 분리됨
- 호출될 때마다 메모리에 저장되는 값을 생각해야 함..

```python
f(i, N) #일반적인 형태) i는 현재, N은 목표
fibo(n) # 점점 1, 0 등으로 감소해가는 것이기 때문에 변수가 하나만 있어도 ㅇㅋ
```

- 재귀복사

  ```python
  def f(i, N):
      if i == N:
          print(B)
      else:
          B[i] = A[i]
          f(i+1, N)
          
  A = [10, 20, 30]
  B = [0]*3
  f(0, 3)
  ```

  



## Memoization '메모리에 넣기'

> 컴퓨터 프로그램을 실행할 때 이전에 계산한 값을 메모리에 저장해서 매번 다시 계산하지 않도록 하여 전체적인 실행속도를 빠르게 하는 기술

- 시행시간을 줄일 수 있다. (세타 n)

```python
def fibo(n):
    if n>=2 and memo[n] == 0:
        memo[n] = fibo(n-1) + fibo(n-2) #memo에 구해놓고
    return memo[n]

N = 20
memo = [0]*(N+1)
memo[0] = 0
memo[1] = 1
print(fibo(N)) #답만 출력 
print(memo) #저장해놓은 중간값들 호출
```



## DP (Dynamic Programming)

> 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘

- 먼저 입력크기가 작은 부분 문제들을 모두 해결한 후에 그 해들을 이용하여 보다 큰 크기의 부분 문제들을 해결하여 최종적으로 원래 주어진 입력의 문제를 해결하는 알고리즘
- 반복 구조로도 구현 가능

```python
def fibo2(n):
    f = [0, 1]
    
    for i in range(2, n+1):
        f.append(f[i-1]+f[i-2])
        
   return f[n]
```





---

## 문제풀이

- 괄호검사 문제 : 모든 경우 다 커버해야 함

```python
T = int(input())
for tc in range(1, T+1):
    s = input()
    
    stack = [0] * 1000  # 최대 길이 1000이하라고 가정
    top = -1
    ans = 1
    
    for x in s:
        if x == '(':
            top += 1    # push
            stack[top] = x
            
        elif x =='':
            if top == -1:   # 닫는 괄호가 남은 경우
                ans = 0
            else:
                top -= 1
        
    else:
        if top != -1:   # 여는 괄호가 남은 경우 ★ 특히, 빼먹기 쉬움 
            ans = 0
    
    print(ans)
```



