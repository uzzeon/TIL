# Day 03. 모듈과 패키지 

1. 모듈과 패키지
2. 파이썬 표준 라이브러리
3. 가상환경
4. 유용한 패키지와 모듈
5. 사용자 모듈과 패키지



## 1. 모듈과 패키지

모듈 : 특정 기능을 하는 코드를 파이썬 파일 단위로 작성한 것

패키지 : 모듈의 집합

- 불러오기 : `import` 

  ```python
  import random
  
  print(random.sample(range(1, 46), 6))
  ```

  ```python
  import pprint #pretty print  #from pprint import pprint
  a = {'a': ['apple'], 'b': ['banana'], 'c': ['car'], 'd': ['drive'], 'e': ['error', 'eat']}
  print(a)
  pprint.pprint(a)  #pprint(a)
  ```

  

## 2. 사용자 모듈과 패키지

- 모듈 만들기 - check
- 모듈 활용하기 - import 문을 통해 가져옴
  - from _______ import * #위에 실행 내역 지우고 확인해보기
  - import ____