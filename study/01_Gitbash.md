# git

> 분산 버전 관리 시스템 (DVCS)



## 1. git 저장소 만들기 (init)

> Create an empty Git repository or reinitialize an existing one

```bash 
$ git init
Initialized empty Git repository in C:/Users/유지언/Desktop/first/.git/
```

* `.git`  폴더가 생성 => 버전이 기록되는 저장소
  * 해당 폴더를 지우게 되면 모든 버전이 삭제되니 주의
* `(master)` 



## 2. 버전 기록하기

### add 

> Add file contents to the index

```bash
$ git add 파일명
$ git add a.txt
$ git add my_folder/
$ git add a.txt b.txt
```

### commit

>  Record changes to the repository

```bash
$ git commit -m '커밋메시지'
<<<추가>>>
```

- 커밋 메시지는 항상 버전의 내용(해당 변경사항)에 대해서 나타낼 수 있도록 기록한다. 
- 각 커밋은 고유한 값을 가지고 있고, 값이 다르면 서로 다른 커밋이다.
  - 커밋 메시지를 변경하는 명령어 (`git commit --amend` ) 사용하는 경우 변경되니 주의하자.


### status

> show the working status

```bash
$ git status
```

```bash
$ git status

# 커밋할 변경사항들 (staging area)
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt

# 커밋을 위해 준비되지 않은 변경사항 (staging area에 안올라옴. working directory)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

# 트래킹되지 않은 파일들 (working direcotry)
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        c.txt
```

- 파일을 조작하는 방법은 총 4가지 "CRUD"
  - 생성 Create
  - ~~읽기 Read~~
  - 수정 Update
  - 삭제 Delete

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt
        new file:   c.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt
```



### log

> show commit logs

```bash
$ git log
```



## 3. git 파일의 라이프 사이클

[관련문서 - Git 기초](https://git-scm.com/book/ko/v2/시작하기-Git-기초)




- untracked : 커밋에 포함된 적 없는 파일
- tracked 
  - modified : 커밋에 의해 수정된 경우
  - staged : 커밋 되기 전 목록 (staging area)
  - commited : 커밋된 상태 

[관련 문서] 

!!이미지 파일 2개 수업자료에서 참고하기!!





### 기타

- `history` : Bash로 git 작업한 내역들은 따로 저장하거나 볼 수 있는 방법

- 명령하는 위치를 잘 봐야한다. 노란색 부분을 잘 봐야 한다.

  GIT_DIR! 는 적절하지 않은 위치라는 말. 너 나가!

  `add commit` : 해당 버전을 저장/기록하기

  

- ctrl+L : 화면 초기화 

- 명령어 `git` 하면 사용가능한 명령어가 쭉 나온다

- `head`  지금 내가 어디에 있는지 ... 여러 버전, 여러 commit 들이 있는데 그 중 내가 지금 보고 있는 상태가 무엇인지 알려줌

  



### 퀴즈

```bash
quiz/
	.git
	a.txt
	my_folder/
	
project/
	.git
	a.py
	b.py
	
내 폴더/
	마케팅/
	..
```

- quiz 폴더 이름을 변경해도 되는가? O
- quiz 폴더 이름 변경에 대한 기록이 남는가? X
- quiz 폴더 위치를 변경해도 되는가? △
  - project 폴더에는 옮기지 않는다.
    - .git 프로젝트 저장소로 옮기는 경우 내부에서 동작이 복잡하게 진행
  - 내 폴더는 이동 가능하다.
- my_folder는 지우면 복원 가능한가? △
  - 커밋된 변경사항은 무조건 복원 가능
  - 커밋되지 않은 경우는 절대 불가능

- 만약에 .git 폴더가 있는 저장소 내부에서 새롭게 .git을 만들어도 되나요? X
  - `git init` 명령어를 입력하려고 하는데 `(master)` 가 있다? 다시 생각해보기. 어떠한 폴더에 대해 저장폴더가 있다는 의미이기 때문
  - 