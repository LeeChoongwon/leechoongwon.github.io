---
layout: post
title: 블로그 웹마스터도구 등록
categories:
  - Blog
date: 2017-12-12 00:00:02 +09:00
comments: true
visible: 1
---

네이버 블로그가 아닌 이상, 네이버 웹마스터도구 등록을 해주지 않으면 네이버검색에 나의 포스트가 뜨지 않는다. 네이버와 구글 웹마스터도구에 등록해 봅니다.


## 네이버 웹마스터도구 등록
[네이버 웹마스터도구](http://webmastertool.naver.com/) 에 접속하여 `네이버 계정`으로 로그인 합니다.

연동 사이트 목록에서 `사이트 추가+` <br/>
도메인을 입력하면 사이트 소유확인 페이지로 넘어갑니다.

### 사이트 소유 확인
Jekyll 을 이용한 블로그 운영이므로 HTML파일을 추가할 수 있습니다.
HTML파일을 다운로드 후, 다운받은 파일을 본인의 `루트 디렉토리`에 위치시킵니다.

<figure>
<img src="/assets/posts/20171212/201.png" width="500">
<figcaption align="middle">
</figcaption>
</figure>

`github`에 커밋 후, 웹마스터도구 사이트에서 보안문자 입력 후 제출하면, 소유권 확인이 완료.

## 구글 웹마스터도구 등록
[구글 웹마스터도구(Search Console)](https://www.google.com/webmasters/tools/home?hl=ko)에 접속합니다.

`사이트추가` 클릭 후 자신의 도메인 입력 <br/>
네이버에서 처럼 HTML파일을 다운로드 후, 다운받은 파일을 본인의 `루트 디렉토리`에 위치시킵니다. <br/>

완료 후 확인을 클릭하면 등록이 완료됩니다.

## 사이트맵 제출
### 사이트맵의 필요성

`사이트맵(sitemap)`은 웹페이지를 나열하는 파일로 사이트 콘텐츠의 구성을 Google 및 다른 검색 엔진에 알리는 데 사용한다. <br/>
또한 `메타데이터`를 제공하는데, 메타데이터는 웹페이지에 관한 정보로 페이지가 마지막으로 업데이트된 날짜, 페이지 변경 빈도, 사이트 페이지의 중요성 등을 포함. <br/>
사이트맵은 매우 큰사이트나, 페이지간의 연결 및 링크가 자연스럽지 않은 웹페이지에서 `봇(bot)`이 `크롤링(Crawling)`을 더욱 지능적으로 할 수 있도록 정보를 제공한다. <br/>

직접 사이트맵을 작성하기는 귀찮기 때문에, 대신 사이트맵을 자동으로 생성해주는 웹사이트들이 있다. <br/>

1. [Online XML Sitemap Generator](http://www.web-site-map.com/xml_sitemap.php) <br/>
2. [XML-Sitemaps.com](https://www.xml-sitemaps.com)
3. [XML Sitemap Generator](https://xmlsitemapgenerator.org)

구글에 검색해보면 무료 웹사이트들이 많이 있다. 하나를 골라 본인의 도메인을 입력하면 `sitemap.xml`파일을 다운받을 수 있다. <br/>

다운받은 `sitemap.xml`은 대략 아래와같이 생겼을 것이다.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
  <url>
    <loc>http://leechoong.github.io/</loc>
    <changefreq>daily</changefreq>
    <priority>1.00</priority>
  </url>
  <url>
    <loc>https://leechoong.github.io/categories/</loc>
    <lastmod>2017-12-06T07:53:40+00:00</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.85</priority>
  </url>
  <url>
    <loc>https://leechoong.github.io/about/</loc>
    <lastmod>2017-12-06T07:53:40+00:00</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.85</priority>
  </url>
  <url>
    <loc>https://leechoong.github.io/archives/</loc>
    <lastmod>2017-12-06T07:53:40+00:00</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.85</priority>
  </url>
  <url>
    <loc>https://leechoong.github.io/tags/</loc>
    <lastmod>2017-12-06T07:53:40+00:00</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.85</priority>
  </url>
  <url>
    <loc>https://leechoong.github.io/articles/2017-12/Raspberry-Pi-VNC</loc>
    <lastmod>2017-12-06T07:53:40+00:00</lastmod>
    <changefreq>daily</changefreq>
    <priority>0.85</priority>
  </url>
```

<!-- ad -->

### 네이버
다시 네이버 웹마스터도구에 접속하여, 등록한 본인의 URL 클릭. <br/>
좌측 탭에서 `요청` &rarr; `사이트맵 제출`<br/>

<figure>
<img src="/assets/posts/20171212/202.png" width="300">
<figcaption align="middle">
</figcaption>
</figure>

**/sitemap.xml** 입력.

### 구글
Google Search console 에서 등록한 본인의 URL 클릭 후, <br/>
좌측 탭에서 `크롤링`  &rarr;  `sitemaps`<br/>

<figure>
<img src="/assets/posts/20171212/203.png" width="300">
<figcaption align="middle">
</figcaption>
</figure>


`SITEMAP 추가/테스트` 버튼 클릭 후, **/sitemap.xml** 입력.

## robots.txt 수집
기본적으로 루트디렉토리에 위치하는 `robots.txt`파일을 자동으로 인식하지만, 직접 입력하였을 경우, 따로 제출합니다.
```
User-agent: *
Allow: /

Sitemap: http://leechoong.github.io/sitemap.xml
```

### 네이버
<figure>
<img src="/assets/posts/20171212/204.png" width="300">
<figcaption align="middle">
</figcaption>
</figure>

루트디렉토리에 파일 위치 후, `수집` 요청.

### 구글
Google Search console 에서 등록한 본인의 URL 클릭 후, <br/>
좌측 탭에서 `크롤링`  &rarr;  `sitemaps`<br/>

루트디렉토리에 파일 위치 후, `제출` 요청.

## 마무리
웹마스터도구에 등록하는 것은 자신의 블로그를 네이버나 구글같은 메이져 검색엔진에 노출시키기 위해 가장 먼저 해야할 일입니다.
