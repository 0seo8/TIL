# git flow

Git Flow는 Git으로 형상관리를 할때 브랜치를 효율적으로 관리하기 위해 사용하는 브랜치 관리 전략(Branch management strategy)이다.

git flow를 통해 프로젝트의 규모가 커져서 팀원이 늘어났을 경우 누군가는 하루 종일 conflict를 해결해야 하며, 이슈가 발생했을 때 개발한 코드를 다시 되돌리고 이러한 과정에서 개발을 멈춰야 되는 불편함이 있습니다.
물론 회사마다 프로젝트를 효율적으로 관리를 하는 방법이 있겠지만, 위와 같은 과정들을 최소화하고 형상관리를 효율적으로 하기 위해 생겨난 전략이라고 생각하면 될 것같습니다.

<img src ="https://images.velog.io/images/0seo8/post/e3359307-8f4c-4e3e-ada3-742f89f303ab/image.png" width="500px">

### branching models

- **git flow**
    - (hotfix)- `master -(release)`- `develop` - feature
    - pros: 가장 많이 적용, 각 단계가 명확히 구분
    - cons: 복잡..
     - main브랜치는 사용자가 직접쓰게될 단위의 커밋만 존재
	- develop라는 브랜치를 두고 자유롭게 작업을 함
    - 릴리즈 주기가 긴 프로덕트에 도입하기 좋은 모델
    - https://danielkummer.github.io/git-flow-cheatsheet/index.ko_KR.html
    
- **github flow**
    - `master` - feature
    - pros: 브랜치 모델 단순화, `master` 의 모든 커밋은 deployable
    - cons: CI 의존성 높음. 누구 하나라도 실수했다간..(pull request로 방지)
    
>**master** : 기준이 되는 브랜치로 제품을 배포하는 브랜치.
**develop** : 개발 브랜치로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합(Merge)친다.
**feature** : 단위 기능을 개발하는 브랜치로 기능 개발이 완료되면 develop 브랜치에 합친다.
**release** : 배포를 위해 master 브랜치로 보내기 전에 먼저 QA(품질검사)를 하기위한 브랜치.
**hotfix** : master 브랜치로 배포를 했는데 버그가 생겼을 떄 긴급 수정하는 브랜치.
    
 
## git flow 실습

**git flow는 가급적이면 프로젝트를 시작할 때, 다른 branch가 생기지 않았을 때 바로 도입을 하는 것이 좋다** 또한 항상 `git init`을 확인해 commit 않은 파일이 없는지 확인하고 시작하는 것이 좋다.

**작업환경설정**
```shell
$ git clone https://github.com/0seo8/git-flow-practice.git
$ cd git-flow-practice/
$ git branch 
```

**git flow**
```shell
/*초기화*/
$ git flow init // 나오는 프로세스 모두 엔터, 제공되는 이름을 그대로 사용하는 것이 좋다.
$ git branch // *develope main , "develope로 자동이동, develope위에서 시작"

/*feature생성*/ 
$ git flow feature start fizzbuzz
$ git branch   //  *feature/fizzbuzz   : "feature브랜치 하부에 fizzbuzz가 생성."

/* 작업 예시 */
$ touch fizzbuzz.py
$ vi fizzbuzz.py 
					//for _ in range(15):
                    		print('hello')
$ git add fizzbuzz.py
$ git commit -m "feat: Create fzzbuzz.py"
$ vi fizzbuzz.py    
                      //for i in range(1, 15+1);
                          if i%3==0:
                              print('fizz');
                          else:
                              print (i);
$ git add fizzbuzz.py
$ git commit -m "feat: Print fizz if i is times of 3"
$ vi fizzbuzz.py      // for i in range(1, 15+1);
                            if i%3==0:
                                print('fizz');
                            elif i%5==0:
                                print('buzz');
                            else:
                                print (i);
                                
$ git add fizzbuzz.py
$ git commit -m "feat: Print fizz if i is times of 5"
						
/* 기능 닫기 */ "fizzbuzz를 develope에 merge && fizzbuzz 삭제 && develop로 전환" 
$ git flow feature finish fizzbuzz // 작업을 완료하면 merge commit이 뜸(바로 닫아도 됨)
$ git branch // *developt main // feature/fizzbuzz가 사라짐.


/* 릴리즈  시작 */ "develpe로부터 release브랜치 생성"
$ git flow release start v0.0.1  [version naming 중요]

/* 릴리즈 완료 */ "release를 mater에 merge","release이름으로 tag","release를 develop로 재병합", "release삭제"
$ git flow release finish v0.0.1 

$ git branch // *develop main

/* branch  push */ 각각 branch를 push해주어야 합니다.
$ git push -u origin develop   : -u는 처음 만들 때만 해주면 됨.
$ git switch main
$ git push origin main 

/* 태그 push */
$ git push --tags  //특정한 설명을 추가하고 싶을 때
```
<img src="https://images.velog.io/images/0seo8/post/38c4a295-ca7d-4a80-8a78-f089e7258f51/image.png" >



>**릴리즈 완료**(`git flow release start v.0.0.1`)
- 2~3개의 창이 뜨게 된다.
- 1. Merge branch 'release/v0.0.1' into main : 바로 닫아도 괜찮음.
- 2. 태그가 적힌 release note 
  ```shell
  //작성예시
  implement fizz, buzz 
  >
  Print fizz if i is times of 3
  Print buzz if i is times of 5
  otherwise, print i itself.
  ```

