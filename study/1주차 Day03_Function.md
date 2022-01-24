# Day 03. Function _ 오전

> 특정한 기능을 하는 코드의 조각(묶음)

- 특정 명령을 수행하는 코드를 매번 다시 작성하지 않고, 필요 시에만 호출하여 간편히 사용



## 1. 함수 기초

- 사용자 함수와 내장함수 

```python
def function_name(parameter):
    #code block
    return returngin_value
```

```python
import statistics
values = [100, 75, 95, 85, 90]
statistics.pstdev(values)

# pstdev 함수 : 표준편차
```

- 기본구조 : 입력, 결과값, 문서화, 범위



### 정의(선언)과 호출

> 선언은 def로, 호출은 함수명()으로

- tip) 호출될때 정의된 부분을 보고 실제 결과가 무엇인지 유출한다.
- 함수 정의 시 생각할 것: 이름(함수) - Input 이름 - 로직 - 결과값



## 2. 함수의 결과값(Output)

- Void function : 명시적 return값이 없는 경우 none을 반환하고 종료
- Vaule returning function



- print vs return

  - print는 출력을 위해 사용되는 함수_ 값을 보려고 사용

  - return은 함수 안에서 사용되는 키워드. 

    - 값을 반환하고 함수 종료. 반환 값으로 튜플 사용

    

- return X → None을 반환 

- return o → 하나의 객체를 반환

```python
def rectangle(width, height):
    return width * height, 2 * (width + height)

print(rectangle(30, 20))
(600, 100) #하나의 튜플로 반환
```



## 3. 함수의 입력(Input)

- parameter와 argument
  - p: 식별자, a: 함수 호출할 때 넣어주는 값



Argument

- 1. Positional Arguments : 가장 기본
  2. Keyword A
  3. Default Arguments Values : 기본값을 지정하여 함수 호출시 argument 값 설정하지 않도록 함

```python 
def add(x, y):
    return x + y

print(add(1, 2)) # Positional_ 내부에서 바인딩 x=1, y=2
print(add(y=2, x=1)) #keyword_ 직접 x와 y 값을 지정
print(add(1, y=2)) #positional 하고 keyword는 가능
print(add(x=1, 2)) #Syntax Error. keyword 다음에 positional은 불가능

def add(x, y=0):
	return x + y #Default

def foo(a=1, b=2, c)
	pass
foo(c=2) #절대 안됨. keyword 한다음에 positional 안되니까 못부름
```

- 정해지지 않은 여러 개의 Arguments 처리 : 연산자(*) 'asterisk'
- Positional A_ packing/unpacking

```python
def add(*args):
    return(args, type(args))
    
print(add(1, 2, 3, 4))
((1, 2, 3, 4), <class 'tuple'>)

-----------------------------------------

def add(*args):
    print(args, type(args))

print(add(1, 2, 3, 4))
(1, 2, 3, 4) <class 'tuple'>
None
```



- Keyword A_packing/unpacking : 연산자(**)로 하면 딕셔너리로 묶여 처리됨 (key-value)

```python
def family(**kwagrs):
    print(kwagrs, type(kwagrs))
   
family(father = '고길동', monster = '공룡') #father는 식별자, 고길동은 값
{'father': '고길동', 'monster': '공룡'} <class 'dict'>
```

![요약 정리](Day03_Function.assets/%EC%BA%A1%EC%B2%98.PNG)



## 4. 함수의 범위

- 코드 내부에 **local scope** 를 생성하고, 그 외의 공간인 **global scope** 로 구분

- 함수의 가장 기본 : local scope

blackbox 안에서 생성된 것은 그 안에서 사용되고 끝남

블랙박스의 결과를 받아보고 싶으면 반환 값을 변수에 저장해서 사용하는 것

블랙박스 밖으로 결과를 주고 싶으면 return을 해줘야 한다.

- LEGB

built-in socpe: 파이썬 실행된 이후부터 영원히

global scope: 모듈이 호출된 시점 이후 혹은 인프리터(.py)가 끝날 때까지 유지

local scope: 함수가 호출될 때 생성되고, return 될 때까지 유지



## 5. Q & A

- 함수를 직접 만들 때 입력 혹은 출력에 대한 타입을 직접 정할 수 있나요?

  - Dynamic type language - python

- type hinting (동작을 막는게 아니라 단순 힌트)

- 바인딩 

  ```python
  def foo(a, b):
      return a, b
  
  foo(1, 2) # a= 1, b = 2 로 바인딩
  foo(1, 2, 3) # 위치로 대응x _error
  foo(b=2, a=1) # b=2, a=1로 바인딩
  ```

- string이 immutable 하다?

  ```python
  A = 'SSAFY' 에서 A[0] = 'P'를 해도 대입이 안돼요
  
  a = ''
  a = a + '123'
  값 자체를 바꿔버리는 행위
  
  a = [1, 2 3]
  a = [4, 5]
  이렇게 바꾸는건 가능하다.
  ```

- 함수 정의: 기본 정의, 기본 값 지정, 정해지지 않은 갯수(*또는 ** 사용)

  

  