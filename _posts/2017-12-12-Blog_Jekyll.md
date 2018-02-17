---
layout: post
title: Jekyll 과 Github Page 연동 (macOS)
categories:
  - Jekyll
  - Blog
date: 2017-12-12 00:00:01 +09:00
comments: true
visible: 1
---

지금 이 블로그도 Jekyll을 Github Page와 연동해 운영하는 것이다. Jekyll에 대해 알아보자.


## Intro
### Jekyll 의 장단점
장점
1. **Static (정적)** 웹사이트로 속도가 빠르다
2. 글작성이 직관적인 **Markdown** 사용
3. 내 **입맛**대로 꾸미기가 가능하다

단점
1. Dynamic 웹사이트에 비해 처음 접근하기 어렵다.
2. Markdown 문법에 익숙하지 않으면 글 작성이 어렵다.
3. 단독으로 댓글기능이나 분석등이 불가능하다

Markdown 문법은 생각보다 단순했고, 댓글기능 등은 DISQUS 등을 이용하여 쉽게 가져올 수 있었다.

### Jekyll + Github pages 준비
macOS 에서 진행할 예정.
1. Xcode
2. Github 계정

## Jekyll 설치
먼저 Xcode 를 최신버젼으로 업데이트합니다. 한번 실행하여 `Command line tool` 설치
macOS 에는 `Ruby`가 기본적으로 설치되어있다. Ruby 설치를 할 필요는 없다. <br/>

Terminal에서
```sh
$ gem install jekyll
```

이로써 Jekyll이 설치된다.

<!-- ad -->

## Jekyll 시작하기

원하는 디렉토리로 이동한 뒤,
```sh
$ cd mydirectory/
```
```sh
$ jekyll new [github_username].github.io
```
> 나의 경우 leechoong.github.io

```sh
$ cd [github_username].github.io
```
생성된 폴더로 진입후,
```sh
$ jekyll serve --watch
```
명령어로 서버를 구동시킵니다.

테마에 bundle 설치가 필요하다면
```sh
$ sudo bundle install
```
뒤에
```sh
$ bundle exec jekyll serve --watch
```
명령어로 서버를 구동시킵니다.


`localhost:4000`을 브라우저로 접속하면,

<figure>
<img src="/assets/posts/20171212/101.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>

위와같이 Jekyll이 내 컴퓨터에서 구동되는것을 볼 수 있다.

## Jekyll 을 Github Page 에 업로드
github 계정이 없으면 www.github.com 에서 생성 후,
새로운 Repository 를 생성하는데, 이때 이름을 [username].github.io 로 설정한다.

Terminal을 다시 킨 후, 아까 생성한 Jekyll 폴더로 이동.
```sh
$ git init
$ git remote add origin [git주소]
$ git add .
$ git commit -m "initial commit"
$ git push origin master
```

> git 명령어는 다음에 정리할 예정.

본인의 github에 접속하여 보면, 생성한 repository에 로컬 폴더의 파일들이 업로드 된것을 볼 수 있다. <br/>

처음 업로드 시 시간이 좀 걸리기 때문에 한 `5분정도 후` 브라우저에서 [username].github.io에 접속하면, 위에서 localhost:4000에서 본 나의 Jekyll 홈페이지를 볼 수 있다.

## Jekyll 사용하기
기본적으로 Markdown 파일을 `_posts`에 저장하면 포스트를 작성할 수 있다. <br />
파일 이름은 `201x-xx-xx-제목.md`
파일 시작은
```md
---
layout: post
title:  "제목"
date:   201x-xx-xx xx:xx:xx +0900
categories: 카테고리
---
```
으로 작성해주면 된다. <br/>

## 마무리
Jekyll을 설치하고, Github Page와 연동하는 법을 정리해 보았다. <br/>
`markdown`을 사용해보니 생각보다 간단하고 직관적이라 글 작성하기가 편리한것 같다. 앞으로 열심히 이용해 볼 예정입니다. `:)`
