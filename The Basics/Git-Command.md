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

### `git log`

```
$ git log --oneline
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

#### Rebase 

* Commit 순서를 재배열함
* Base : 새로운 Branch 가 파생되는 Commit - 공통 조상 Commit
* Rebase : 파생된 Branch 의 기준이 되는 Base Commit 을 변경한다는 의미
* Rebase 를 하는 이유
    - 복잡한 Branch 들로 이루어진 수많은 경로는 진행 상황을 파악하기 어렵게 함
    - Commit 진행 상황을 쉽게 파악할 수 있도록 단순화하기 위해 Rebase 를 함

#### 병합 (Merge) vs 리베이스 (Rebase)

* Merge 는 두 Branch 의 Commit 을 순차적으로 비교해서 최종 Commit 을 생성함
* Rebase 는 두 Branch 를 서로 비교하지 않고 순차적으로 Commit 병합을 시도함

* 결과
    1. 병합은 3-Way 병합의 경우 병합 Commit 이 있지만, Rebase 는 병합 Commit 이 없음
    2. Rebase 는 Branch 들 간의 HEAD 위치가 서로 다름 

* Rebase 는 병합되는 방향이 `merge` 명령과 반대임
    - 결국 Branch 가 가리키는 포인터 위치의 변경을 의미함
    - 그러므로 병합을 하는 Branch 로 가서 Rebase 를 해야 함

```
$ git rebase <base-branch>
```

* Rebase 명령을 실행하면 파생 Branch 의 Commit 들은 기준 Branch 의 마지막 Commit 으로 재정렬됨
* Rebase 는 기존 Commit 의 Hash 값을 변경함 : 포인터 위치가 변경되면서 기존 Commit 이 새 Commit 으로 대체되는 개념
* Rebase 는 Commit 위치를 재조정할 뿐 Branch 의 HEAD 포인터까지 옮기지는 않음

```
$ git checkout main
$ git merge <rebased-branch>
```

* 위와 같이 Rebase 를 실행한 Branch 를 다시 병합해야 함

```
$ git rebase --continue
```

* Rebase 과정에서의 충돌을 해결한 후 위와 같이 `rebase` 와 `--continue` 옵션을 같이 사용함

```
$ git rebase --abort
```

* Rebase 를 취소하는 옵션

```
$ git rebase -i <HEAD~3>
```

* `-i` 옵션을 사용하면 여러 개의 Commit 들을 하나로 묶을 수 있음
* 위에서 `<HEAD~3>` 은 HEAD 가 가리키는 곳으로부터 3 개의 Commit 들을 하나로 묶으라는 의미임

#### Rebase 에서 주의할 점

* Rebase 는 Commit 위치와 Hash 값을 변경함 : Rebase 는 외부로 코드를 공개하기 전에 Local 에서만 실행하는 것이 좋음
* 저장소를 외부에 공개했다만 공개한 순간부터는 Rebase 를 사용하지 않는 것이 원칙임
* 공개한 Commit 을 변경하려면 `revert` 를 사용하는 것이 더 좋음

#### 충돌 방지

* 개발 과정에서 병합 충돌을 최소화하고 예방하려면, `main` Branch 내용을 자주 Pull 하여 병합하는 것이 좋음
* 원격 저장소의 `main` Branch 를 모니터링하고, 변화된 부분을 즉시 반영하여 작업하면 충돌을 최소화하거나 예방할 수 있음

### `git reset`

```
$ git rest <option> <commit-id>
```

* 지정한 Commit 코드로 되돌아감
* 옵션의 종류 : `--soft`, `--mixed`, `--hard`
    1. `soft` : Stage 영역을 포함한 상태로 복원, `mixed` 와의 차이점은 'Stage 영역' 임
    2. `mixed` : 기본 옵션 상태
    3. `hard` : 실제 파일이 삭제된 상태로 복원, `mixed` 와의 차이점은 'Working 디렉토리' 임

#### Commit 합치기

* Reset 의 동작 원리를 이해하면, Commit 을 수정할 수 있음
* `git reset --soft` 는 `HEAD` 를 해당 Commit 으로 이동하고, 원본 내용은 Stage 에 남겨둠
* `git reset --soft HEAD~2` 로 2단계 전으로 Reset 하고, Commit 하면 두 Commit 을 합친 효과를 냄

#### Stage Reset 하기

```
$ git rest <file-name>
```

* `reset` 명령 다음에 Commit ID 대신 '파일 이름' 을 사용하면 해당 파일이 Unstage 상태가 됨
* 위 명령은 `git reset --mixed HEAD <file-name>` 의 줄임 형태임
* `git reset <commit-id> <file-name>` 을 사용하면 'HEAD' 대신 Commit ID 로 Reset 함

#### 작업 취소

* 수정 작업을 완전히 취소하려면 Working Directory 와 Stage 영역을 모두 제거하고 마지막 Commit 상태로 되돌려야 함
* `HEAD` 포인터는 가장 마지막의 Commit 을 가리킴

```
$ git reset --hard HEAD
```

* Reset 시점을 `HEAD` 기준으로 하면 해당 시점의 수정 작업을 삭제할 수 있음

#### 병합 취소

```
$ git reset --merge HEAD~
```

* 바로 이전에 병합한 Commit 을 Reset 하여 취소

### `git revert`

* Reset : 기존 Commit 정보 삭제
* Revert : 기존 Commit 을 남겨 두고 취소에 대한 새로운 Commit 생성

```
$ git revert HEAD 
```

* HEAND 포인터를 사용하여 직전 Commit 을 Revert 함

```
$ git revert <commit-id>
```

* Revert 는 한 번에 Commit 하나만 취소함, 여러 Commit 을 취소하려면 순차적으로 해야 함
* 임의의 Commit 취소

```
$ git revert <commit-id .. commit-id>
```

* 범위 지정 연산자로 여러 Commit 을 Revert 함 : **위의 설명과 모순이라 확인 필요함**

> 이론상 `git revert <commit-id .. HEAD>` 도 가능할 것 같은데 확인 필요함

```
$ git revert --manline <number> <commit-id>
```

* 병합 시점의 Commit ID 를 입력하면 해당 시점으로 Revert 하여 병합이 취소됨
* Rebase 한 병합은 Revert 하기 힘듦 : Rebase 로 인하여 병합 이전의 공통 조상 Commit 을 찾기 어렵기 때문

#### Reset 과 Revert

* Reset 과 Revert 는 동작을 취소하고 과거로 돌아간다는 점에서 비슷함
* 두 명령어를 분리한 것은 원격 저장소로 공유를 하고 있는지와 관련이 있음
* 저장소를 외부에 공유했으면 특정 Commit 을 삭제하는 것은 위험 : 저장소의 Commit 기록이 깨질 수 있음
* 외부로 공유한 저장소라면 Revert 를 사용하는 것이 좋음
* 로컬에서 작업할 때는 Reset 사용 가능

### `git tag`

### `git submodule`

```
$ git submodule add <remote-repo-url> <directory-name>
```

* 위 명령은 부모 저장소가 될 메인 저장소에서 실행함
* 자식 저장소를 등록할 때는 자식 저장소와 연결된 원격 저장소 주소를 입력함
* 부모 저장소에서 Submodule 을 등록하면 원격 저장소를 매개로 하여 자식 저장소를 복제함

#### Submodule Commit

* 메인 저장소가 자식 정보를 가지고 있으려면 이를 Commit 해서 저장해야 함
* 사실 Submodule 환경 설정 파일인 `.gitmodules` 만 등록해서 Commit 하고, 복제한 자식 저장소는 Commit 하지 않음

### 부모 저장소 Clone

* 부모 저장소를 Clone 하면 Submodule 정보만 복제하며 자식 저장소는 같이 복제하지 않음
* Submodule 의 저장소는 명령어로 직접 가져와야 함

```
$ cd child 

$ git submodule init 
$ git submodule update
```

* Submodule 의 `update` 옵션으로 관련된 자식 저장소를 복제함

### 부모 저장소 Update

* Submodule 로 구성한 부모, 자식 저장소 관계에서, 자식 저장소가 갱신되면 부모 저장소 설정 파일도 변경됨
* 즉, 자식 저장소의 코드를 수정하고 Commit 하면, 부모 저장소에도 새로운 Commit 이 발생함
* 부모 저장소를 정기적으로 Update 하여 Submodule 상태를 최신으로 유지해야 함

```
$ git pull origin main 

$ git submodule update
```

* 부모 저장소를 Pull 했다고 해서 모든 자식 저장소를 자동으로 Update 하지 않음
* 즉, Submodule 의 Update 는 위와 같이 별도로 명령을 실행해 줘야 함
