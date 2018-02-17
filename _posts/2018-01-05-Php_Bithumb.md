---
layout: post
title: PHP 빗썸 API 활용#1
categories:
  - Fun
  - PHP
date: 2018-01-05 00:00:01 +09:00
comments: true
visible: 1
---

가상화폐 거래소마다 API를 제공한다. 이미 많은 분들이 api를 활용하여 개인 시세 알림 서비스등을 개발할 수 있다.


## 빗썸 api 신청
빗썸 홈페이지에 접속해서 <br />
`마이페이지` -> `API 관리`

API CONNECT Key 와 API SECRET KEY를 신청합니다.
PRIVATE API를 사용하려면 API SECRET KEY까지의 발급이 필요합니다.

휴대폰 인증과 Email인증까지 마치고 API키를 발급 받습니다.

<figure>
<img src="/assets/posts/20180105/101.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>

API Secret은 잘 보관해둡니다.

<!-- ad -->

## 예시파일 다운로드
빗썸 홈페이지 하단에 api메뉴가 있습니다.
<figure>
<img src="/assets/posts/20180105/102.png" width="400">
<figcaption align="middle">
</figcaption>
</figure>

저는 이중에서 PHP를 활용하여 작성해 보도록 하겠습니다. <br />
PHP파일을 다운받습니다.

```
Bithumb_20150824_RESTFulAPI-php
├── api_test.php
└── xcoin_api_client.php
```

`xcoin_api_client.php`는 서버에서 작동하며, `api_test.php` 를 통해 접속하게 됩니다.

### 예시파일 수정
```php
<?php

require("xcoin_api_client.php");
$api = new XCoinAPI("api connect key", "api secret key");
$result = $api->xcoinApiCall("/public/ticker", $rgParams);
 ?>
```
API_CONNECT_KEY 와 API_SECRET_KEY 에 본인의 API키를 입력합니다. <br />
개인 정보 말고, 테스트로 퍼블릭 데이터를 가져오기 위해 xcoinApiCall 도 /public/ticker 로 수정합니다.

### 예시파일 적용
<figure>
<img src="/assets/posts/20180105/103.png" width="700">
<figcaption align="middle">
</figcaption>
</figure>

데이터가 잘 출력되는것을 볼 수 있습니다. 접속에 성공하면 status = 0000 입니다.

## 마무리
기본 예시파일을 활용하면 사용하기 편한 언어로 거래소가 제공하는 데이터를 보고 사용할 수 있다. 여러 거래소의 api를 활용해 나만의 차트를 만들수 있다.
