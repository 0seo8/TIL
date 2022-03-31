# Git 블로그 만들기

```shell
//github 레퍼지토리 생성 (★레퍼지토리 이름 {user.name}.github.io)
$ git clone {github_url}
//hexo-cli설치
$ npm install hexo-cli -g
$ hexo init { 폴더명 }
$ cd { 폴더명 }
$ npm install
$ hexo server

//Writing 포스트 만들기
$ hexo new post "My first post" ⭐
$ vi source/_post/My-first-post.md

//localhost:4000 
$ hexo server

//github 레퍼지토리와 연결 (_config.yml에서 수정)
$ vi _config.yml

	*Deployment* 수정
              type: git
              repo: { github의 url주소}
              branch: main

//deploy : 자동으로 업데이트 될 수 있도록 설정
$ npm install hexo-deployer-git --save

       
// clean & deploy (※ && 앞 명령을 하고 성공하면 뒤 명령을 해라)
$ hexo clean && hexo deploy
```

**Writing(hexo의 기본 레이아웃)**
- `post`, `page`, `draft `
- `page`: 빈페이지, `post` : 블로그포스트 레이아웃이 입혀진 상태

## 테마바꾸기

가장 안정적으로 사용되는 테마인 hexo-theme-next를 사용. 

```shell
$ npm i hexo-theme-next //hexo관련 명령어들은 vi _config.yml가 있는 폴더에서 진행

$ vi _config.yml
	//Extentions의 theme을 next로 설정
    
$ hexo clean && hexo deploy
```






