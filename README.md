# TIL
Today I Learn...

# Git

## 프로젝트 시작할 떄 두가지 방법

### clone의 방법
git허브에서 먼저 만들어서 작업하는 방법이 편하다.

#### 1. 레퍼지토리 생성
	- github에서 레파지토리 생성 (**단, ADD a README file 체크 후 생성**)
    - url복사	
#### 2. git clone { url }
레퍼지토리를 복사해고자 하는 폴더위치에서 `git clone` 명령어를 통해 레퍼지토리를 복사해온다.
```
$ git clone {url}
$ cd {저장소이름}
$ ls // 저장소 내부 파일, 폴더가 제대로 복사해왔는지를 확인
$ ls -a // .git이라는 숨김파일이 생성된 것을 확인할 수 있다.
