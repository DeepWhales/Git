# Git 명령어 정리

## References

* [Git 교과서](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9791165210885)

## Git 명령어

### `git config`

```
$ git config 
```

* `config` 명령은 환경 설정 파일을 직접 수정하지 않고 환경 설정을 할 수 있게 해줌
* '로컬 (local)' 과 '글로벌 (global)' 영역에서 설정을 할 수 있으나, '글로벌' 설정을 권장함

```
$ git config --global user.name "<user-name>"
$ git config --global user.email "<e-mail>"
```

* '글로벌 (global)' 영역에서 '사용자 이름' 과 '이메일 주소' 를 설정함
* '글로벌 (global)' 영역에서 사용자 등록을 하면 다음 명령으로 내용을 확인 가능함

```
$ cat ~/.gitconfig
```

### `git init`

```
$ git init
```

* 해당 명령을 실행한 디렉토리를 '깃 (git)' 저장소로 변경함 == 초기화
* `.git` 이라는 '숨김 폴더' 를 추가하여 이를 수행함
* 보통 `mkdir <directory>`, `cd <directory>` 명령 수행 후에 실행함

### `git commit`

```
$ git commit -am "message"
```

* 파일을 Stage 영역에 등록하는 작업과 Commit 메시지를 등록하는 작업을 동시에 처리함
* `git add .` 명령과 `git commit -m "message"` 명령을 한 번에 수행

```
$ git commit --allow-empty-message -m ""
```

* 메시지가 없는 빈 커밋 작성을 허용하는 방식 : 커밋 메시지가 없는 것을 권장하지는 않음

### `git diff`

```
$ git diff
```

* Working 디렉토리와 Stage 영역 사이의 변경 사항을 비교
* 변경한 파일을 Stage 에 등록한 후에는 아무 것도 출력하지 않음

```
$ git diff head
```

* Stage 영역과 최신 Commit 사이의 변경 사항을 비교
* HEAD 는 최신 커밋을 가리키는 포인터

```
$ git commit -v
```

* Commit 메시지를 작성할 때 `-v` 옵션을 사용하면 `vi` 에디터에 `diff` 내용 추가 가능함

### `git remote`

```
$ git remote -v
```

* 원격 저장소의 '별칭' 과 'URL' 을 확인할 수 있음
* 원격 저장소를 연결하면 'fetch' 와 'push' 두 개의 정보를 출력함

```
$ git remote add <remote-alias> <remote-URL>
```

* 로컬 저장소를 원격 저장소에 연결함
* `<remote-alias>` 는 원격 저장소 별칭으로 보통 `origin` 을 많이 사용함
* `<remote-URL>` 은 원격 저장소 주소로, 나중에는 '별칭' 만으로 접근 가능함

```
$ git remote rename
```

```
$ git remote show
```

```
$ git remote rm
```

### `git push`

### `git clone`

### `git pull`

### `git fetch`

* 원격 저장소에서 Commit 된 코드를 임시 'Branch' 로 내려받는 작업
* 내려받은 후 현재 'Branch' 와 자동 '병합 (Merge)' 을 하지 않음

### `git merge`

```
$ git merge <remote-alias>/<branch-name>
```

#### Work Flow

##### State

* 'Push' 는 서버의 마지막 'Commit' 과 Push 되는 'Commit' 을 병합함

* 원격 저장소에 Push 하려면, 자신의 '로컬 저장소' 를 최신 상태로 유지해야 함
* 즉, 자신의 저장소가 원격 저장소에 Commit 된 것보다 최신이어야 한다는 의미임

* 협업할 때는 순차적으로 Push 해야함
* Commit 이 순차적이지 않을 때 Git 은 Push 동작을 거부함
* Push 동작을 거부하면, Pull 또는 Fetch 로 자신의 로컬 저장소를 갱신해야 함
* 갱신 후에 다시 Push 할 수 있음

##### Conflict

* Git 이 최신 상태에서만 Push 를 허용하는 것음 충돌을 방지하기 위함임
* Pull 작업은 내려받은 Commit 들을 현재 Branch 로 자동 병합함
* Commit 내용이 순차적이지 않으면 병합 과정에서 충돌이 발생함

* Pull 과정에서 충돌이 발생하면, 이 충돌을 해결한 후 Commit 하고 Push 할 수 있음
* Git 은 이를 위해 Push 할 때 Commit 의 순차 기록을 확인함

* 권장 순서 : Pull > Coding > Commit > Pull > Push

### `git branch`

* Branch 는 가상의 작업 디렉토리, 공통된 Commit 을 가리키는 지점, SHA1 Hash 키를 가리킴
* 보통 Branch 를 생성하면 현재 Commit 을 가리키는 HEAD 를 기준으로 생성됨
* 기본 Branch 외에 새로 생성하려면 직접 `branch` 명령을 사용해야 함

```
$ git branch
```

* 생성한 모든 Branch 출력

```
$ git branch <branch-name> <commit-id>
```

* `<branch-name>` 만 입력하면 현재 HEAD 를 기준으로 새로운 Branch 생성
* `<commit-id>` 를 입력하면 지정한 Commit 을 기준으로 Branch 생성

### `git stash`

### `git clean`

### `git merge`

* Fast-Forward 병합
* 3-Way 병합

```
$ git branch -d <branch-name>
```

* 병합 후 불필요한 Branch 삭제

```
$ git branch --merged
```

* 병합을 완료한 Branch 만 보여줌 

```
$ git branch --no-merged
```

* 병합하지 않은 Branch 만 보여줌

### `git rebase`

* Commit 순서를 재배열함






