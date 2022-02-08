## 1. 기초 문법

- 들여쓰기 (Identation) : 4칸 들여쓰기

- 변수(Variable) : 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름

  - 객체(Object) : 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것... 파이썬은 객체지향 언어

  - 할당 연산자(=)를 통해 값을 할당함

  - type() : 변수에 할당된 값의 타입_ str 등

  - id() : 변수에 할당된 값의 고유한 아이덴티티 값이며 메모리주소

  - 변수 연산 :

  - 변수 할당: 

    - 같은 값을 동시에 할당할 수 있음

      ```python
      x = y = 1004 
      print(x, y)
      ```

    - 다른 값을 동시에 할당할 수 있음 

      ```python
      x, y = 1, 2
      print(x, y)
      ```

       - 각각 값을 바꿔서 저장하는 코드

         ```python
         x, y = 10, 20
         tmp = x
         x = y
         y = tmp
         print(x, y)
         20 10
         ```

         ```py
         y, x = x, y
         print(x, y)
         20 10
         ```

- 식별자(Identifiers)

  - 식별자 이름은 영문 알파벳, 언더스코어, 숫자로 구성
  - 첫글자에 숫자가 올 수 없음
  - 길이제한이 없고 대소문자를 구별함
  - 예약어로 사용할 수 없음 : False, None, True, as, and, asser, await, break 등

   - 사용자 입력

     - input([prompt]) : 사용자로부터 값을 즉시 입력 받을 수 있ㄴㄴ 내장함수
     - 주석(comment) : 한 줄씩 `#`을 사용하거나, `"""` 으로 표현, `crtl+/` (Vs code의 경우)

     

## 2. 자료형 분류

- Boolean Type : True, false

  - 0, '', [] : False /// [0], -1 등 : True

- Numeric Type : Int, Float, Complex

  - Int : 정수(integer), 매우 큰 수를 나타낼 때 오버플로우가 발생하지 않음

    - 2진수 : 0b / 8진수 : 0o / 16진수 : 0x

  - Float : 실수

    - 부동소수점

    - e = 10*17

      ```python
      10**100/3
      3.33333333333e+99
      ```

      ````py
      1e-1
      0.1
      ````

  - Complex : 복소수

    - complex(1, 2) = 1 + 2j

    - 실수 부분: real / 허수 부분: imag

      ```python
      a = ComplexNumber(1, 2) * self
      a.real = 1
      a.imag = 2
      ```





- String Type : 문자형

  - 작은 따옴표나 큰 따옴표를 활용하여 표기
  - immutable 문자열을 변경할 수 없음_ 특정 값 하나만 바꿀 수 없다. my string! 을 my string?으로 바꿀 수 없음
  - lterable 문자열을 순회 가능함
  - escape sequence : `\` 활용
    - \n 줄 바꿈, \t 탭, \0 널(null)  
  - string interpolation : 문자열을 변수를 활용하여 만드는 법
    - %d 정수, %f 실수, $s 문자열
    - str.format()
- None Type : 값이 없음을 표현하기 위한 타입
- 역슬래시 



## 3. 컨테이너 분류

> 여러 개의 값을 담을 수 있는 것으로 서로 다른 자료형을 저장할 수 있음

- 시퀀스형 (순서가 있다) = 리스트 / 튜플 / 레인지
- 비시퀀스형 (순서가 없다) = 세트 / 딕셔너리
  - 리스트, 세트, 딕셔너리 : 가변형 / 튜플, 레인지 : 불변형



### 리스트 (List)

>  순서를 가지는 0개 이상의 객체를 참조하는 자료형

- 가변자료형

- 대괄호 형태 [] 혹은 list()를 통해 생성

```python
boxes = ['A', 'B', ['apple', 'banana', 'cherry']]

