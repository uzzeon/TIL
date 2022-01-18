# Day2. 파이썬 실습



## 1. 개수 구하기

```python
fruit = ['딸기', '바나나', '수박']

count = 0
for i in fruit:
    count += 1
print(count)

# print(len(fruit))
```

- **count = 0** 변수를 초기화해야 한다. 



## 2. 득표수 구하기

```python
students = ['이영희', '김철수', '이영희', '조민지', '김철수', '조민지', '이영희', '이영희']

count = 0
for i in students:  #리스트 안에서 이영희라는 요소가 있을 때 count 1씩 증가
    if i == '이영희'
    	count += 1
print(count)
4

# students.count('이영희') 리스트에서 count 매서드!
```

- 실수: **==** 부분을 =으로 표기함



## 3. 최댓값 구하기

``` python
numbers = [7, 10, 22, 4, 3, 17]

# 1번

max_num = numbers[0]

for i in numbers:
    if i >= max_num:
        max_num = i
print(max_num)

# 2번

max_numbers = numbers[0]
for i in range(1, len(numbers)):
    if max_numbers < numbers[i]:
        max_numbers = numbers[i]
print(max_numbers)

# 3번
max(numbers)
```

- 알고리즘 문제 풀이 시: 값의 범위! → 가장 작은 수를 뭐라고 할까? 
- 초기 값을 어떻게 설정할 것인가? **첫 번째 요소** 로 잡고 시작하기



## 4. 최솟값 구하기

```python
numbers = [7, 10, 22, 4, 3, 17]

# 1번
min_num = j if j < min_num else min_num

# 풀어서 쓰면
if j < min_num:
		min_num = j
else:
		min_num = min_num

# 2번
min_num = numbers[0]
for i in range(1, len(numbers)):
    if min_num > numbers[i]:
        min_num = numbers [i]
print(min_num)
```



## 5. 최댓값 구하고, 몇 번인지 구하기

```python
numbers = [7, 10, 22, 7, 22, 22]

# 1번
# 최댓값 저장 변수, 횟수 변수 
# 처음 값 : 음의 무한대 값
# 최댓값이 같으면 카운트 증가, 아니면 1로 다시 초기화

maxi, cnt = float('-inf'), 1
for i in numbers:
    if maxi <= i:
        if maxi == i:
            cnt += 1
        else:
            cnt = 1
        maxi = i
print(maxi, cnt)


# 2번
max_num = numbers[0]
max_cnt = 0

for num in numbers:
    if num > max_num:
        max_num = num
        max_cnt = 0  
        
    if num == max_num:
        max_cnt += 1

print(max_num, max_cnt)
```

- float('inf') : 양의 무한대 (infinitive value) // float('-inf') : 음의 무한대



## 6. 5의 개수 구하기

```python
numbers = [7, 17, 10, 5, 4, 3, 17, 5, 2, 5]

# 1번
numbers_cnt = [i for i in numbers if i == 5]

print(len(numbers_cnt))

# 2번: count_num을 초기화, Find_num 변수로 지정
find_num = 5
count_num = 0
for i in numbers:
    if i == find_num:
        count_num += 1
print(count_num)

# 3번
count = 0

for i in numbers:
    if i == 5:
        count += 1
print(count)
```

-  찾고자 하는 숫자를 '대문자'로 : FIND_NUM (가독성)



## 7. a가 싫어 ★

```python
# 1번. 출력버전
# a를 만나면 continue하게 하고, end 넣어서 붙어서 출력되도록 함
# print(char, end ='\n')

word = input()

for char in word:
    if char == 'a':
        continue
    print(char, end='')
    
    
# 2번. 리스트를 만들어서 활용하기 => 결과문자열

word = input()
word = list(word)
result = []

for i in word:
    if i != 'a':
        result.append(i)
print(''.join(result))

# 3번. 리스트 만들어서 활용하기

word = input()

new_word = list()
for i in word:
    if i != 'a':
        new_word.append(i)
print(*new_word, sep='')

# 4번. 문자열

word = input()

while 'a' in word:
    word = word.replace('a', '')
print(word)

# 5번. list comprehension

word = input()
while 'a' in word:
    word = word.replace('a', '')
print(word)

# 6번.

word = input()

new_word = ''

for alphabet in word:
    if alphabet != 'a':
        new_word += alphabet
        
print(new_word)

# 7번.

result = ''

for i_word in word :
    if i_word == 'a' :
        continue
    else :
        result += i_word
        

print(result)
```

- join 매서드 

  ```py
  '!'.join(['banana', 'apple']) #사이에 넣을 것을 !에 쓰기. 공백을 넣을 거면 한 칸 띄어서
  ```

- word.replace('a', ""): replace 매서드

  ```python 
  # str.replace('이거를','이걸로') 교환
  
  'apple'.replace('a', '')
  'pple'
  
  'apple'.replace('a', '')
  'ale' 
  ```



## 8. 단어 뒤집기 ★

- 인덱스라면 i, idx 같은 변수 사용
- 요소라면 요소를 나타낼 수 있는 변수명을 지어주기

```python
# 1번. 인덱스 활용
# for문으로 단어의 길이만큼 시행하고 (range(len(word))) 거꾸로 출력하기 위해서 인덱스 활용

word = input()

for i in range(len(word)):
    print(word[-i-1], end='')

# 2번. 문자열 만들어가기 : 앞에 추가된다.

word = input()

new_word = ''

for alphabet in word:
    new_word = alphabet + new_word
    
print(new_word)

# 3번. 매서드

print(word[::-1])

# 4번.
word = input()

for i in range(len(word)):
    print(word[len(word) - int(i) - 1],end='')
```



## 9. 암기하기

- count 매서드 : ex. list.count('banana')
- float('inf') : 양의 무한대 (infinitive value) // float('-inf') : 음의 무한대
- replace 매서드 : ex. word.replace('a', " ") 
- join 매서드 : ex. '!'.join(['banana', 'apple']) => banana!apple
- list comprehension 어렵다: <expression> for <변수> in <iterable> if <조건식>