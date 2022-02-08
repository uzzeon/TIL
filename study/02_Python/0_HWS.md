# HW & WS 배운 내용



## 1일차

- python 예약어 불러오기

  ```python
  import keyword
  print(keyword.kwlist)
  #> ['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert' ...]
  ```
  
- 실수 비교

  - **print(abs(num1 - num2) <= 1e-10) : `1e-10`**
  - `math. isclose(a, b)` : a와 b가 근접하면 True, 그렇지않으면 False 반환

- String interpolation

  ```python
  name = "'철수'"
  print('안녕, %s야' % name)
  print("'안녕, {0}야'".format(name))
  print(f'"안녕, {name}야"')
  ```

  - `%d` 정수 / `%f` 실수(소수점 6자리) / `%s` 문자열 

​	

 - 문자열 포맷팅

   - % 연산자 : `%` 와 출력하려는 데이터 값 사이에 띄어쓰기가 있어야 한다

     ```python
     fruit = "'사과'"
     num = 4
     print("나는 %s를 %d개 먹었다." % (fruit, num))
     ```

   - Format() 함수 : 출력하려는 문자열 안에 필요한 만큼 `{}` 를 넣어준 뒤 문자열 뒤에서 `.format()` 호출

     ```python
     print("나는 {0}에 {1}을 먹었다.".format("1월23일", "육회"))
     print("나는 {날짜}에 {음식}을 먹었다.".format(날짜 = "1월23일", 음식 = "육회"))
     ```

   - 더하기

     ```python
     name1 = "영희"
     name2 = "철수"
     print(name1 + "는 " + name2 + "를 좋아한데요!")
     ```

   - f-string : `f'{변수}'` 

     ```python
     a = 5
     b = 2
     print(f'{a}x{b}={a*b}')
     #> 5x2=10
     
     a=5
     for b in range(10):
         print(f'{a} x {b} = {a*b:2}')  # `:2` 라고 해서 두자리로 맞춰짐
     ```



- 네모 출력 : 줄바꿈을 더해주기 `+ '\n' `

  ```python
  n = 5
  m = 9
  print(('*' * n + '\n') * m)  
  ```

  

## 2일차

- 변경 가능한 (mutable) : List, Set, Dictionary

- 변경 불가능한 (immutable) : String, Tuple, Range

- `end = ' '` : 보통 출력은 줄바꿈이 디폴트이지만, 그냥 띄어쓰기만 하게 됨 cf. `end = ', '` 

- dictionary 만들기

  ```python
  a ={
      '이름' : '나이',
      '김싸피' : 25,
      '홍길동': 14
  }
  
  print(a)
  ```

- CF. *로 트리 비슷한 모양.. (?) 만들기

  ```python
  n = 5
  m = 9
  for i in range(m):
      for j in range(n):
          print('*',end='')
      print('')
  ```
  
- **계단 만들기 ★ (ws #3)**

  ```python
  num = int(input())
  
  # 4를 넣으면 4줄 출력 : 4번 반복
  for i in range(1, num+1):
      # 줄마다 입력되는 숫자 수 늘어남: 1째줄에서는 1개, 2째줄에서는 2개
      for k in range(1, i+1):
          print(k, end = " ")
      # print(' ')는 두 번째 for문이 끝나면 결괏값을 다음 줄부터 출력하게 해주는 문장
      print()
  ```

  



## 3일차 

- 딕셔너리들로 이루어진 리스트

  ```python
  students = [{'name': 'lee', 'age': 12}, {'name': 'kim', 'age': 4}]
  
  '''
  input : 리스트 (딕셔너리로 이루어진)
  output : 숫자 (나이 합)
  '''
  def dict_list_sum(stduents): #()안에 dict라고 쓰면 스스로 헷갈리 수 있음
      sum = 0
      for student in students: #student는 개별 딕셔너리
          #원하는 것은 students 개별 딕셔너리의 age 값 : student['age']
          sum += student['age']
      return sum
  ```
  
  - students 개별 딕셔너리의 'age' key에 해당하는 value 값 : **student['age']**



- cf

```python
def all_list_sum(lst):
    res=0
    for i in lst:
        if type(i) == list:
            res+ = all_list_sum(i)
        else:
            res+=i
    return res

all_list_sum([[1]]) >> 1
all_list_sum([[1],1,[1,1,1],[1,1]])
```



## 4일차 

- 내장함수 `chr(코드값_정수)` : 아스키코드값에 해당되는 문자를 반환
- 반대는 `ord(문자)` _ 반환된 숫자는 <class 'int'>
- `리스트명.append(추가 요소)` 함수는 list 제일 오른쪽에 요소 추가. 




## 예시 문제

- for 반복문 사용시 return의 위치 ★

  ```python
  def is_id_valid(user_data):
      # print(type(user_data['id'][-1])) = 'str'
      
      for i in range(0,11):
          if user_data['id'][-1] == str(i):
              return True
      return False
  ```

  - `for문` 다 돌면서 조건문 확인했는데도 True 가 안나오면 → False : `for문` 다 돈 다음!!! 위치 중요




- 달팽이 문제 (재귀로 풀기)

  ```python
  def snail(height, day, night, cnt):
      height -= day
      if height <= 0:
          return cnt
      height += night
      return snail(height, day, night, cnt+1):
  ```

  

## 5일차 

- HW 3번 <신기한 답안. 참고>

```python
def only_square_are(L1, L2):
    value = set(L1) & set(L2)
    return [i**2 for i in value]
```

- set은 수학의 집합 개념이라는 점!
  - `ㅣ` 합집합, `&` 교집합, `-` 차집합, `^` 대칭 차집합



- WS 2번 ★★ 대표적인 word counting 문제

  ```python
  # 딕셔너리 만들어서 현출하기...
  
  def count_blood(bloods):
      blood_dict = {} #답 담을 통을 만들고
      for blood in bloods: #리스트의 값을 하나씩 돌면서,,,
          if blood_dict.get(blood): #값이 나왔다는 건 blood_dict에 이미 값이 있다는 말
              blood_dict[blood] += 1
          else:
              blood_dict[blood] = 1 #해당 blood로 키를 만들고 1로 value 값
              
      return blood_dict   
  ```

  <교수님 답안>

  ```python
  result = {}
  for blood_type in blood_types:
      if blood_type in result:
          result[blood_type] += 1
      else:
          result[blood_type] = 1
  ```

  ```python
  result = {}
  for blood_type in blood_types:
      result[blood_type] = result.get(blood_type, 0) + 1
      # 에러가 뜨지 않게 초기 값을 0으로 두는 것
  ```

  

- 딕셔너리의 `.get()` 

  ```python
  dic = {'a': 10, 'b': 20}
  
  print(dic.get('a')) #>> 10
  print(dic.get('b', 0)) #>> 20
  #>> 키가 존재하면 해당 키 값을 호출하고, 존재하지 않는 키를 입력하면 괄호 안에 입력한 값인 '0'이 호출된다.
  print(dic.get('c', 0)) #>> 0
  ```

  

