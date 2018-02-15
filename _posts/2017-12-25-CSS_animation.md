---
layout: post
title: CSS 애니메이션
categories:
  - CSS
date: 2017-12-25 00:00:01 +09:00
comments: true
visible: 1
---

CSS로 애니메이션 효과를?

## 목차
{:.no_toc}

0. toc
{:toc}

## CSS 애니메이션

### 예시
<style media="screen">
@keyframes example1 {
    from {background-color: red;}
    to {background-color: yellow;}
}
@keyframes example2 {
    0%   {background-color:red; left:0px; top:0px;}
    25%  {background-color:yellow; left:200px; top:0px;}
    50%  {background-color:blue; left:0px; top:100px;}
    75%  {background-color:green; left:200px; top:100px;}
    100% {background-color:red; left:0px; top:0px;}
}

.animation1 {
   width: fit-content;
   height: fit-content;
   background-color: red;
   animation-name: example1;
   animation-duration: 3s;
   animation-iteration-count: 10;
}
.animation2 {
    width: fit-content;
    height: fit-content;
    position: relative;
    background-color: red;
    animation-name: example2;
    animation-duration: 3s;
    animation-iteration-count: 10;
}
</style>

<div class="animation1">leechoong</div>
<div class="animation2">Hello World!</div>
<br />
<br />
<br />
<br />
위와 같이 색깔이 바뀌거나, 위치를 이동시키기가 가능하다.
### CSS 애니메이션 적용

먼저 적용시킬 html 파일에 클래스를 지정해 글을 작성한다.
```html
<div class="test1">TEST1</div>
```
이번에는 CSS로, 애니메이션 속성값을 입력한다.

```html
<style media="screen">
@keyframes animation1 {
    from {background-color: red;}
    to {background-color: yellow;}
}

.test1 {
   width: fit-content;
   height: fit-content;
   background-color: red;
   animation-name: animation1; /* 위에서 정의한 애니메이션 */
   animation-duration: 3s; /* 지속 시간 */
   animation-iteration-count: 100; /* 반복 횟수 */
}
</style>
```

위처럼 `from` 과 `to` 로 지정하거나 <br />
진행 % 별로 설정 가능

```html
<style>
@keyframes animation2 {
    0%   {background-color:red; left:0px; top:0px;}
    25%  {background-color:yellow; left:200px; top:0px;}
    50%  {background-color:blue; left:0px; top:100px;}
    75%  {background-color:green; left:200px; top:100px;}
    100% {background-color:red; left:0px; top:0px;}
}
</style>
```


## 응용
<style media="screen">
.animated_div {
width:fit-content;
height:fit-content;
padding: 10px;
background: #92B901;
color: #ffffff;
position: relative;
font-weight:bold;
font-size:20px;
padding:10px;
animation:animation3;
animation-duration: 5s;
animation-iteration-count: 5;
}

@keyframes animation3 {
0% {transform: rotate(0deg);left:0px;}
25% {transform: rotate(360deg);left:0px;}
50% {transform: rotate(-180deg);left:250px;}
55% {transform: rotate(+360deg);left:500px;}
70% {transform: rotate(0deg);left:500px;background:#1ec7e6;}
100% {transform: rotate(-360deg);left:0px;}
}
</style>
<div class="animated_div">응용</div>
