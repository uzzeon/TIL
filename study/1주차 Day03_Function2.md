# Day 03. Function_오후



## 6. 함수의 문서화(Doc-String)

#### 1. Docstring

- 설명... Jupyter notebook에서 `shift+tab`

  

#### 2. Naming Convention

- 상수 이름은 영문 전체를 대문자
- 클래스, 예외 이름은 첫 글자만 대문자
- 나머지는 소문자, 밑줄로 구성
- 인덱스 : i _ j



## 7. 함수 응용



#### 1. map  : map(function, iterable)

>  input 값들을 숫자로 바로 활용하고 싶을때 

```python
input_value = input()
type(input_value) 
str
-----------------

input_value = input()
input_value.split() # split은 나눠서 저장
['20', '20'] # 리스트 형태

numbers = input_value.split()
result = []
for number in numbers:
    result.append(int(number))
print(result)
[20, 20]

-------------------- map 적용 -------------------
a = input.split()
list(map(int, a))
[20, 20]

n, m = map(int, input().split())
print(n, m)
print(n, m, type(n), type(m))
```

- map의 결과는 하나의 묶음(시퀀스)
- 매번 list 형 변환해서 사용해야 함 = list(map(function, iterable))
  - 왜? 값을 리스트로 반환해주면 한번에 다 받아야 함. 이터레이터는 하나씩 뽑아주는 기계 (공간을 효율적으로 사용) → 내가 그 값을 보려면 리스트로 형변환해서 봐야 하는 것




#### 2. filter : filter(function, iterable)

> 순회 가능한 데이터구조의 모든 요소에 함수 적용하고 그 결과가 True인 것들을 filter object로 반환

```python
def odd(n):
    return n % 2
numbers = [1, 2, 3]
result = filter(odd, numbers)

print(result, type(result)) 
<filter object at 0x10e4dfc10> <class 'filter'>

list(result)
[1, 3]
```

- 매번 list 형 변환해서 사용해야 함
- 'function 함수 적용 / iterable : 통' 이라고 해석하기



#### 3. zip : zip(*iterables)

> 복수의 iterable을 모아 튜플을 원소로 하는 zip object 반환

```python
girls = ['jane', 'jenny']
boys = ['justin', 'tom']
pair = zip(girls, boys)
print(pair, type(pair))
list(pair)
=> [('jane', 'justin'), ('jenny', 'tom')]
```



#### 4. lambda 함수

> 이름 없는 익명 함수. def 대신에 사용 (잠깐 쓸 때)

```python
def triangle_area(b, h):
    return 0.5 * b * h
triangle_area(5, 6)
15.0

triangle_are = lambda b, h : 0.5 * b * h
```

```python
def odd(n):
    return n % 2
print(list(filter(odd, range(5))))

print(list(filter(lambda n: n % 2, range(5))))

```

- lambda 대신에 def  함수



#### 5. 재귀 함수 (recursive funciton)

> 정의 암기 ★) 자기 자신을 호출하는 함수 

- 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성
- 예: factorial (!)

- f라는 함수를 정의하고 base case에 수렴할 때까지 계속 호출하는 것 

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n-1) #내부에서 factorial 호출
factorial(4)
```



## ＠ Q & A

##### 1. map 함수 다시 설명

- input() : 사용자 입력값을 string으로 반환해줌

- split() : default는 공백

  ```python
  #['1', '2', '3'] => [1, 2, 3] 각각 int 형변환을 해줄 수 있다.
  n, m = map(int, input().split())
  
  n, m = map(int, "20 20".split()) 
  n, m = map(int, ["20", "20"])
  n, m = [20, 20]
  ```

> 함수를 통해 통에 있는 각각의 요소에 적용된 결과를 반환(map object)



##### 2. print vs return

- print 출력하는것 / return 함수 반환
- print 그냥 보기 위해서 / return은 코드 작성하기 위해 함수 반환
- 
