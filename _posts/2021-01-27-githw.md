## 1/25 github 과제 :+1:

1. git과 github의 차이점

2. init, add, commit -m 명령어들에 대한 설명

3. remote, clone, push, pull 명령어들에 대한 설명

4. 아래 사진을 첨부하기
사진 url : https://i.ytimg.com/vi/0nqJKEh3YCc/maxresdefault.jpg

5. branch, checkout 명령어 설명

6. merge 2가지 설명 (fast-forward/Merge conflict)

- - -

1.git과 github의 차이점

* git: Version Control System. git은 파일을 untracked, modified, staged, committed 상태로 관리한다. 즉 **프로젝트의 버전을 손쉽게 다룰 수 있게 해주는 시스템** 중 하나이다.

* github: `git` repository를 다른 사람과 공유할 수 있는 플랫폼. 이곳을 통해 협업할 수도 있고 자신이 관심있는 프로그램들이 무엇인지 알려줄 수도 있다. 

- - -

2.init, add, commit -m 설명

| init | add | commit -m
|:---:|---:|---:|
| 디렉토리를 git repository로 만들어 디렉토리 내의 파일을 git이 추적하게 한다. | `<FILE>`을 스테이징 한다. | 스테이징된 파일들을 커밋하여 하나의 버전으로 만들어 git 데이터베이스에 저장한다. `-m <MESSAGE>`로 커밋 메세지를 바로 입력할 수 있다.

- - -

3.remote, clone, push, pull 설명

-remote
  - `git remote add <NAME> <URL>` : `<NAME>` 이라는 별칭으로 `<URL>` 의 원격 레포지토리를 등록한다.
    - `git remote rm <NAME>` 으로 원격 레포지토리를 삭제할 수 있다.
    - `git remote rename <NAME> <NEW>` 으로 원격 레포지토리의 별칭을 수정할 수 있다.

-clone
  - `git clone <URL> <NAME>` : `<URL>` 의 원격 레포지토리를 가져와서 `<NAME>` 디렉토리에 복제한다.
    - 만약 디렉토리 이름 `<NAME>` 을 생략하고 `git clone <URL>` 으로 입력하면 원격 레포지토리의 이름으로 디렉토리가 자동 생성된다.

-push
  - `git push <NAME> <BRANCH>` : `<NAME>` 의 원격 레포지토리로 변경사항을 업데이트한다.
   - `git push origin master` 로도 업데이트 할 수 있다.

-pull
  - `git pull <REMOTE> <BRANCH>` : `<REMOTE>` 의 원격 레포지토리를 가져온 후 `<BRANCH>` 에 병합한다.
  
- - -

4.사진 업로드

![git commands](https://i.ytimg.com/vi/0nqJKEh3YCc/maxresdefault.jpg)


- - -

5.branch, checkout

-branch
  - git branch : 현재 상주하고 있는 브랜치를 출력한다.
  - git branch <NAME> : 새로운 브랜치 <NAME> 을 만든다.


- checkout
  - git checkout <NAME> : <NAME> 브랜치로 이주한다.
  - git checkout -b <NAME> : <NAME> 브랜치를 생성함과 동시에 이주한다.


- - -

6. Merge

-Fast-Forward
  - master 브랜치가 새로 만든 브랜치가 포인팅하고 있는 것을 커밋을 포인팅하게 되는 것.

-Merge Conflict
  - head가 가리키는 master 브랜치의 변경사항과 새로 만든 브랜치의 변경사항이 다를 때 충돌이 일어난 것. 




[참고링크](https://ccss17.github.io/ProgrammerBase/git/)
