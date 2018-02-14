---
layout: post
title: Node.js 개요 및 설치
categories: programming
tags: node.js
date: 2017-12-11 00:00:01 +09:00
comments: true
visible: 1
---

Node.js 가 웹서버 플랫폼으로 각광받고 있다. 자세히 알아보자

## 목차
{:.no_toc}

0. toc
{:toc}

## Intro
2009년 `Ryan Dahl`은 플리커의 파일 업로드 진행 표시줄을 보았을 때, 파일이 얼마나 업로드되었는지 알기 위해서는 서버에 쿼리를 전송해야 한다는 점을 보고 조금 더 쉬운 방법을 찾다가 고안해 내었으며, 그가 일하던 `Joyent`라는 회사에서 개발 및 운영을 담당하고 있다.[^1] <br/>
`V8 (자바스크립트 엔진)` 위에서 동작하는 `이벤트 처리 I/O 프레임워크이다`. 웹 서버와 같이 확장성 있는 네트워크 프로그램 제작을 위해 고안되었다. [^2] <br/>
*파이썬으로 만든 `트위스티드`, 펄로 만든 `펄 객체 환경`, 루비로 만든 `이벤트머신`과 그 용도가 비슷하다.* <br/>

<figure>
<img src="/assets/posts/20171211/101.png" width="400">
<figcaption align="middle">
&uarr;Node.js logo
</figcaption>
</figure>


**node.js** 는 `Javascript`언어를 사용하지만, 클라이언트(Client)가 아닌 서버(Server-side)에서 활용된다. Javascript와 Node.js를 활용하면, 한가지 언어로 클라이언트, 서버 모두를 관리할 수 있게 된다. <br/>

### Node.js 예시
```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

### Node.js 설치 준비
Node.js 는 `Windows`, `macOS`, `Linux` 등의 자주 사용되는 운영체제, 또한 `Docker`, `SunOS` 등 다양한 플랫폼에서 운영됨.

<!-- ad -->

## Node.js. 설치
Node.js 공식 홈페이지(한글): [https://nodejs.org/ko/](https://nodejs.org/ko/) <br/>
다운로드 페이지: [https://nodejs.org/ko/download/](https://nodejs.org/ko/download) <br/>

<figure>
<img src="/assets/posts/20171211/102.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>

### LTS와 Current의 차이
**LTS(Long Term Supported)**
- 장기적으로 지원이 제공되는 안정적인 버젼 (2017년 12월 7일자 최신: v8.9.2)
- 안전성에 초점을 두어 일반인이 사용하기 좋음

**Current**
- 가장 최신의 업데이트를 포함한 버젼 (2017년 12월 7일자 최신: v9.2.0)
- 안전성보다는 최신 업데이트를 초점을 두어 가장 최신의 기능이 필요한 개발자 등이 사용하기 좋음

복잡하지 않은 서버운영이 목적이기 떄문에 **macOS v8.9.2 LTS** 버젼을 받도록 하겠다.

설치진행
<figure>
<img src="/assets/posts/20171211/103.png" width="500">
<figcaption align="middle">
</figcaption>
</figure>

## 마무리
앞으로 다양한 `npm`들을 소개할 예정입니다.



[^1]: 출처: [wikipedia](https://ko.wikipedia.org/wiki/Node.js#cite_note-Node.js_pushes_JavaScript_to_the_server-side-3)
[^2]: 출처: [wikipedia](https://ko.wikipedia.org/wiki/Node.js#cite_note-Node.js_pushes_JavaScript_to_the_server-side-3)
