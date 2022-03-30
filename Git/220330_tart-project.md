# 프로젝트 시작할 때 두가지 방법

### 1. git clone의 방법
- git허브에서 먼저 만들어서 작업하는 방법이 편하다.
- clone은 remote로 원격 저장소 경로를 명시하지 않아도 된다.
>```shell
//github에서 repo를 생성 후(생성시 ADD a README file 체크)
$ git clone {repo address}
$ git add .
$ git commit
$ git push (origin main)
>```

**조금 더 자세한 정리**
```shell
$ git clone {url}
$ cd {저장소이름}
$ ls // 저장소 내부 파일, 폴더가 제대로 복사해왔는지를 확인
$ ls -a // .git이라는 숨김파일이 생성된 것을 확인할 수 있다.
$ vi READ.md
$ git status //Changes not staged for commit:   commit이 되지 않은 상태
$ git commit
$ git push
```

### 2. git init의 방법

사용자의 컴퓨터에서 local에서 부터 시작해서 remote로 끌어올리는 방법이다.

>
```shell
$ mkdir second-repo
$ cd second-repo
$ git init
>
// after creating remote repo on github,
$ git remote add mask {repo_url} : repo_url과 프로젝트 폴더 이름 일치시키기
>
$ git remote  // mask
$ git remote -v // :fetch할 때 url, push할 때 url을 받을 수 있다.
>
>//파일작업
>$ touch README.md
$ vi README.md
>
$ git status // branch name이 master인 것을 확인할 수 있다.
>
>// After doing some work,
$ git add { filename }
$ git commit
>
// branch name 맞춰주기
$ git branch -M main
// 아직까지는 localrepo와 remoterepo가 완전 다른 녀석(선언만 해놓은 상태)
$ git push -u mask main
    //>branch 'main' set up to track 'mask/main'.
```

### 🐥 git init을 잘못한경우

```
$ ls -a //을 통해 .git을 확인
$ rm -rf .git // .git폴더 삭제
```


