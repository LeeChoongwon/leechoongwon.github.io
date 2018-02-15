---
layout: post
title:  mysql 과 mysqli
categories:
  - MySQL
  - PHP
date: 2018-01-18 00:00:01 +09:00
comments: true
image-sm:
---

지난번에  MySQL과 php5의 연동에 대해 작성했었는데, 그때 사용한 mysql보다 mysqli을 사용하는 추세라 mysqli 예제를 간단히 다뤄보겠습니다.

## 목차
{:.no_toc}

0. toc
{:toc}

## mysqli
php7으로 업데이트 되면서, mysql 보다 mysqli 사용이 더 권장되고 있습니다. <br />
보안성이 좋고 속도가 더욱 빠르다고 합니다.

### php5에서 mysql -> mysqli

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$database = "dbname";
$conn = mysql_connect($servername, $username, $password);
mysql_select_db($conn, $database);
 ?>
```

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$database = "dbname";
$conn = mysqli_connect($servername, $username, $password);
mysqli_select_db($conn, $database);
 ?>
```

단순히 mysql를 mysqli 로 바꾼 예제입니다.
위처럼 바꿔서 사용하면 되는데. 이때, `php.ini` 파일에서
```ini
extension=php_mysqli.dll
```

주석이 풀려있는지 확인하고, 만약 주석처리되어 있으면 풀어줍니다.
