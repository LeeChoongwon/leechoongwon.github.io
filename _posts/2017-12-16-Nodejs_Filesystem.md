---
layout: post
title: fs (file system) 파일 입출력
categories: programming
tags: node.js
date: 2017-12-16 00:00:01 +09:00
comments: true
visible: 1
---

npm `fs` 를 활용한 기본적인 파일 입출력을 정리합니다.

## 목차
{:.no_toc}

0. toc
{:toc}

## Intro
fs는 file system으로 node.js환경에서 파일시스템에 접근, 사용할 수 있게 해 주는 npm 이다.
### 준비
```sh
$ npm install fs
```
npm install을 통해 fs 모듈을 설치
```
fs_test
├── app.js
└── package.json
```
app.js 파일을 만들어 fs 모듈을 사용할 수 있도록 포함시켜 줍니다.
``` js
var fs = require('fs');
```

## 파일 읽기
`.readFile `메소드를 사용하여 파일읽기를 수행합니다.
### 사용법
비동기: fs.readFile('filepath' , `encoding`, callback) <br />
동기: fs.readFileSync('filepath`, `encoding`)

### 예시

먼저 읽어올 파일을 생성합니다. `Read.txt`를 만들고 쓰고싶은 글을 작성한 뒤 저장합니다.
<figure>
<img src="/assets/posts/20171216/101.png" width="400">
<figcaption align="middle">
</figcaption>
</figure>

```js
// Read File

// ASync
fs.readFile('Read.txt', 'utf8', function(error, data){
  if (error) {throw error};
  console.log(data);
});

// Sync
var Syncdata = fs.readFileSync('Read.txt', 'utf8')
  console.log(Syncdata);
```

결과
```sh
Sync: Hello, My name is Lee Choongwon.
ASync: Hello, My name is Lee Choongwon.
```

## 파일 쓰기
`.writeFile` 메소드를 사용하여 파일 쓰기를 수행합니다.

### 사용법
비동기: fs.writeFile('filepath' , data ,`encoding`, callback) <br />
동기: fs.writeFileSync('filepath`, data ,`encoding`)
### 예시
```js
// Write File

// ASync
var data = "Welcome to my blog.";
fs.writeFile('WriteASync.txt', data ,'utf8', function(error, data){
  if (error) {throw error};
  console.log("ASync Write Complete");
});

// Sync
fs.writeFileSync('WriteSync.txt', data, 'utf8');
  console.log("Sync Write Complete");

```
결과 <br/>
```
Write Complete
```
파일출력이 잘 된것을 확인할 수 있습니다. `WriteSync.txt` 와 `WriteASync.txt` 를 확인합니다.
<figure>
<img src="/assets/posts/20171216/102.png" width="400">
<figcaption align="middle">
</figcaption>
</figure>

## 파일 확인
`.exists` 메소드를 사용하여 파일 확인을 합니다.

### 사용법
비동기: fs.exists( `filepath`, callback )
동기식: fs.existsSync ( `filepath` )
### 예시
```js
// File Exist?

// ASync
fs.exists('Read.txt', function (exists) {
 console.log("ASync 파일 존재?: ", exists);
});

fs.exists('Read2.txt', function (exists) {
 console.log("ASync 파일 존재?: ", exists);
});

// Sync
var exists = fs.existsSync('Read.txt');
console.log("Sync 파일존재?: ", exists);

var exists = fs.existsSync('Read2.txt');
console.log("Sync 파일존재?: ", exists);
```
결과
```
Sync 파일존재?: true
Sync 파일존재?: false
ASync 파일 존재?: true
ASync 파일 존재?: false
```

<!-- ad -->

## 파일 복사
`.copyFile` 메소드를 사용하여 파일 복사를 수행합니다.
### 사용법
비동기: fs.copyFile('filepath', 'dest_filepath', callback) <br />
동기: fs.copyFileSync('filepath', 'dest_filepath')

### 예시
```js
// File Copy

// ASync
fs.copyFile('Read.txt', 'ReadCopy.txt', function(error){
  if (error) {throw err};
  console.log('Read.txt 는 ReadCopy.txt로 복사됨');
});

// Sync
fs.copyFileSync('Read.txt', 'ReadCopy2.txt');
console.log('Read.txt 는 ReadCopy2.txt로 복사됨');
```
결과
```
Read.txt 는 ReadCopy2.txt로 복사됨
Read.txt 는 ReadCopy.txt로 복사됨
```

```
fs_test
├── Read.txt
├── ReadCopy.txt
├── ReadCopy2.txt
├── WriteASync.txt
├── WriteSync.txt
├── app.js
├── node_modules
├── package-lock.json
└── package.json
```

## 마무리
지금까지 fs 모듈을 이용하여 할 수 있는 단순한 작업들을 정리했습니다. 공부하면서 더 정리할것이 필요하면 추가로 포스팅 할 예정입니다.
