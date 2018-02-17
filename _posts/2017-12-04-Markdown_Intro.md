---
layout: post
title: 마크다운(Markdown) 개요와 문법
categories:
  - Markdown
date: 2017-12-04 00:00:01 +09:00
comments: true
visible: 1
---

그동안 `HTML`을 이용한 경험은 있지만  `마크다운(Markdown)`은 생소하기 때문에, 첫번째 포스팅으로 간단하게 앞으로 블로그 작성시 참고할 만한 `마크다운(Markdown)` 문법을 정리하고자 한다.


## 목차
{:.no_toc}

0. toc
{:toc}


## Markdown 이란?

<figure>
<img src="/assets/posts/20171204/101.png" align="middle">
<figcaption align="middle">
&uarr;Markdown logo
</figcaption>
</figure>

`마크다운(Markdown)`의 창시자 **John Gruber** 은 마크다운을 **text-to-HTML conversion tool for web writers**, 즉 텍스트를 HTML로 변환해 주는 도구라고 정의하고 있다.<br />
**easy-to-read** (읽기 쉽고) **easy-to-write** (쓰기 쉬운) 간단한 문법의 텍스트 형식으로 글을 작성하면 HTML의 구조로 변환해 주기 때문에 HTML의 문법을 배우지 않은 사람들도 쉽게 사용할 수 있다. <br />
개발자라면 흔히 사용하는 `Github`의 README.md 도 Markdown문서이다.

### HTML과의 차이?
HTML(HyperText `Markup` Language) 은 Markup 언어로, Markup과 Markdown의 차이를 이해해야 한다. 마크다운(markdown)은 일반 텍스트 문서의 양식을 편집하는 문법이고, 마크업 언어(markup language)는 태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어의 한 가지이다. <br />
사용자가 문서를 작성시 구조를 직접 웹페이지가 알아들을 수 있는 문법으로 표시하느냐의 차이이다.
HTML을 사용할 줄 아는 사람이면 <br />
`HTML`&rarr;`웹에 표현`이 가능하지만, 그렇지 않더라고 훨씬 단순한 Markdown 을 사용할 줄 안다면 <br />
`HTML`&rarr;`HTML로의 변환`&rarr;`웹에 표현` 이 충분히 가능하다.

### Markdown의 사용
- README 파일
- 각종 텍스트에디터

단순히 문서를 작성하는 것에 비해 훨씬 "있어보이는" 문서를 만들 수 있다.

<!-- ad -->

## Markdown 문법
필자도 가끔 Cheatsheet로 사용할 Markdown 문법을 정리해 보도록 하겠다.

### 헤더

```
# 가장 큰 제목
## 두번째 큰 제목
### 세번째 큰 제목
#### 네번째 큰 제목
##### 다섯번째 큰 제목
###### 여섯번째 큰 제목
```

### 목록
```
- 이충원
- 홍길동
- 임꺽정

1. 이충원
2. 홍길동
3. 임꺽정

* 이충원
  * 홍길동
* 임꺽정
```

- 이충원
- 홍길동
- 임꺽정
<br />

1. 이충원
1. 홍길동
1. 임꺽정
<br />

* 이충원
  * 홍길동
* 임꺽정

### 강조

*기울임* <br />
`*` 혹은 `_`으로 감싸준다.
```
큰 바다 넓은 *하늘을 우리는 가졌노라* (2018학년도 _대학수학능력시험_ 필적확인 문구)
```
*큰 바다 넓은 하늘을*  우리는 가졌노라 (2018학년도  _대학수학능력시험_  필적확인 문구) <br />

**강조** <br />
`**`로 감싸준다
```
큰 바다 넓은 **하늘을 우리는 가졌노라** (2018학년도 대학수학능력시험 필적확인 문구)
```
큰 바다 넓은 **하늘을 우리는 가졌노라** (**2018학년도** 대학수학능력시험 필적확인 문구) <br />

**강조2** <br />
`` ` ``로 감싸준다
```
큰 `바다` 넓은 `하늘`을 우리는 가졌노라 (2018학년도 대학수학능력시험 `필적`확인 문구)
```
큰 `바다` 넓은 `하늘`을 우리는 가졌노라 (2018학년도 대학수학능력시험 `필적`확인 문구) <br />


### 주석
> 주석은 >기호를 이용하여 작성할 수 있다.

### 링크 삽입
```
[Github](http://github.com/leechoong)를 참고하세요
```
[Github](http://github.com/leechoong)를 참고하세요

### 이미지 삽입
```
![이미지이름](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/200px-Markdown-mark.svg.png)
```
![이미지이름](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/200px-Markdown-mark.svg.png)

### 표
```
| 헤더1    |  헤더 2  |   헤더 3  |
|:---|:---:|---:|
| 셀 1    | 셀 2    |   셀 3    |
| 셀 4    | 셀 5    |   셀 6    |
| 셀 7    | 셀 8    |   셀 9    |
| 셀 10   | 셀 11   |   셀 12   |
```

| 헤더1    |  헤더 2  |   헤더 3  |
|:---|:---:|---:|
| 셀 1    | 셀 2    |   셀 3    |
| 셀 4    | 셀 5    |   셀 6    |
| 셀 7    | 셀 8    |   셀 9    |
| 셀 10   | 셀 11   |   셀 12   |


### 코드
 `` ` `` 사이에 코드 삽입

```c
int main(void) {
 printf("Hello, world!\n");
 return 0;
} // C lang
```

```php
<?
  echo("Hello, world!"); // php
?>
```

```html
<!-- html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Insert Code</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

### 기타
개인적으로 기록해 두고 싶은 팁 <br />
키 입력 (`` ` ``랑 좀 다르다)
```
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd>
`Ctrl`+`Alt`+`Del`
```
<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> <br />
`Ctrl`+`Alt`+`Del`


화살표
```
&uarr; &darr; &rarr; &larr;
```
&uarr; &darr; &rarr; &larr;


## 마무리
`Markdown` 문법을 간단히 알아보았는데, 앞으로 사용하면서 추가할 내용이 있으면 추가할 예정.
