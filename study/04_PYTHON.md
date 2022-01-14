# PYTHON



## 0. 설치 & 실행

- 좌측 상단 File > New File
- 저장하기 (ctrl + s) - 파일명 hello.py
- 코드 작성 후 저장하기
- Terminal > New Terminal
- 터미널에서 python hello.py



- 파일에서 마우스 우클릭해서 `코드로 열기` 



## 1. 기본

- dust == 60 : dust에 저장된 값은 60과 같다.

- 글자는 `''` 를 붙여야 한다. 58은 숫자 / '58'은 글자

- 참/거짓: True, False 단 두 가지 (조건, 반복에 사용된다)
- ctrl + / : 드래그해서 한번에 주석처리 하는 방법



## 2. 변수 vs 리스트 vs 딕셔너리

- **변수** (박스1개) 

  - dust = 40 

- **리스트** (List) (박스 여러개)

  ```pyth
  dust = [58, 40, 70]
  print(dust[1])
  40
  ```

  - 리스트 안에 리스트가 들어가기도 한다.

  ```python
  lunch_box = ["kfc", "버거킹"]
  dinner_box = ['닭가슴살', '샐러드']
  meal_box = [lunch_box, dinner_box]
  
  print(meal_box)
  ```

- **딕셔너리** (견출지 붙인 박스)

  ```python
  dust = {'영등포구': 40, '강남구': 50}
  dust['영등포구']
  40
  ```

  ```python
  phone_book = {'강동원': '01012345678', '유승호': '0103456789'}
  print(phone_book)
  
  print(phone_book['강동원'])
  01012345678
  print(phone_book['강동원'], phone_book['유승호'])
  01012345678 0103456789
  ```

   - 전화번호는 숫자가 아니라 문자다

   - 숫자 0이 제일 앞에 나오면 error난다

     

- `nameError` : name ~~ is not defined : 만들지 않은 변수 
- `SyntaxError: leading zeros in decimal integer` : 숫자0으로 시작X



## 3. 흐름 제어하기

- 읽는 방법: ← 우측에서 좌측으로, ↓위에서 아래로, 안에서부터 밖으로 
- ctrl + n → crtl + s → dust.py



### ① 조건

```python
if True:
    print('조건문입니다.')
```

```python
dust = 60
if dust > 50:
    print('50초과')
else:
    print('50초과')

50초과
```

- indentation 기반으로 하고 있다. not {}.

```python
dust = 100
if 150 < dust:
    print('매우나쁨')
elif 81 <= dust <= 150:
    print('나쁨')
elif 31 <= dust and dust <= 80:
    print('보통')
else:
    print('좋음')
    print('여행가자~')
나쁨
```

- elif 부분에서 81 <= dust 라고만 써도 괜찮다. 순차적으로 작동하기 때문!!
- dust = 20 일때에는 '여행가자~' 도 출력된다. `Tap` 의 중요성!!



### ② 반복

#### `while` 

`while` 에 해당하는 조건일 동안 계속해서 반복

```python
greeting = 'Guten Tag!'
i = 0
while i < 3:
    print(greeting)
    i = i+1
Guten Tag!
Guten Tag!
Guten Tag!
```

- **종료조건** 이 반드시 필요
- 해당 조건이 False가 되면 종료된다.

#### `for` 

`for` : 정해진 박스 내에서의 반복 시 사용. '가지고 있는 모든 것을 꺼낸다'

```python
dust = [59, 24, 103]
for i in dust:
    print(i)
59, 24, 103
```

```python
# 통 : range(3)

greeting = 'Guten Tag!'
print(range(3))
print(list(range(3)))
for i in range(3):
    # i = 0, 1, 2
    print(greeting)

Guten Tag!
Guten Tag!
Guten Tag!
```

```python
# 런치박스의 메뉴를 하나씩 menu에 넣어줌
lunch_box = ['kfc', '버거킹', '맥도날드']
for menu in lunch_box:
    # menu = 'kfc', '버거킹', '맥도날드'
    print(menu)
    
    
# 런치박스의 길이(len)만큼 숫자들을 나열시키고 (range)
# 하나씩 i에 인덱스를 넣어줌
for i in range(len(lunch_box))
	# 인덱스에 하나씩 접근
    print(lunch_box[i])
```

- 종료조건이 필요 없다.



## 4. 함수

> 특정한 용도 어떤 작업을 반복하기 위해서 사용

- 파이썬 함수: Built-in (내장함수) / 비내장함수(?)
    - print('hi')	abs(-3) = 3 절댓값	len('hi') = 2 길이

- 모듈 : 많이 쓰는 함수를 묶어놓은 것

---



*import random* 제일 먼저 써주기



### ① random. choice(리스트)

> 리스트에서 임의의 요소 하나를 선택하는 것

```python
# 점심 메뉴 리스트를 만들고 출력해보자
# 모듈 불러오기 - 점심 메뉴 리스트를 만들기 - 하나를 랜덤으로 선택하여 - 출력한다.

import random 
lunch_box = ['삼겹살', '햄버거', '비빔밥', '마라탕']
today_menu = random.choice(lunch_box)

# print(random.choice(lunch_box)))으로도 가능함. 그치만 쪼개서 생각하는게 편하다.
print(today_menu)
```

- import random 안 치면, NameError가 뜬다



### ② random.sample(리스트, 개수)

> 리스트에서 특정 수의 요소를 임의적으로 비복원추출

```python
# random 모듈 불러오기 - 숫자 통 (1~46) - 숫자 통에서 6개 샘플 - 결과 출력

import random
numbers = range(1,46) 
	# range(n, m) : n이상 m미만
lotto_number = random.sample(number, 6)
print(lotto_number)
[3, 20, 35, 21, 18, 2]
```

- [1, 2, 3] : 인덱스 0, 1, 2 /// 길이 3
- (**tip**) 리스트는 복수형으로 써라! 'numbers'
- random.sample 결과는 항상 리스트에 담아서 추출된다.

```python
for i in range(5):
    lotto_number = random.sample(range(46),6)
    print(sorted(lotto_number))
    
[0, 14, 17, 30, 36, 44]
[19, 22, 23, 31, 35, 44]
[5, 34, 36, 37, 40, 45]
[0, 7, 20, 35, 40, 44]
[8, 22, 32, 34, 37, 45]
```

- `sorted` : 정렬

- `list`  :  요소들을 담고 있음. 반복 가능한 가변 시퀀스

  a = [1, 2, 3]  /// a = ['1', '3']

- `range`  : 숫자들의 불변 시퀀스

​		b = range(1,6)



```pyth
import random

def lotto_number_maker(n):
    # n번 반복
    for i in range(n):
    # 로또 번호를 추출
        print (random.sample(range(1,46), 6))

lotto_number_maker(5)

[19, 33, 32, 25, 6, 27]
[17, 40, 22, 27, 30, 34]
[33, 32, 8, 22, 31, 38]
[38, 35, 37, 19, 4, 45]
[24, 37, 15, 1, 11, 8]
```

