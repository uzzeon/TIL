# HW & WS 배운 내용



## 1일차

- python 예약어 불러오기

  ```python
  import keyword
  print(keyword.kwlist)
  
  ['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert' ...]
  ```

- 실수 비교

  - print(abs(num1 - num2) <= 1e-10) : `1e-10`
  - `math. isclose(a, b)` : a와 b가 근접하면 True, 그렇지않으면 False 반환

- String interpolation

  ```python
  name = "'철수'"
  print('안녕, %s야' % name)
  ```

  - `%d` 정수 / `%f` 실수 / `%s` 문자열 

- 네모 출력

  ```python
  n = 5
  m = 9
  print(('*' * n + '\n') * m)  
  ```

  - 줄바꿈을 더해주는 것:  `+ '\n' `



## 2일차

- 변경 가능한 (mutable) : List, Set, Dictionary

- 변경 불가능한 (immutable) : String, Tuple, Range

- `end=''` 메세지 연결 (한 칸 띄운채 연결)

- dictionary 만들기

  ```python
  a ={
      '이름' : '나이',
      '김싸피' : 25,
      '홍길동': 14
  }
  
  print(a)
  ```

- 두 개의 정수 n과 m이 주어졌을 때, 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 별(*) 문자를 이용하여 출력하시오. 단, 반복문을 사용하여 작성하시오.

  ```python
  # 1번 (ok. 혼자 작성 가능)
  n = 5
  m = 9
  for i in range(m):
      print('*'* n)
  
  # 2번 (생소)
  n = 5
  m = 9
  for i in range(m):
      for j in range(n):
          print('*',end='')
      print('')
  ```

  



## 3일차 

- 딕셔너리들로 이루어진 리스트

  ```python
  students = [{'name': 'lee', 'age': 12}, {'name': 'kim', 'age': 4}]
  ```

  - students 개별 딕셔너리의 age 값 : **student['age']**






## 예시 문제

- 출력 양식: 리스트로 구성된 딕셔너리

  ```python
  def f(temperatures):
   
  	list1 = []
  	list2 = []
  
  return {}
  ```

  

- 



- 달팽이 문제 (재귀로 풀기)

  ```python
  def snail(height, day, night, cnt):
      height -= day
      if height <= 0:
          return cnt
      height += night
      return snail(height, day, night, cnt+1):
  ```

  