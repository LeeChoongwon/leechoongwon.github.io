---
layout: post
title: Node.js로 멜론 순위 차트 데이터 파싱
categories: 
  - Node.JS
date: 2017-12-11 00:00:03 +09:00
comments: true
visible: 1
---

`Melon (멜론)`이 언제부터인지 신규 API의 신청을 받지 않고 있다. 개인적으로 진행하고 있는 프로젝트에 멜론 실시간 순위 데이터를 가져오고 싶어서 알아보던 중 데이터 크롤링을 할 수 있는 `npm package`을 알게되어 소개하고자 한다.

## 목차
{:.no_toc}

0. toc
{:toc}

## Intro
### 준비
- Node.js
- npm

## Project 준비

원하는 디렉토리에 프로젝트 폴더 하나 생성후 js파일 생성 <br/>
필자는 `crawling_test/melonchart.js`

`Terminal`에서 프로젝트 폴더 진입
```sh
$ cd crawling_test/
```

Package 생성
```sh
$ npm init
```

```
package name: (crawling_test)
version: (1.0.0)
description: melon crawling test
entry point: (melonchart.js)
test command:
git repository:
keywords:
author:
license: (ISC)
```

## npm 설치
### Cheerio
Node.js에서 HTML 데이터 파싱을 하기 위해 Cheerio를 사용.
> Fast, flexible, and lean implementation of core jQuery designed specifically for the server
 [https://www.npmjs.com/package/cheerio](https://www.npmjs.com/package/cheerio)

```sh
$ npm install cheerio
```

### Request
Cheerio에서 파싱할 데이터를 가져오는 역할을 Request가 합니다.
> Request is designed to be the simplest way possible to make http calls. It supports HTTPS and follows redirects by default.
[https://www.npmjs.com/package/request](https://www.npmjs.com/package/request)

```sh
$ npm install request
```


### npm 설치 확인

`crawling_test/package.json`
```
"dependencies": {
  "cheerio": "^1.0.0-rc.2",
  "request": "^2.83.0"
}
```
위와 같이 `dependencies` 밑에 cheerio와 request가 있으면 성공.

## 멜론 데이터 가져오기
```js
var cheerio = require('cheerio');
var request = require('request');
```
두 패키지를 불러옵니다.

```js
var url = 'http://www.melon.com/chart/';

request(url, function(error, response, html){
    var $ = cheerio.load(html);
})
```

`request` 이용하여 웹페이지 load.

### 데이터 확인

<figure>
<img src="/assets/posts/20171211/301.png" width="500">
<figcaption align="middle">
</figcaption>
</figure>

`class = "ellipsis rank01"` &rarr; `span` &rarr; `a` 에서 곡명 확인.

<figure>
<img src="/assets/posts/20171211/302.png" width="500">
<figcaption align="middle">
</figcaption>
</figure>

`class = "checkEllipsis"` &rarr; `a` 에서 아티스트명 확인.

## 데이터 파싱
```js
  $('.ellipsis.rank01 > span > a').each(function(){
    var title_info = $(this);
    var title_info_text = title_info.text();
  })

  $('.checkEllipsis > a').each(function(){
    var artist_info = $(this);
    var artist_info_text = artist_info.text();
  })
```
HTML script를 읽어가며 지정해준 클래스의 정보를 가져옵니다.

### 결과 #1
```js
console.log(artist_info_text + " - " + title_info_text);
} // 콘솔창 출력
```
```
성시경 - 나의 밤 나의 너
```
이렇게 **마지막 결과 (100위)** 만 가져오게 됩니다.
<figure>
<img src="/assets/posts/20171211/303.png" width="400">
<figcaption align="middle">
</figcaption>
</figure>

<!-- ad -->

### 결과 #1 수정
`배열`을 이용하여 지나간 값을 저장합니다.
```js
// 곡명 파싱
 for (var i = 0; i < 10; i++) {
   $('.ellipsis.rank01 > span > a').each(function(){
     var title_info = $(this);
     var title_info_text = title_info.text();
     title[i] = title_info_text;
     i++;
   })
 }

 // 아티스트명 파싱
 for (var i = 0; i < 10; i++) {
   $('.checkEllipsis > a').each(function(){
     var artist_info = $(this);
     var artist_info_text = artist_info.text();
     artist[i] = artist_info_text;
     i++;
   })
 }

 // 순위 제목 - 아티스트명
 for (var i = 0; i < 10; i++) {
   console.log(title[i] + " - " + artist[i]);
 }
}
```



### 결과 #2
```
기억의 빈자리 - 나얼
눈 (Feat. 이문세) - Zion.T
선물 - 멜로망스
좋아 - 민서
Beautiful - 윤종신
피카부 (Peek-A-Boo) - Wanna One (워너원)
그때의 나, 그때의 우리 - Red Velvet (레드벨벳)
밤이 되니까 - 어반자카파
좋니 - 펀치 (Punch)
LIKEY - 윤종신
```
무언가 이상합니다.. <br />
**아티스트가 두명 이상일 경우 아티스트가 밀립니다**

다시 수정합니다.

### 결과 #2 수정
```js
// 아티스트명 파싱
for (var i = 0; i < 10; i++) {
  $('.checkEllipsis').each(function(){
    var artist_info = $(this);
    var artist_info_text = artist_info.text();
    artist[i] = artist_info_text;
    i++;
  })
}
```
`> a`를 지워줍니다. `checkEllipsis` 밑에 여러 아티스트가 모두 있기 때문에 한번에 가져오기 위해서 `a`태그까지 내려가면 안됩니다.

### 결과 #3
```
기억의 빈자리 - 나얼
눈 (Feat. 이문세) - Zion.T
선물 - 멜로망스
좋아 - 민서, 윤종신
Beautiful - Wanna One (워너원)
피카부 (Peek-A-Boo) - Red Velvet (레드벨벳)
그때의 나, 그때의 우리 - 어반자카파
밤이 되니까 - 펀치 (Punch)
좋니 - 윤종신
LIKEY - TWICE (트와이스)
```
완성

### 번외
날짜, 업데이트 시간 등도 모두 웹페이지에서 가져올 수 있습니다.

## 최종 코드 및 결과
### 코드
```js
var cheerio = require('cheerio');
var request = require('request');

var url = 'http://www.melon.com/chart/';
var title = new Array(),
    artist = new Array(),
    up_date,
    up_time;
var rank = 10;  //10위까지 확인


request(url, function(error, response, html){
  if (!error) {
    var $ = cheerio.load(html);

   // 곡명 파싱
    for (var i = 0; i < rank; i++) {
      $('.ellipsis.rank01 > span > a').each(function(){
        var title_info = $(this);
        var title_info_text = title_info.text();
        title[i] = title_info_text;
        i++;
      })
    }

    // 아티스트명 파싱
    for (var i = 0; i < rank; i++) {
      $('.checkEllipsis').each(function(){
        var artist_info = $(this);
        var artist_info_text = artist_info.text();
        artist[i] = artist_info_text;
        i++;
      })
    }

    // 업데이트 날짜
    $('.year').each(function(){
      var date_info = $(this);
      var date_info_text = date_info.text();
      up_date = date_info_text;
    })

    // 업데이트 시간
    $('.hhmm > span').each(function(){
      var time_info = $(this);
      var time_info_text = time_info.text();
      up_time = time_info_text;
    })

    //xxxx년 xx월 xx일 오후/오전 xx시 format
    var up_date_arr = new Array();
    var up_date_arr = up_date.split('.');
    var up_time_arr = new Array();
    var up_time_arr = up_time.split(':');
    var newtime;

    // 오후 오전 삽입
    if (up_time_arr[0] >12) {
      up_time_arr[0] = up_time_arr[0] - 12
      newtime = "오후 "+up_time_arr[0];
    } else {
      newtime = "오전 " +up_time_arr[0];
    }

    // 콘솔창 출력
    console.log("< 멜론 차트 1 ~ "+rank+"위 >");

    // 순위 제목 - 아티스트명
    for (var i = 1; i < rank+1; i++) {
      console.log(i+ "위" + " " + title[i-1] + " - " + artist[i-1]);
    }
    // 업데이트 시간
    console.log("("+up_date_arr[0]+"년 "+up_date_arr[1]+"월 "+up_date_arr[2]+"일 "+newtime+"시에 업데이트됨)");
  }
});
```

### 결과
```
< 멜론 차트 1 ~ 10위 >
1위 기억의 빈자리 - 나얼
2위 눈 (Feat. 이문세) - Zion.T
3위 선물 - 멜로망스
4위 좋아 - 민서, 윤종신
5위 Beautiful - Wanna One (워너원)
6위 피카부 (Peek-A-Boo) - Red Velvet (레드벨벳)
7위 그때의 나, 그때의 우리 - 어반자카파
8위 밤이 되니까 - 펀치 (Punch)
9위 좋니 - 윤종신
10위 LIKEY - TWICE (트와이스)
(2017년 12월 11일 오전 11시에 업데이트됨)
```

## 마무리
모든게 독학이라 코드도 지저분하고 정신 없습니다.. 자유로운 지적 부탁드리며, 모든 파일은 [github](http://github.com/leechoong)에 올려놓았습니다. <br/>

Melon 홈페이지의 HTML 구성이 변경되면 다시 데이터를 가져와야 한다는 단접이 있지만, 웬만해서는 잘 바꾸지 않는거 같으니 당분간은 괜찮을듯 싶다.
