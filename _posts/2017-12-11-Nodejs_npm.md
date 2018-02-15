---
layout: post
title: npm 설치
categories:
  - Node.JS
date: 2017-12-11 00:00:02 +09:00
comments: true
visible: 1
---

`npm (Node Package Manager)`은 `Node.js`의 패키지 관리자이다. 다시말해, Node.js에서 사용가능한 모듈들을 패키지화 시켜서 모아둔 것이다. 미리 누군가가 만들어 놓은, 내가 필요한 기능을 하는 모듈을 가져와서 나의 프로젝트에 빌드하게되면, 개발 시간과 고생이 줄어들게 된다. <br />

## 목차
{:.no_toc}

0. toc
{:toc}

## npm 이란?
<figure>
<img src="/assets/posts/20171211/201.png" width="300">
<figcaption align="middle">
</figcaption>
</figure>

마치 레고와 같아서 여러 모듈을 가져다가 붙여서 큰 프로젝트를 만들 수 있게 되는 것이다. <br />

기존의 `github`등에서 개발자들이 자신의 모듈을 공유할 수 있었지만, 그 과정을 더욱 편리하게 하기 위해 `Isaac Z. Schlueter` 가 npm을 개발하게 되었다. <br/>

## npm 설치
npm은 `Node.js`설치 시 자동으로 설치된다. <br/>
Node.js 설치는 [여기](https://leechoong.github.io/articles/2017-12/Node.js-Intro)참고

## npm 사용
원하는 위치에 프로젝트 디렉토리 생성후 진입
```sh
$ cd project_directory
```
```sh
$ npm init
```
명령어를 실행하여 `package.json` 파일 생성

```bash
package name: (project_directory)
version: (1.0.0)
description: npm tutorial
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
```

차례대로 나오는 항목들을 입력하면
project_directory/package.json이 생성된다.
```json
{
  "name": "project_directory",
  "version": "1.0.0",
  "description": "npm tutorial",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

<!-- ad -->

### npm 설치 관련 명령어
```sh
$ npm install (패키지이름 or 주소)
```
패키지 설치시 사용하는 명령어이며, 뒤에 `-g` 입력 후 실행하면 글로벌 설치가 되서 다른 패키지에서도 사용할 수 있다.
```sh
$ npm update
```
설치된 npm의 업데이트 확인하고 진행한다.
```sh
$ npm ls
```
설치된 dependencies를 트리구조로 볼 수 있다.

## 마무리
다양한 명령어와 실제 npm의 사용은 추후에 다룰 예정.
