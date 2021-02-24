# Git 의 기초

* [컴퓨터 파일](https://ko.wikipedia.org/wiki/컴퓨터_파일)의 변경 사항을 추적하고 사용자들 사이의 작업을 조율하기 위한 [분산 버전 관리 시스템](https://ko.wikipedia.org/wiki/분산_버전_관리_시스템)

## 분산 버전 관리 시스템

* [클라이언트-서버 시스템](https://ko.wikipedia.org/wiki/클라이언트-서버)과는 달리, 네트워크 접속이나 중앙 서버와 독립적으로 동작하는 완전한 이력 및 버전 추적 기능을 가짐

* 중앙 집중식 vs 분산 관리식

![Centeralized](https://homes.cs.washington.edu/~mernst/advice/version-control-fig2.png) vs ![Distribued](https://homes.cs.washington.edu/~mernst/advice/version-control-fig3.png)

* 이미지 출처 : [Version control concepts and best practices](https://homes.cs.washington.edu/~mernst/advice/version-control.html)

* 특징 : 빠른 수행 속도, 데이터 무결성, 분산, 비선형 작업 흐름 지원

## 작동 방식

* `$ git init` 명령 실행 후, `.git` 숨김 폴더가 생기며, 여기에 모든 변경 내용을 저장함
* `.gitignore` 파일 : Git 으로 추적하지 않는 파일들을 관리, GitHub 에 있는 gitignore 파일들을 그대로 사용할 수 있음

## 참고 자료

* [Git](https://git-scm.com) : [Pro Git 한글판](https://git-scm.com/book/ko/v2)
* [Git - Wikipedia](https://en.wikipedia.org/wiki/Git)
* [GitHub](https://github.com)
* [svn 능력자를 위한 git 개념 가이드](https://www.slideshare.net/einsub/svn-git-17386752)
* [Version control concepts and best practices](https://homes.cs.washington.edu/~mernst/advice/version-control.html)