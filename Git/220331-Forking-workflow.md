# Forking Workflow
- 팀장의 저장소를 `Fork`해서 팀원마다 각각 저장소를 가지고 프로젝트를 하는 방식
- 각자의 저장소에서 자유롭게 작업을 진행하고 최종적인 팀원의 작업 내용은 Pull requests를 통해 팀장의 확인 후 반영된다.
- 팀장 저장소의 권한은 팀장만 가지고 있으면서 다른 사람의 커밋을 프로젝트에 적용이 가능하다.
- 오픈소스프로젝트에서 많이 사용하는 방식이다.

🐥: 팀장
🐣: 조원

## 팀장🐥
### 1. 팀장이 remote_repo를 생성한다.
### 2. 팀장이 본인의 로컬저장소에 클론을 해온다.
```shell
    $ git clone { URL }
    $ cd { 파일명 }
    $ git branch //*main
```
### 3. git flow를 이용해 작업 시작 `$ git flow init`
	- 대상 파일을 만들고 작업하는 경우 충돌이 자주 일어날 수 있기에 학습효과를 높일 수가 있다.
    
```shell
    $ git flow init
    
    $ git branch // *develop  main
    $ touch fizzbuzz.py
    $ git status // 확인
    $ git add fizzbuzz.py
    $ git commit -m "feat: Create fizzbuzz.py"
```
### 4. 작업한 내용을 원격저장소에 psuh
```shell
    $ git push -u origin develop
```

### 5. 팀원에게 가져가라고 메세지를 보냄

## 팀원🐣

### 1. 팀장의 해당 프로젝트의 github로 이동
### 2. fork를 이용해 전체 저장소 복제

- ⭐1번의 상태에서 바로 clone을 하지 않는다.
- 타인의 repo를 clone해서 바로 push할 수 있는 능력이 없다.
- 팀원의 저장소에 팀장의 저장소를 복사해와 작업을 한 후 팀장에게 작업한 내용을 **pull request**해달라고 요청


### 3. fork한 개인 원격 저장소에서 개인 로컬저장소 생성.

```shell
    $ git clone { copy_repo_url }
    $ cd { 파일명 }
    $ ls // LICENSE  README.md (작업한 파일을 확인하기 위해서는 develop브랜치로 이동해야한다.
    $ git branch //하지만 브랜치를 확인해보면 main브랜치 밖에 없는 것을 확인할 수 있다.
```   

### 4. issues작성
- 중앙 원격저장소의 isuues를 작성.
- 내가 어떤 기능을 만들겠다(suggest), 이 프로그램에 어떤 문제가 있다(bug report). 등을 작성.
```    
  ex) 
  I'll do fizzbuzz
   # Task list
      - [ ] do fizz
      - [ ] do buzz
      - [ ] do fizzbuzz
```

### 5. `$ git flow init`을 통해 초기화

```shell
    $ git flow init
    $ ls // LICENSE  README.md  fizzbuzz.py : fizzbuzz.py가 생긴 것을 확인할 수 있다.
```
> **어떻게 팀장이 작업한 fizzbuzz.py가 생성될 수 있는지?에 대한 이해 흐름**
>- 팀장의 remote_repo를 복사해왔기 때문에 팀원의 remote_repo를 확인해보면 `main`과 `develop`로 브랜치가 두개인 것을 확인할 수 있다.
>- 팀원의 remote_repo의 `develop`브랜치를 확인해보면 똑같이 fizzbuzz.py가 있는 것을 확인할 수 있다.
>- 따라서 local_repo에서 이름이 같은 `develop`브랜치를 만들면 당연히 상태도 똑같아야하기 때문에, fizzbuzz.py도 당겨오게 되는 것.

### 6. 기능 개발 시작

```shell
    $ git flow feature start do-fizzbuzz //do-fizzbuzz라는 브랜치 생성
    $ vi //작업시작
    
    //작업후
    $ git status
    $ git add fizzbuzz.py
    $ git commit -m "feat: Complete fizzbuzz"
```

