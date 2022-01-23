# Day 04. Python 실습



## 1. Q & A

1. 리스트인지 딕셔너리인지? 먼저 파악

   ```python
   students = [
       {'이름': '신희', 'role':'반장'},
       {'이름': '찬영', 'role':'학생'}
   ]
   
   students[0]
   #=>{'이름': '신희', 'role':'반장'}
   
   students[0]['이름']
   #=>신희
   ```

2. 매개변수로 리스트 받기

   ```python
   def my_sum(numbers):
       # numbers는 리스트를 주면 sum을 return해주겠다
       return sum(numbers)
   
   sum(1, 2, 3) #오류 뜸
   sum([1, 2, 3]) #=> 6
   # 리스트 변수를 정의보다 먼저 선언한 다음에 변수를 받는다.
   # 따로 리스트만 받도록 하는 것은 파이썬에서 안된다.
   ```



## 2. 실습문제02_ Practice 1

### 1번 문제: `abs()` 직접 구현하기

내 답안

```python
def my_abs(x):
    if type(x) is complex:
        complex_number = ((x.real **2 + x.imag **2) ** 0.5)
#       if complex_number >= 0 :
           absolute = complex_number
#       else:
#           absolute = - complex_number
        return absolute

    else:
        if x >= 0:
            absolute = x
        else:
            absolute = -x
    return absolute
```



참고 답안Ⅰ

```python
def my_abs(x):
    try:
        return x if x> 0 else -x
    except:
        x = str(x).replace('-', '+')
        a, b = x[1:-1].split('+')
        return ((a ** 2) + (b ** 2)) ** .5
```

- 복소수를 문자열로 바꾸고, `split`으로 표현함
- replace('-', '+') : 어차피 제곱할거니까 부호 상관없어서 다 +로 바꿈



참고 답안Ⅱ

```python
def my_abs(x):
    if type(x) == int or type(x) == float:
        if x >= 0:
            return x
        elif x == 0:
            return 0
        else:
            return -x
    elif type(x) == complex:
        return (x.real**2 + x.imag**2)**0.5
```



풀이

```python
# 조건1. 숫자형 자료가 들어오면 절댓값 반환
# 조건2. 복소수형 자료 들어오면 해당하는 자료 크기를 반환

def my_abs(n):
    # 숫자형 자료일 때
    if n < 0:
        return -n
    elif n > 0:
        return n
    else:
        return n ** 2  # -0 == 0 이기 때문에 my_abs(-0)하면 0나오게 하기 위해서

    # 복소수형 자료일 때
    if type(n) is complex:
        return (n.imag**2 + n.real**2) ** 0.5
```



- or 사용하기

  ```python
  n = 1
  type(n) is float or type(n) is int
  # > True
  
  # type(n) is float or int 이렇게 하면 안된다.
  # =>> (type(n) is float) or (int) 
  # type(n) is (float or int) 이렇게 하면 안된다.
  ```

  

### 2번 문제

```python
def my_all(elements):
    for i in elements:
        if bool(i) == False:
            return False
    return True
```



참고 답안 Ⅰ

```python
def my_all(elements):
    for i in elements : 
        if not i :
            return False
    return True
```



참고 답안 Ⅱ : 교수님 답안

```python
def my_all(elements):
    # 통의 모든 요소 => for
    for i in elements : 
        # 조건: 요소가 참인지 확인 => True
        if not i :
            return False
    return True

# 맨 마지막 값만 보고 값이 반환된다.
print(my_all([[], 2, 5, '6'])) 이 틀리게 나온다.
# =>>> 'break'가 필요!!
```



### 3번 문제

```python
def my_any(elements):
    for i in elements:
        if bool(i) == True:
            return True
    else:
        return False
```



교수님 답안

```python
def my_any(elements):
    # 통의 모든 요소 => for
    for i in elements : 
        # 조건: 요소가 참인지 확인 => True
        if i :
            return True
    return False
```

