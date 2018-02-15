---
layout: post
title: 동기(Sync) 와 비동기(Async)
categories: programming
tags: node.js
date: 2017-12-16 00:00:02 +09:00
comments: true
visible: 1
---

Node.js와 Javascript를 공부하다보면 `동기(synchronous)` 와 `비동기(asynchronous)`를 자주 접하게 됩니다. 차이와 활용예시에 대해 정리 해봅니다.

## 목차
{:.no_toc}

0. toc
{:toc}

## 동기 vs 비동기
Synchronous: <br/>
Adj (전문 용어) 동시 발생[존재]하는<br/>
Adj occurring at the same time; contemporaneous <br/>
(출처: [네이버 사전](http://endic.naver.com/enkrEntry.nhn?sLn=en&entryId=1b8ccfaec6c047ecb233a1b086bd656f))

현실에서 `동기`의 의미는 A일과 B일이 동시에 발생하는 것이다. 스마트폰을 컴퓨터에 연결하여 두 기기간의 데이터를 같게 `동기화`하기도 한다. 또, 여러 명의 선수가 수면 위에서 같은 동작을 연기하는 경기 종목인 `싱크로나이즈드` 도 있다. <br/><br/>
그럼 프로그래밍에서는? <br/>
동기식 구조에서 A코드와 B코드가 있을 때, A코드가 모두 진행될 때 까지 B코드는 대기한다.
> 현실 동기와 너무 다르다..

그럼 비동기는? <br/>
위와 같이 두 코드가 있고 A코드를 비동기식으로 동작시키면, A코드에게 '시작해라' 명령을 내린 뒤, B코드를 실행한다. 그리고 A코드는 수행이 완료되는대로 결과를 출력한다. <br/>
> 현실 동기/비동기 뜻과 전혀 부합하지 않는듯 해서 1차 혼란.

### 예시
앞서 fs(filesystem) 포스팅에서 다뤘던 메소드로 예시를 들어보겠다.
패키지를 하나 생성한 뒤, 패키지 루트 디렉토리에 `Read1.txt`, `Read2.txt`, `Read3.txt`를 생성하고 각각 "첫번째 파일", "두번째 파일", "세번째 파일" 입력 후 저장하였다.

#### 동기식
```js
// Sync.js
var fs = require('fs');

// Read File

// Sync -> Sync -> Sync
var Syncdata = fs.readFileSync('Read1.txt', 'utf8')
  console.log(Syncdata);

var Syncdata = fs.readFileSync('Read2.txt', 'utf8')
  console.log(Syncdata);

var Syncdata = fs.readFileSync('Read2.txt', 'utf8')
  console.log(Syncdata);
```

결과는 너무나 당연히(?)
```
첫번째 파일

두번째 파일

세번째 파일
```
위와 같이 순서대로 나온다. <br />
동기식 방법이기 떄문에, 첫번째 파일을 읽기 전까지 두번째 파일을 읽지 않고 대기한다, 첫번째 파일 읽기가 완료되면 두번째 파일을 읽고, 역시 세번째 파일 읽기는 대기상태이다. 두번째 파일 읽기가 완료되어야 비로소 세번째 파일을 읽게 된다.

#### 비동기식
```js
// Async.js
var fs = require('fs');

// Read File

// Sync -> ASync -> Sync
var Syncdata = fs.readFileSync('Read1.txt', 'utf8')
  console.log(Syncdata);

fs.readFile('Read2.txt', 'utf8', function(error, data){
  if (error) {throw err};
  console.log(data);
  });

var Syncdata = fs.readFileSync('Read2.txt', 'utf8')
  console.log(Syncdata);
```

결과는..
```
첫번째 파일

세번째 파일

두번째 파일
```
위와 같이 `두번째 파일`과 `세번째 파일` 읽기 순서가 바뀌었다. 첫번째 파일을 읽은 뒤, 두번째 파일에게는 **명령** 만 내린 뒤, 바로 세번째 파일 읽기로 넘어간다. 세번째 파일을 읽는 도중 두번째 파일읽기도 완료 되었을테고, 세번재 파일 출력 뒤 바로 두번째 파일에 대한 출력이 나오게 되었다. <br />
조금 더 알아보고 싶어서 한가지 테스트를 더 해보았다. <br />
```js
// Async2.js
var fs = require('fs');

// Read File

// Sync -> ASync -> ASync -> Sync
var Syncdata = fs.readFileSync('Read1.txt', 'utf8')
  console.log(Syncdata);

fs.readFile('Read2.txt', 'utf8', function(error, data){
  if (error) {throw err};
  console.log(data);
  });

fs.readFile('Read3.txt', 'utf8', function(error, data){
  if (error) {throw err};
  console.log(data);
  });

var Syncdata = fs.readFileSync('Read4.txt', 'utf8')
  console.log(Syncdata);
```

이번엔 `Read4.txt`를 생성하고 두번째 세번째 파일은 비동기식으로 읽고, 첫번째와 네번째 파일은 동기식으로 읽어오도록 작성했다. <br />

결과는 아래와 같았다.
```
첫번째 파일

네번째 파일

세번째 파일

두번째 파일
```
위 패키지는 https://github.com/leechoong/Node.js-Sync-Async-test 에 올려 놓았습니다.

> 첫번째 뒤에 네번째 파일이 오는것은 어느정도 이해할 수 있겠는데, 세번째와 두번째 파일의 순서도 바뀌어있다.. 대혼란이다.

### 대혼란
첫번째 파일이 출력된 뒤, 두번째 파일은 비동기식이므로 명령만 내리게 된다. 그뒤, 세번째 파일에게도 명령을 내리고, 네번째 파일을 실행한다. 두번째 파일에 대한 명령은 분명히 세번째 파일에 대한 명령 보다 먼저 수행되었을텐데, 세번째 파일에 대한 출력이 먼저 나오는 것을 보면, 두번째 파일은 세번째 파일에 대한 코드에 의해 우선순위가 뒤로 물러난 것일까?


<!-- ad -->

## 블로킹, 논블로킹
동기와 비동기를 이해하고 싶어 검색하였더니, 블로킹과 논블로킹이라는 용어가 등장했다.
"블로킹 메소드는 동기로 실행되고 논블로킹 메소드는 비동기로 실행된다"
> ?

### 블로킹 (Blocking)
말 그대로 작업을 중단시킨다는 의미이며, 네트워크에서 요청이 완료될 때까지 다른 작업은 중단한 채 대기한다.

### 논-블로킹 (non-Blocking)
위 블로킹 개념과 반대되는 개념으로 네트워크에 다른 요청이 있어도, 기다리지 않고 다른 작업을 수행할 수 있다.

### Node.js는 Single Thread non-Blocking I/O model
다른 Multi-thread의 형태를 갖고 있는 `Apache`나 `Tomcat`등 서버는 `Thread Pool`에 여러 I/O Thread를 풀어놓고 필요할때마다 꺼내쓰는 식이다. 생성할 수 있는 Thread 에 한계가 있고 I/O효율에도 문제가 생길 수 있다. <br />

반면 Node.Js는 기본적으로 `Single Thread model`이다. 하나의 요청을 받으면 수행하다가 I/O작업을 던져놓고 다른 요청을 수행한다. 비동기식으로 요청받은 작업들은 이런 과정으로 수행하게 되는데, 이러한 작업을 진행하는 Thread를 `Event Loop Thread`라고 한다. <br />

<figure>
<img src="/assets/posts/20171216/201.jpg" width="500">
<figcaption align="middle">
Event loop Thread
</figcaption>
</figure>

I/O 요청이 온다면 이 요청들은 callback 요청 메세지와 함께 Event Queue에 저장된다. <br />
이때 Event Loop는 Queue에 있는 요청들을 불러내 `non-Blocking` 방식으로 처리를 하도록하며, 이때 완료된 작업은 다시 callback function의 형태로 반환시킨다. <br />

## 비동기의 활용
Single Thread 비동기 처리의 특징을 갖는 Node.Js는 어떤식으로 활용해야 할까? <br />
하나의 Thread에서 처리하기 때문에 복잡하고 페이지가 많은 웹 개발에는 적합하지 않을 것이다. 한 작업의 CPU 작업이 길 경우 전체 요청에 대한 응답이 지연된다. 그렇기 떄문에 가볍지만, 빠른 응답속도를 요구하는 프로그램에 적합하다.

## 마무리
정말 얕은 지식에 아직 모르는게 너무 많다. 동기, 비동기 관련 새롭게 알게 되는 내용이 있다면 수정할 예정이다.

> Queue 는 FIFO(First In First Out)으로 먼저 입력된 event가 먼저 출력되어야 할 것이다. 근데 Async2.js 테스트에서 3번째 파일 읽기와 2번째 파일 읽기의 순서가 바뀐 것은 아직도 잘 이해가 되지 않는다.. 허허

참고목록 <br />
1. https://nodejs.org/ko/docs/guides/blocking-vs-non-blocking/
2. https://stackoverflow.com/questions/10570246/what-is-non-blocking-or-asynchronous-i-o-in-node-js
3. https://www.linkedin.com/pulse/nodejs-event-loop-padmanabhan-pillai/