### 7. 기능 개발 닫기 & 개인 원격 저장소에 push
```shell
    $ git flow featur finish do-fizzbuzz //이제 develop 브랜치에서도 do-fizzbuzz에서 했던 동작이 작동하게 된다. 
    
    $ git push -u origin develop // 첫 push니깐 -u를 붙여진행
```
### 8. 팀장에게 작업 내용 전달해 컨펌 받기	
    
   - 팀원 원격저장소에서 `compare & pull request` 누르기.(또는 `Contribute`버튼)
   - `compare & pull request` 클릭 후 이동된 팀장의 레포에서 화살표방향과 브랜치 꼭 확인( ⭐`base: develop`)  
    ![](https://images.velog.io/images/0seo8/post/a6b18c38-e6b7-4cea-98b6-8841f4c73da8/image.png)

>**issues 체크**
>- 개발을 끝낼 때마다 해당하는 \#1 (이슈넘버) 에 대한 해결사항을  Open a pull request 에 적어줘야 한다.
>-#를 눌러 해당 이슈를 자동완성시킬 수 있다.


## 팀장🐥

### 1. issues 
- Assingnees :본인
- Labels : enhancement
    
> #### issues 의 tag 의미
- **bug** 예기치 않은 문제 또는 의도하지 않은 동작(버그), 수정 시 close
- **duplicate**  해당이슈 또는 PR이 기존에 있음, 원본에 링크를 남기고 close.
- **enhancement**  새로운 기능 요청 구현 시 close.
- **help wanted**  관리자가 문제 또는 PR 요청에 대한 도움요청 해결 시 close.
- **invalid**   이슈 또는 PR 요청이 더 이상 관련이 없음.(실현 불가능). 안 되는 이유를 쓰고 close.
- **question**  이슈 또는 풀 요청에 추가 정보가 필요함. 해결 or 납득 시 close.
- **wontfix**   문제 나 PR 요청에서 작업이 계속되지 않음. 이유를 쓰고 close.
- **documentation** 문서를 개선하거나 추가 할 필요가 있음

### 2. Pull requests
요청사항을 요구해야하는 상황이라고 가정.

**Conversation**
- Reviewers: 본인
- Assingees: 본인 + 팀원
- Lable: enhancement

**Files changed**

- `+`버틀을 눌러 코멘트 달기
	ex) It's not pythonic. Do fizzbuzz with 1 if statements

### Finish your review 
- Write 작성
	ex) Do tihs RIGHT AWAY!!!!
- 해당하는 라벨 클릭   
  - Comment: 단순한 조언
  - Approve: 승인
  - Request changes : 요청사항이 있는 경우
- Submit 


## 팀원🐣
요청사항이 있다고 가정한 상황.

### 1. 요청사항 확인
- technical issue에 대한 커뮤니케이션을 진행(코멘트에 대한 답 달기).
<img src="https://images.velog.io/images/0seo8/post/32252ccb-1cce-4a1f-a715-2c6548c7ee51/image.png" width="650px">
- 현재 ulgoon(팀원)의 develop가 **열려(Open)**있는 상태
  - 이 경우 ulgoon이 무엇인가를 변경하면 pull requests 아래에 쌓이게 된다.
  - 추가 수정사항이 생겼을 때 develop에서 작성을 해 바로 push를 하면 pull requests에 반영이 된다.
  - **팀장은 Open이 되었을 때 바로바로 Close** 해줘야 팀원들이 편하게 일을 할 수 있다.

### 2. 수정필요한 내용 수정
- **수정요청사항이 n개인 경우 각각 따로 수정하고 commit해야한다. 즉 n개만큼 커밋**

```shell
$ vi fizzbuzz
//1번 요청사항 수정 후 
$ git add
$ git commit 

$ vi fizzbuzz
// 2번 요청사항 수정 후 
$ git add
$ git commit 
```

### 3. push

```shell
$ git push origin develop
```
  
## 팀장🐥

### 1. Files changed
- viewed 체크
- Review changes

### 2. 확인 후 Merge pull request
- 팀장이나 리뷰한 사람이 진행을 한다.


## 팀원🐣
- 수정에 기여한 팀원 외 다른 팀원들은 develop가 바뀐 사항들에 대해 pull 해야한다.

### 팀장
- 본인 것이기 때문에 바로 pull을 받으면 된다.

```shell
$ git pull origin develop
```

### 팀원
- 팀원들은 remote를 해야한다.

```shell
//확인
$ git remote
$ git remote -v

//팀장의 레포 url 등록
$ git remote add upstream   //upstream의 경우 관습적으로 사용하는 alias
$ git remote -v

// upstream 당겨오기
$ git fetch upstream develop  
$ git merge FETCH_HEAD
```

> **upstream 당겨오기**
- 방법1 pull
- 방법2 fetch
  - 당겨서 해당 브랜치에 반영을 바로 하는 것이 아님
  - 당겨서 FETCH_HEAD라는 임시 브랜치에 담아놓음
  - FETCH_HEAD에 담긴 후에는 원하는 부분만 당겨올수도 있고 전체를 당겨올 수도 있음.
  (이 때 바로 당기게 되면 pull과 동일하게 동작한 것과 같다.)



여기까지가 한 사이클을 돌린 것이다. 여기서 feature브랜치를 가져와 작업을 하면 다른 사이클이 시작되는 것입니다.

```
$ git flow feature start fb-lc
```


---

참고자료
- 최우영 강사님
- [[Git] GitHub로 협업하기 - Forking Workflow](https://velog.io/@hyowon_lee/Git-GitHub%EB%A1%9C-%ED%98%91%EC%97%85%ED%95%98%EA%B8%B0-Forking-Workflow)
