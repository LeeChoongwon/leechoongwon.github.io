---
layout: post
title: git 명령어 및 사용법
categories:
  - Git
date: 2017-12-19 00:00:01 +09:00
comments: true
visible: 1
---

버전관리에 대해 대충이나마 알게 되었다. git을 이용한 버전관리를 직접 해보자.


## git
git 은 버전관리 시스템 중에서 `분산버전관리 시스템`이라는 방법을 채용한 플랫폼이다. <br />
분산버전관리 시스템 (DVCS) 는 변경사항의 마지막 스냅샷을 가져오는 것이 아니라, 저장소 (repository)를 통째로 복사하여 관리한다.

## git 사용하기
### git scm 다운로드
https://git-scm.com
에서 본인 운영체제에 맞는 git을 다운받으면 된다.

나는 `macOS`에서 진행할 예정이다

### git 사용
프로젝트를 깃을통해 버전관리를 하기 전에 github 홈페이지에서 저장소를 먼저 만들어 준다.
https://github.com/

`new repository`를 클릭한 후,



<img src="/assets/posts/20171219/101.png" width="600" align="middle">

저장소를 생성한다.


그 다음 터미널을 실행한 뒤 <br />
```sh
$ mkdir git_test
```
로컬 저장소도 생성한다. `mkdir` 은 make directory로 디렉토리를 생성할 때 사용하는 명령어 이다. <br />
편의를 위해 원격저장소와 로컬저장소의 이름을 `git_test`로 맞췄다.

```sh
$ cd git_test
$ git init
```
`init`은 초기화 한다는 의미로, 컴퓨터에게 앞으로 이 로컬디렉토리는 깃의 로컬 저장소로 사용할 것임을 알려주는 것이다.

```sh
$ touch README.md
```
`README.md`는 마크다운(Markdown)언어로 작성되는 파일로, 저장소의 설명을 작성할 수 있는 파일이다. <br />
커맨드라인으로의 생성 말고도, github홈페이지에서 저장소를 생성할 때, 같이 생성할 수 있다.


<img src="/assets/posts/20171219/102.png" width="600" align="middle">

`.gitignore`파일은 git에서 무시할 파일들의 이름을 작성하는 파일이다.
`License`파일은 이 저장소 내의 프로젝트의 라이센스를 기재할 수 있는 파일이다.

```sh
$ git remote add origin "https://github.com/leechoong/git_test.git"
```
이 명령어는 원격 저장소의 주소를 로컬 저장소에게 알려주는 것이다.

```sh
$ git remote -v
```
이 명령어로 현재 로컬저장소가 알고있는 원격 origin 저장소가 무엇인지 확인한다.

현재 원격 저장소는 텅 비어있는 상태이고, 로컬 저장소는 README.md파일이 있다. README.md 파일을 커밋해보자

```sh
$ git add .
```
`.`은 모두 를 뜻한다. 로컬 저장소의 모든 파일을 추가한다.

```sh
$ git commit -m "initial commit"
```
위에서 추가한 파일들 모두에 "커밋 메세지"와 함께 커밋한다.
명령어를 입력하면
```
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 README.md
```
위와 같은 메세지로 변경될 파일을 확인할 수 있다.

```sh
$ git push origin master
```
원격 저장소로 push 한다.

<img src="/assets/posts/20171219/103.png" width="600" align="middle">


확인해보면 원격저장소에도 `README.md`가 추가된 것을 확인할 수 있다.

<!-- ad -->

## GUI
command line 은 명령어와 텍스트로 출력되다보니 직관적으로 알기 어렵다. <br />
간편하고 직관적으로 git기능을 사용하려면 gui툴을 이용하면 좋다. `github desktop`과 `sourcetree`만 소개하려 한다.

### github desktop
https://desktop.github.com (github desktop)
https://www.sourcetreeapp.com (sourcetree) <br />


<img src="/assets/posts/20171219/104.png" width="700" align="middle">
<div align="middle" style="font-size:80%;">
&uarr; github desktop
</div>
<br />

<img src="/assets/posts/20171219/105.png" width="700" align="middle">
<div align="middle" style="font-size:80%;">
&uarr; sourcetree
</div>
<br />

직관적으로 변경사항을 확인할 수 있고, 커밋 메세지 작성이나, 누가 커밋했으며 언제 했는지 등을 한눈에 확인할 수 있다

## 마무리
팀 협업으로 프로젝트를 진행할 때, 더 빛을 발하는 버전관리이다. 명령어도 위에 작성한것 외에 더 많지만, 현재 나에게 필요한 정도만 정리해 두었다.
