## 레포지토리를 구성하는 중요한 문서들

### README.md

README.md는 프로젝트를 설명하는 가장 중요한 문서이다. **프로젝트와 Repository를 설명하는 책의 표지와 같은 문서**로 README.md만 봐도 이 프로젝트가 어떤지를 판단할 수 있기 때문에 많은 개발자들이 README.md 파일을 작성하는데 많은 시간과 노력을 기울인다.
즉, README.md파일은 나와 동료, 이 repo의 사용자를 위한 문서라고 할 수 있다.

[angular](https://github.com/angular/angular)의 경우 README.md를 굉장히 잘 정리를 해놓았기 때문에 참고해서 작성을 하는 것도 좋다.

**기본 틀** : README.md파일 작성 전 복사해서 붙여넣고 작성하는 것을 권장한다.

```shell
# Project Name
Abstract your project in few lines.
see [project sample page](project link)
## Documentation
### Installation
To install,
`$ pip install sesame`
and run `$ python open_sesame.py`
### Supported Python versions
`>=3.6`
### More Information
- [API docs]()
- [Official website]()
### Contributing
Please see [CONTRIBUTING.md]()
### License
Sesame is Free software, and may be redistributed under the terms of specified in the [LICENSE]() file.
```

### .gitignore
.gitignore 는 git이 파일을 추적할 때, 어떤 파일이나 폴더 등을 추적하지 않도록 명시하기
위해 작성하며, 해당 문서에 작성된 리스트는 수정사항이 발생해도 git이 무시하게 된다.

특정 파일 확장자를 무시하거나 이름에 패턴이 존재하는 경우, 또는 특정 디렉토리 아래의 모든 파일을 무시할 수 있다.

```shell
# 주석을 달기 위한 Hashtag
# MacOS Setup
.DS_Store
# Python cache files
.py[cdo]
# Important files
/Important
# AWS key
key.pem
```

### .gitignore and .gitattributes

#### .gitignore: 특정파일 추적을 하고 싶지 않을 경우

```
*.java
*.py[cod]
```

>프로젝트에 맞는 .gitignore을 자동으로 설정해주는 사이트
https://www.toptal.com/developers/gitignore
- 어떤 os, 어떤 프레임워크에, 어떤 코드에디터를 쓸 것인지를 적어 create


#### .gitattributes: 파일단위, 디렉토리 별 다른 설정을 부여하고 싶을 경우
- git은 텍스트라인을 탐색한다. 하지만 os나 안드로이드는 깨질수 있다 그래서 텍스트라인 탐색하지 말고 그냥 올려야하기 때문에 .git 사용한다.
```
# Avoid conflicts in pbxproj files
*.pbxproj binary merge=union
# Always diff strings files as text
*.strings text diff
```


### LICENSE
**오픈소스 프로젝트에서 가장 중요한 License는 내가 만들 때에도, 배포할 때에도 가장 신경써야 하는 일 중 하나**이다.

기본적으로 회사에서 진행하는 프로젝트는 오픈소스가 아닌 경우가 많다. 만약 오픈소스를 가져다 쓰는 경우 우리 회사의 프로젝트가 오픈되어버릴 수도 있기에 라이센스를 체크하는 습관을 들이는 것이 중요하다.

가장 많이 사용하는 License는 다음과 같다.

- MIT License
	- MIT에서 만든 라이센스로, 모든 행동에 제약이 없으며, 저작권자는 소프트웨어와 관련한 책임에서 자유롭다.
- Apache License 2.0
	- Apache 재단이 만든 라이센스로, 특허권 관련 내용이 포함되어 있다.
- GNU General Public License v3.0
	- 가장 많이 알려져있으며, 의무사항(해당 라이센스가 적용된 소스코드 사용시 GPL
을 따라야 함)이 존재한다.

GPL을 하나라도 가져다 쓰면 내코드는 무조건 오픈을 해야하고 돈을 내야하기 때문에 주의해서 사용하는 것이 좋다.





