# Python 제어문



- 위에서부터 아래로 순차적으로 명령을 수행

- 코드를 선택적 실행하거나 반복하는 제어가 가능

- 순서도(flow chart) 표현 가능



## 1. 조건문 

> 참, 거짓을 판단할 수 있는 조건식과 함께 사용

```py
num = int(input('숫자를 입력해주세요 : '))
print(num, type(num))

if num % 2 == 1:
    print('홀수입니다.')
else:
    print('짝수입니다.')

```

- `들여쓰기` 중요
- 자료형 중요! int 정수인가 문자열인가



### ⓐ 복수 조건문 : if ~ elif ~ else

### ⓑ 중첩 조건문

```py
dust = int(input('미세먼지 농도를 입력해주세요 : '))

if dust >= 151:
    print('매우 나쁨')
    if dust > 300:
        print('실외 활동을 자제하세요.')
elif 151 > dust >= 81:
    print('나쁨')
elif 80 > dust >= 31:
    print('보통')
else:
    if dust >= 0:
        print('좋음')
    else:
        print('값이 잘못 되었습니다.')

print('미세먼지 확인 완료')
```

- else 뒤에는 조건 오면 안된다.
- else 생략은 가능하다.
- `SyntaxError` : 문법 오류



### ⓒ 조건 표현식

```py
# 절댓값
value = num if num >= 0 else -num
```

```py
num = 5
result = '홀수' if num % 2 else '짝수'
print(result)
홀수
```



## 2. 반복문

- while 문 : 종료조건 필요
- for 문: 반복가능한 객체를 모두 순회하면 종료 (별도의 종료조건 불필요)
- 반복 제어:



### ⓑ For문

1. **문자열(String) 순회**

```python
chars = 'happy'
# # 1. 단순히 순회 (for)

for char in chars:
     print(char)

h
a
p
p
y
        
# 2. 인덱스로 접근 => 0 ~ 길이-1 (반복)
for idx in range(len(chars)):
    print(idx, chars[idx])
    
0 h
1 a
2 p
3 p
4 y
```



2. **딕셔너리(Dictionary) 순회**  

```py
grades = {'john': 80, 'eric': 90}

# 1. 딕셔너리 순회 => key !

for key in grades:
    print(key, grades[key])

john 80
eric 90

# 2. keys
for key in grades.keys():
    print(key, grades[key])

john 80
eric 90

# 3. values
for value in grades.values():
    print(value)

80
90

# 4. items
for key, value in grades.items():
    print(key, value)

print(grades.items())

john 80
eric 90
dict_items([('john', 80), ('eric', 90)])

# print(grades.keys())
# print(grades.values())
# print(grades.items())
```



3. **enumerate 순회** : enumerate(literable, start=0)

> (index, value) 형태의 튜플로 구성된 열거 객체 반환

```pyth
members = ['민수', '영희', '철수']

for idx, member in enumerate(members):
	print(idx, member)

0 민수
1 영희
2 철수

list(enumerate(members))
[(0, '민수'), (1, '영희'), (2, '철수')]

list(enumerate(members, start=1))  # 기본값은 원래 0
[(1, '민수'), (2, '영희'), (3, '철수')]
```

```python
# 반복문과 조건문만 활용해서 1~30까지 숫자 중 홀수만 출력하시오.

for i in range(1, 31):
    if i % 2 == 1:
        print(i) # 답이 쭉 나열
        
# 1-1. 빈통
numbers = []
for i in range(1, 31):
    if i % 2 == 1:
        numbers.append(i)
print(numbers) # [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29] 출력

# 1-2. 더 간단하게
numbers_2 = [i for i in range(1, 31) if i % 2 ==1]
print(numbers_2) # [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29] 출력
```



4. **list comprehension**

>  <expression> for <변수> in <iterable>

> <expression> for <변수> in <iterable> if <조건식>



### ⓒ 반복문 제어

1. **break** : 반복문 종료
2. **continue** : 이후 코드 블록은 수행하지 않고 다음 반복을 수행
3. **pass** : nth. 반복문 아니어도 사용 가능. 자리 채우는 용도
4. **else** : 끝까지 반복문을 실행한 이후에 else문 실행



## 3. Q &A

1. **list comprehension** 

```PYTHON
even_numbers = []

for i in range(1, 11):
    if i % 2 ==0:
        even_numbers.append(i)
print(even_numbers)

# 값을 초기화 => 1~10 짝수
even_numbers = [i for i in range(1, 11) if i % 2 == 0]
```

- 빈 통을 먼저 하나 만들고

  

2. **for-else**

```py
n = 6
for i in range(6):
	if i > 4:
		break
else:
	print('5 안넘음')
```

- break는 반복문을 종료
- break를 통해 중간에 종료되는 경우 else 문은 실행하지 않음

```py
while True:
	if __________:
		break
	print('hello')
```



3. **items vs enumerate** 

- enumerate() 는 함수
- .items 는 매서드(주어_ 동사의 개념). dictionary에서만 사용 가능하고, key와 value를 분리함
  - .upper() / .title()



4. **한줄로 출력 end=' '** 

   ```py
   cnt = 1
   
   while cnt < 11:
   	print(cnt, end=' ')
   	cnt = cnt + 1
   1 2 3 4 5 6 7 8 9 10 
   ```

   

   
