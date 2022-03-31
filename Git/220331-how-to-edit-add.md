# add,commmit 수정, 취소

---

# git의 유용한 명령어

## git add 취소

  - `git reset HEAD [file]` : file명이 없는 경우 모든 add를 취소


## git commit
### 1. commit 취소

```shell
// 상태확인
$ git log

//[방법 1] commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존
$ git reset --soft HEAD^

// [방법 2] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
$ git reset --mixed HEAD^ // 기본 옵션
$ git reset HEAD^ // 위와 동일
$ git reset HEAD~2 // 마지막 2개의 commit을 취소

// [방법 3] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제
$ git reset --hard HEAD^
```

### 2. commit 수정

**push 전에 해당합니다**

```shell
/* 가장 최근의 commit 수정 */
$ git commit --amend

/* 가장 최근~세번째 수정 */
$ git rebase -i HEAD~3 //1. 열린 창에서 수정하고 싶은 커밋 옆의 pick을 reword로 변경=>각각 커밋 창이 뜸.

```


## 3. git status 에 deleted 된 파일들 한번에 지우고 반영하기
  ```shell
 $ git add -u    --> -u 옵션의 의미는 update tracked files
 $ > git commit -m "Message"
 $ > git push
 ```

---
참고자료

 [커밋 메세지 수정하기](https://velog.io/@mayinjanuary/git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%84%B8%EC%A7%80-%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0-changing-commit-message)
