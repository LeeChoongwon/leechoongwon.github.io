---
layout: post
title:  PHP로 xml과 json 파싱
categories:
  - PHP
date: 2018-01-17 00:00:01 +09:00
comments: true
visible: 1
---

API를 활용하다 보면, 결과값을 xml 형식으로 제공하는 곳도 있고, json형식으롼 제공하는 곳도 있습니다. 두 형식 모두 원하는 데이터를 파싱할 수 있어야 편리합니다.


## XML 에서 원하는 데이터 추출
예시로 xml 파일을 하나 생성합니다
`example.xml`
```xml
<data>
    <employee>
        <firstName>John</firstName>
        <lastName>Doe</lastName>
    </employee>
    <employee>
        <firstName>Anna</firstName>
        <lastName>Smith</lastName>
    </employee>
    <employee>
        <firstName>Peter</firstName>
        <lastName>Jones</lastName>
    </employee>
</data>
```

위처럼 주어진 데이터에서 각 이름만 출력하고자 합니다. <br />

`xml_parse.php`
```php
<?php

$xml = file_get_contents("example.xml");
$result_xml = simplexml_load_string($xml);
print_r($result_xml);

 ?>
```

`simplexml_load_string()` xml 데이터를 배열,오브젝트형식으로 변환해주는 함수입니다.
```php
SimpleXMLElement Object
(
    [employee] => Array
        (
            [0] => SimpleXMLElement Object
                (
                    [firstName] => John
                    [lastName] => Doe
                )

            [1] => SimpleXMLElement Object
                (
                    [firstName] => Anna
                    [lastName] => Smith
                )

            [2] => SimpleXMLElement Object
                (
                    [firstName] => Peter
                    [lastName] => Jones
                )

        )
)
```

이렇게 배열로 출력되어 원하는 데이터에 접근하기 쉬워졌습니다. 이제 각 데이터를 읽어오겠습니다.

```php
<?php

echo $result_xml->employee[0]->firstName; // John
echo $result_xml->employee[0]->lastName; // Doe

echo $result_xml->employee[1]->firstName; // Anna
echo $result_xml->employee[1]->lastName; // Smith

echo $result_xml->employee[2]->firstName; // Peter
echo $result_xml->employee[2]->lastName; // Jones

?>
```
<!-- ad -->
## JSON에서 원하는 데이터 추출
마찬가지로, json  형식으로 같은 데이터를 가지고 파일을 하나 만들겠습니다.
`example.json`
```json
{
   "data": {
      "employee": [
         {
            "firstName": "John",
            "lastName": "Doe"
         },
         {
            "firstName": "Anna",
            "lastName": "Smith"
         },
         {
            "firstName": "Peter",
            "lastName": "Jones"
         }
      ]
   }
}
```

### 첫번째 방법
`json_parse1.php`
```php
<?php

$json = file_get_contents("example.json");
$result_json = json_decode($json,true);
print_r($result_json);

?>
```

위 코드는 `json_decode($json,true)` 를 사용하였습니다. <br />
TRUE 는 배열로 반환하는 인수입니다. 그렇기 때문에 출력하면,
```php
Array
(
    [data] => Array
        (
            [employee] => Array
                (
                    [0] => Array
                        (
                            [firstName] => John
                            [lastName] => Doe
                        )

                    [1] => Array
                        (
                            [firstName] => Anna
                            [lastName] => Smith
                        )

                    [2] => Array
                        (
                            [firstName] => Peter
                            [lastName] => Jones
                        )
                )
        )
)
```
위와같이 배열로 출력됩니다. <br />
배열이기 때문에 원하는 데이터를 출력하기 간편합니다.
```php
<?php

echo $result_json[data][employee][0][firstName]; // John
echo $result_json[data][employee][0][lastName]; // Doe

echo $result_json[data][employee][1][firstName]; // Anna
echo $result_json[data][employee][1][lastName]; // Smith

echo $result_json[data][employee][2][firstName]; // Peter
echo $result_json[data][employee][2][lastName]; // Jones

?>
```

### 두번째 방법
`json_parse2.php`
```php
<?php

$json = file_get_contents("example.json");
$result_json2 = json_decode($json);
print_r($result_json2);

?>
```

이번에는 `TRUE`인자를 뺴고 출력하였습니다.
```php
stdClass Object
(
    [data] => stdClass Object
        (
            [employee] => Array
                (
                    [0] => stdClass Object
                        (
                            [firstName] => John
                            [lastName] => Doe
                        )

                    [1] => stdClass Object
                        (
                            [firstName] => Anna
                            [lastName] => Smith
                        )

                    [2] => stdClass Object
                        (
                            [firstName] => Peter
                            [lastName] => Jones
                        )
                )
        )
)
```

위와 같이, 배열과 객체가 혼합된 형태로 출력됩니다.
```php
<?php

print_r($result_json2->data->employee[0]->firstName); // John
echo " ";
print_r($result_json2->data->employee[0]->lastName); // Doe
echo "<br />";
print_r($result_json2->data->employee[1]->firstName); // Anna
echo " ";
print_r($result_json2->data->employee[1]->lastName); // Smith
echo "<br />";
print_r($result_json2->data->employee[2]->firstName); // Peter
echo " ";
print_r($result_json2->data->employee[2]->lastName); // Jones

?>
```

객체나 배열이나 본인이 원하는 형태로  decode 해서 필요한 데이터만 가져올 수 있습니다.

## 마무리
api를 사용한다던지, 방대한 데이터가 있을 때,  원하는 데이터만 추출해야하는 경우가 있습니다. 그럴때 알아두면 편리한 php 함수였습니다.
