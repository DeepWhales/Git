# Git 의 기초

* [컴퓨터 파일](https://ko.wikipedia.org/wiki/컴퓨터_파일)의 변경 사항을 추적하고 사용자들 사이의 작업을 조율하기 위한 [분산 버전 관리 시스템](https://ko.wikipedia.org/wiki/분산_버전_관리_시스템)
* 특징 : 빠른 수행 속도, 데이터 무결성, 분산, 비선형 작업 흐름 지원

## 분산 버전 관리 시스템

* [클라이언트-서버 시스템](https://ko.wikipedia.org/wiki/클라이언트-서버)과는 달리, 네트워크 접속이나 중앙 서버와 독립적으로 동작하는 완전한 이력 및 버전 추적 기능을 가짐

* 중앙 집중식 vs 분산 관리식

![Centeralized](https://homes.cs.washington.edu/~mernst/advice/version-control-fig2.png) vs ![Distribued](https://homes.cs.washington.edu/~mernst/advice/version-control-fig3.png)

* 이미지 출처 : [Version control concepts and best practices](https://homes.cs.washington.edu/~mernst/advice/version-control.html)

## 구성

* `.git` 숨김 폴더 : 모든 변경 내용이 저장되는 숨김 폴더 - `$ git init` 으로 생성할 수 있음
* `.gitignore` 파일 : Git 으로 추적하지 않는 파일들을 관리하는 숨김 파일 - [GitHub](https://github.com/github/gitignore) 에서 제공하는 파일 사용 가능

### `.gitignore` 파일 추가

`$ curl https://raw.githubusercontent.com/github/gitignore/master/Python.gitignore > .gitignore`

## 사용 방법

1. `CLI` : Git 자체의 명령어를 직접 사용 - Terminal, Cmd, ...
2. `GUI` : Git 을 위한 클라이언트용 GUI 툴을 설치하여 사용 - SourceTree, GitHub Desktop, ...
3. `IDE` : 거의 모든 통합 개발 환경은 Git 을 지원함 - VSCode, Xcode, ...

### SourceTree

* Atlassian 에서 제공하는 무료 Git 클라이언트 프로그램

# GitHub 

* Git 을 사용한 프로젝트를 지원하는 웹호스팅 서비스
- Git: 프로그램
- GitHub: 저장소 제공 서버
* Fork 기능 제공
- Clone : 원격 저장소에서 로컬 저장소로 복제함
- Fork : 원격 저장소에서 원격 저장소로 복제함

* Clone 과 Fork

![Clone & Fork](https://www.tomasbeuzen.com/post/git-fork-branch-pull/featured_hud478d74d48d19bfd1c1c03fc398c8033_312322_720x0_resize_lanczos_2.png)

* 이미지 출처 : [The Git Fork-Branch-Pull Workflow](https://www.tomasbeuzen.com/post/git-fork-branch-pull/)

## 참고 자료

* [Git](https://git-scm.com) : [Pro Git 한글판](https://git-scm.com/book/ko/v2)
* [Git - Wikipedia](https://en.wikipedia.org/wiki/Git)
* [GitHub](https://github.com)
* [svn 능력자를 위한 git 개념 가이드](https://www.slideshare.net/einsub/svn-git-17386752)
* [Version control concepts and best practices](https://homes.cs.washington.edu/~mernst/advice/version-control.html)