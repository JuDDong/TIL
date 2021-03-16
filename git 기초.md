# git 기초

> 분산버전관리시스템(DVCS)

## 로컬 저장소 설정

~~~bash
$ git init
~~~

* `.git`폴더가 생성되고, 여기에 git과 관련된 모든 정보들이 저장된다.

## 기본 작업 흐름

모든 작업은 `touch`명령어를 통해서 파일을 만드는 것으로 대체

### 1. `add`

~~~bash
$ git add {디렉토리}
$ git add a.txt #특정 파일
$ git add my_folder #특정 폴더
$ git add a.txt b.txt #특정 파일들
$ git add . #현재 디렉토리(하위 디렉토리 포함)
~~~

* 커밋 대상 파일을 목록에 추가한다.
* Working Directory의 변경사항을 Staging Area상태로 변경시킨다.

#### add 이전

~~~bash
$ touch new.txt
$ git status
On branch master
Untracked files: #새로 만든 파일, tracking이 안되는 파일들
	#포함시키기 위해서는 git add 명령어 사용, Staging Area에 담기위해
  (use "git add <file>..." to include in what will be committed)
        new.txt	#파일 목록

nothing added to commit but untracked files present (use "git add" to track)
~~~

#### add 이후

~~~bash
$ git add new.txt
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   new.txt

~~~

### 2. commit

~~~bash
$ git commit -m 'new.ver.1'	#버전 저장
[master ec9a4ed] new.ver.1
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 new.txt

~~~

* `commit`은 지금 파일 상태를 스냅샷
* 커밋 메시지는 코드 변경사항(이력/버전/커밋)를 충분히 잘 나타낼 수 있도록 작성한다.
* 아래의 명령어를 통해서 지금까지 기록된 커밋을 확인할 수 있다.



#### log

~~~bash
$ git log -1 #최신로그 하나 출력
$ git log -n #최신로그 n개 출력
$ git log	#commit 로그 확인 가능
commit ec9a4edb1807d40fde952ab14076a06c4fe7dc95 (HEAD -> master)
Author: jo <cutecjh33@gmail.com>
Date:   Tue Mar 16 15:09:21 2021 +0900

    new.ver.1

commit 7a6b1ddcd8d608babfb21ccbb6c89ef49c473e9e
Author: jo <cutecjh33@gmail.com>
Date:   Tue Mar 16 13:46:47 2021 +0900

    c.ver.1

commit 63faa407e37eb77b578a6ba4efb91c7095c1a90b
Author: jo <cutecjh33@gmail.com>
Date:   Tue Mar 16 13:34:16 2021 +0900

    ver.2

commit c84207f0dd2bbca520b14e18f9ed66b4b5797c00
Author: jo <cutecjh33@gmail.com>
Date:   Tue Mar 16 13:27:51 2021 +0900

    ver.1
~~~

## 기본 명령어

### 원격저장소 설정

~~~bash
$ git remote add origin {url}
$ git remote add origin https://github.com/edutak/first.git
~~~

* 깃, 원격저장소(remote) 추가해줘(add) 오리진이라는 이름으로(origin) URL!
* 설정된 원격저장소를 확인하기 위해서는 아래의 명령어를 활용한다.

~~~bash
$ git remote -v
origin  https://github.com/JuDDong/first.git (fetch)
origin  https://github.com/JuDDong/first.git (push)
~~~

### push

~~~bash
$ git push origin master
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (10/10), 754 bytes | 377.00 KiB/s, done.
Total 10 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/JuDDong/first.git
 * [new branch]      master -> master
~~~

* origin 원격저장소로 push

#### git config - author

커밋을 남기는 사람에 대한 정보(이메일, 이름)을 설정함.

~~~bash
$ git config --global user.name '이름'
$ git config --global user.email '이메일주소'
~~~

* github 이메일 주소와 동일하게 지정하면, 커밋 기록이 github계정과 연동되어 표기
* 주의! 이 설정과 github 접근권한과는 관련없음
  * 윈도우 - 자격 증명 관리자

#### 자기소개 페이지

* 레포지토리이름을 `이름.github.io` 로 짓는다.



#### branch, 협업전략(git flow, github flow, PR+fork), git 추가 명령어(reset, invert)