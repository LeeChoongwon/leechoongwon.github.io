---
layout: post
title: PHP 빗썸 API 활용#2
categories:
  - Fun
  - PHP
date: 2018-01-05 00:00:02 +09:00
comments: true
visible: 1
---

private api도 사용해보자

## 목차
{:.no_toc}

0. toc
{:toc}

## 빗썸 api 가져오기
빗썸 홈페이지 api메뉴에 접속합니다. <br />

<figure>
<img src="/assets/posts/20180105/201.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>

내가 사용하기 원하는 정보와, 그 정보를 가져올 수 있는 api주소를 여기서 얻을 수 있습니다. <br />
> 그냥 시세를 보고싶으면 /public/ticker, 내 자산을 보고싶으면 /info/balance 등등

php 클라이언트에서
```php
<?php

// API CALL
$balance = $api->xcoinApiCall("/info/balance", $rgParams);
$xrp_public = $api->xcoinApiCall("/public/ticker/XRP", $rgParams);
$btc_public = $api->xcoinApiCall("/public/ticker/BTC", $rgParams);
$xrp_trans = $api->xcoinApiCall("/info/user_transactions", $rgParams_xrp);

 ?>
```
이런식으로 원하는 api를 불러옵니다.

불러온 api를 그냥 출력 해보겠습니다.
```php
<?php
print_r($xrp_public);
 ?>
```
<figure>
<img src="/assets/posts/20180105/202.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>
이처럼 데이터가 정신없이 출력됩니다.

<!-- ad -->

## 데이터 가공
```php
<?php

$xrp_buy_price = $xrp_public->data->buy_price;
echo $xrp_buy_price;

 ?>
```
위처럼 출력하면 어떻게 될까요? <br />
저 위사진의 정보대로라면 4357이 출력됩니다. <br />


먼저 `print_r` 로 출력이 어떻게 되는지 보고, 원하는 데이터가 무슨 Object 뒤에 있는지 확인하고 그 데이터만 지정하여 출력하면 편리합니다.

## 응용
<figure>
<img src="/assets/posts/20180105/203.png" width="600">
<figcaption align="middle">
</figcaption>
</figure>

## 코드
단순한 코드지만, 전체 코드는 올려놓지 않았습니다. <br />
다만, 개인적으로 궁금한거 문의주시면 성심성의껏 답변해 드리겠습니다. <br />