len(boxes) = 3
boxes[2] = ['apple', 'banana', 'cherry']
boxes[2][-1] = [boxes b c][-1] = cherry
boxes[-1][1][0] = b
```



### 튜플(Tuple)

> 순서를 가지는 0개 이상의 객체를 참조하는 자료형

- 불변자료형
- 소괄호()
- 단일 항목의 경우 값 뒤에 쉼표를 붙여야 한다.

```python
a = 1,
print(a)
(1,)
b = 1, 2, 3
print(type(b))
<class 'tuple'>
```



### 레인지(Range)

> 숫자의 시퀀스를 나타내기 위해 사용

- 기본형 : range(n) 0부터 n-1까지의 숫자 시퀀스
- 범위 지정 : range(n, m) n이상 m미만
- 범위 및 스텝 지정 : range(n, m, s) s씩 증가시키기

```py
list(range(1, 5, 2))
[1, 3]
list(range(1, 3, -1))
[]
list(range(6, 1, 1))
[]
```



### 패킹/ 언패킹

> 컨테이너로 묶기 = 패킹
>
> 컨테이너 풀기 = 언패킹



### 셋(Set)

> 순서없이 0개 이상의 해시가능한 객체를 참조하는 자료형
>
> 수학의 '집합'과 동일한 구조

- 담고 있는 객체를 삽입 변경, 삭제 가능 _ 가변자료형

- 중복 없이 순서가 없는 자료구조

  ```py
  {1, 2, 3, 1, 2}
  {1, 2, 3}
  ```

- 빈 중괄호는 dictionary

  ```py
  blank = {}
  print(type(blank))
  <class 'dict'>
  
  black_set = set()
  print(type(set()))
  <class 'set'>
  ```

- 순서가 없어서 인덱스 접근이 불가능하다.

- 활용하기

  ```py
  my_list = {'서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산'}
  
  len(set(my_list))
  4
  
  set(my_list)
  {'광주', '대전', '부산', '서울'} #순서가 없다
  ```

  

### 딕셔너리(Dictionary)

> 순서 없이 키-값 쌍으로 이뤄진 객체를 참조하는 자료형
>
> key를 통해 value로 접근하는 것

- 키(key) : 해시가능한 불변 자료형만 가능 _ list는 키로 활용 불가능
- 값(values) : 어떤 형태든 관계 없음

- 중괄호{} 또는 dict()을 통해 생성

```python
dict_d = {'a': 'apple', 3:'삼', '지역': ['서울', '광주']}
dict_d['지역'][0]
'서울'
```

```py
my_dict = {'a': 'apple', 'b' : 'banana', 'a' : 'ant'}
print(list(my_dict))
print(my_dict)

['a', 'b']
{'a': 'ant', 'b':'banana'}
```



### 형 변환 (Typecasting)

- 암시적 형 변환 : 사용자가 의도하지 않고 파이썬 내부적으로...

  ```python
  True + 3
  4
  3 + 5.0
  8.0
  3 + 4j + 5
  (8+4j)
  ```

- 명시적 형 변환 : 사용자가 의도적으로
- `range`와 `dictionary`로 변환 불가능



## 4. 연산자 (Operator)

### ⓐ 산술 연산자

`/` 나눗셈 _ 항상 결과가 float.... ex. `2.0` 

`//` 몫

`**` 거듭제곱

`%` 나머지

```py
print(divmod(5, 2))
quotient, remainder = divmod(5, 2)
print(quotient, remainder)
(2, 1)
2 1
```



### ⓑ 비교 연산자

> 값을 비교하며 True / False 값을 리턴함

`==` 같음

`!=` 같지 않음

`is` 객체 아이덴티티

`is not` 객체 아이덴티티가 아닌 경우

 

### ⓒ 논리 연산자

`A and B` 모두 T일때 T

`A or B` 모두 F일때 F

`Not` T를 F로, F를 T로

- 단축평가

  - 결과가 확실한 경우, 두 번째 값은 확인하지 않고 첫번째 값 반환

  ```PY
  a = 5 and 4 # TT
  print(a)
  4
  
  b = 5 or 3 #TX
  print(b)
  5
  
  c = 0 and 5 #FX
  print(c)
  0
  
  d = 5 or 0 #TX
  print(d)
  5
  ```

  

### ⓓ 복합연산자

> 연산과 대입이 함께 이뤄짐

- 반복문을 통해 개수를 카운트하는 경우



### ⓔ 식별 연산자

### ⓕ 멤버십 연산자

> in / not in

```py
4 in (1, 2, 'hi')
False

'a' in 'apple'
True

'b' not in 'apple'
True
```



### ⓖ 시퀀스형 연산자

- 산술 (+)

  ```py
  [1, 2] + ['a']
  [1, 2, 'a']
  ```

- 반복 (*)



### ⓗ 인덱싱(Indexing)

- 값을 정리할때 `0`부터 시작하고 `-1`은 제일 마지막이다.
- `IndexError` 는 인덱스에 없는 것.



### ⓘ 슬라이싱(Slicing)

```py
(1, 2, 3)[:2]
(1, 2)

(1, 2, 3, 5)[1:4] #1포함 4미포함
[2, 3, 5]

[1, 2, 3, 5][0:4:2] #k간격으로 슬라이싱
[1, 3]

s[::] = 'abc'
s[::-1] = 'cba' #뒤집기
```



## 5. 파이썬 프로그램 구성 단위

- 식별자:
- 리터럴: 익혀지는 대로 쓰여있는 값 그자체
- 표현식: 새로운 데이터 값을 생성하거나 계산하는 코드 조각
- 문장: 파이썬이 실행 가능한 최소한의 코드 단위
- 함수: 특정 명령을 수행하는 묶음
- 모듈: 
- 패키지: 모듈과 프로그램 묶음
- 라이브러리: 패키지 모음



## 6. 요약 정리

숫자 / boolean / None

string 문자열의 나열

[list] mutable한 요소들의 시퀀스

(tuple) 변경불가능한 요소들의 시퀀스

{set} 중복 없는 요소들의 시퀀스 

{k: v} 딕셔너리 : key와 value들의 시퀀스