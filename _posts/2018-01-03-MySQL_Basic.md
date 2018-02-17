---
layout: post
title: MySQL 기본 명령어
categories:
  - MySQL
  - PHP
date: 2018-01-03 00:00:01 +09:00
comments: true
visible: 1
---

MySQL의 기본 명령어들을 정리한다. 생성, 삽입, 조회, 수정, 삭제


## MySQL 접속
필자는 `MAMP Stack(Mac Apache, MySQL, Php)`을 설치하여 사용한다. 이 환경 기준으로 정리할 예정이다. <br />

설처한 폴더/mysql/bin로 접속
```
cd mampstack-5.6.32-1/mysql/bin/
./mysql -uusername -ppassword -hhost
```
예를들어 username: root, password: 123456, host: localhost 일 경우,
```
./mysql -uroot -p123456 -hlocalhost
```

## Database 조회
```
mysql> SHOW DATABASES;
```
데이터베이스 목록 출력

## 생성 (CREATE)
### Database 생성

예시로 `testdb` 라는 데이터베이스 생성 <br />
`CREATE DATABASE` 명령어 사용
```
mysql> CREATE DATABASE testdb;
```

testdb 사용설정 `USE` 명령어 사용
```
mysql> USE testdb;
Database changed
```

### Table 생성

예시로 `testtable` 이라 하는 테이블 생성 <br />
이 table 에 `id`, `name`, `phone` 이라는 컬럼 생성
```
mysql> CREATE TABLE testtable (
    -> id int NOT NULL auto_increment primary key,
    -> name VARCHAR(15) NOT NULL,
    -> phone VARCHAR(15) NOT NULL
    -> );
```

INT: 정수형 <br />
DOUBLE: 실수형 <br />
VARCHAR 문자형 <br />

NOT NULL: 빈 값일 수 없음 <br />
AUTO_INCREMENT: 숫자가 자동으로 증가 <br />
PRIMARY KEY: <br />


생성된 테이블 상세정보 확인
`DESCRIBE` 나 `EXPLAIN` 명령어 사용
```
mysql> Describe testtable;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| id    | int(11)     | NO   | PRI | NULL    | auto_increment |
| name  | varchar(15) | NO   |     | NULL    |                |
| phone | varchar(15) | NO   |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
```
## 삽입 (INSERT)
### Table 데이터 삽입

id 는 자동으로 숫자가 하나씩 올라가니, 생략하고 name, phone 데이터를 입력한다. <br />
`INSERT INTO 테이블명 (컬럼명1, 컬럼명3, ...) VALUES (값1, 값3, ...);`
```
mysql> INSERT INTO testtable (name, phone) VALUES ('Andy', '010-1234-5678');
mysql> INSERT INTO testtable (name, phone) VALUES ('Brian', '010-4321-8765');
mysql> INSERT INTO testtable (name, phone) VALUES ('Emily', '011-4321-5678');
```

<!-- ad -->

## 조회 (SELECT)
결과 확인하려면 `SELECT` 명령어 사용 <br />
`SELECT 컬럼명1, 컬럼명2, .. FROM 테이블명;`
```
mysql> SELECT id, name, phone FROM testtable;
+----+-------+---------------+
| id | name  | phone         |
+----+-------+---------------+
|  1 | Andy  | 010-1234-5678 |
|  2 | Brian | 010-4321-8765 |
|  3 | Emily | 011-4321-5678 |
+----+-------+---------------+

mysql> SELECT name FROM testtable;
+-------+
| name  |
+-------+
| Andy  |
| Brian |
| Emily |
+-------+
```
전체 컬럼 선택시, id, name 등 전부 입력하기 보다, `*`로 대체 한다.

```
mysql> SELECT * FROM testtable;
+----+-------+---------------+
| id | name  | phone         |
+----+-------+---------------+
|  1 | Andy  | 010-1234-5678 |
|  2 | Brian | 010-4321-8765 |
|  3 | Emily | 011-4321-5678 |
+----+-------+---------------+
```

### 조건 사용하여 조회
`WHERE` 명령어를 사용하여 조건설정 가능
```
mysql> SELECT * FROM testtable WHERE name='Emily';
+----+-------+---------------+
| id | name  | phone         |
+----+-------+---------------+
|  3 | Emily | 011-4321-5678 |
+----+-------+---------------+

mysql> SELECT name, phone FROM testtable WHERE phone LIKE '%5678';
+-------+---------------+
| name  | phone         |
+-------+---------------+
| Andy  | 010-1234-5678 |
| Emily | 011-4321-5678 |
+-------+---------------+
```

위 커맨드는 `LIKE` 명령어로 phone 컬럼 value가 5678로 끝나는 데이터만 골라 출력한 결과. <br />
같은 방식으로 010으로 시작하는 데이터 출력한 결과
```
mysql> SELECT * FROM testtable WHERE phone LIKE '010%';
+----+-------+---------------+
| id | name  | phone         |
+----+-------+---------------+
|  1 | Andy  | 010-1234-5678 |
|  2 | Brian | 010-4321-8765 |
+----+-------+---------------+
```

### 오름차순, 내림차순 정렬 조회
`ASC` : 오름차순 <br />
`DESC` : 내림차순 <br />

`ORDER BY` 명령어를 사용하여 정렬 조건 입력
```
mysql> SELECT * FROM testtable ORDER BY id DESC;
+----+-------+---------------+
| id | name  | phone         |
+----+-------+---------------+
|  3 | Emily | 011-4321-5678 |
|  2 | Brian | 010-4321-8765 |
|  1 | Andy  | 010-1234-5678 |
+----+-------+---------------+

mysql> INSERT INTO testtable (name, phone) VALUES ('Charlie', '017-1234-8389');

mysql> SELECT * FROM testtable ORDER BY name DESC;
+----+---------+---------------+
| id | name    | phone         |
+----+---------+---------------+
|  3 | Emily   | 011-4321-5678 |
|  4 | Charlie | 017-1234-8389 |
|  2 | Brian   | 010-4321-8765 |
|  1 | Andy    | 010-1234-5678 |
+----+---------+---------------+

mysql> SELECT * FROM testtable ORDER BY name ASC;
+----+---------+---------------+
| id | name    | phone         |
+----+---------+---------------+
|  1 | Andy    | 010-1234-5678 |
|  2 | Brian   | 010-4321-8765 |
|  4 | Charlie | 017-1234-8389 |
|  3 | Emily   | 011-4321-5678 |
+----+---------+---------------+
```

## (번외) 데이터가 있는 테이블에 컬럼 추가 (ALTER)
데이터를 세분화하고 싶어서 컬럼을 추가하고 싶을 때, `ALTER TABLE` 명령어 사용 <br />
`ALTER TABLE 테이블명 ADD 컬럼명 컬럼속성 AFTER 컬럼명`

```
mysql> ALTER TABLE testtable add role VARCHAR(15) NOT NULL after phone;

mysql> describe testtable;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| id    | int(11)     | NO   | PRI | NULL    | auto_increment |
| name  | varchar(15) | NO   |     | NULL    |                |
| phone | varchar(15) | NO   |     | NULL    |                |
| role  | varchar(15) | NO   |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
```
## 수정 (UPDATE)
`UPDATE` 명령어로 기존 데이터에 추가 가능하다 <br />
`UPDATE 테이블명 SET 컬럼명=값 WHERE 조건`
```
mysql> UPDATE testtable SET role='student' WHERE id=2;

mysql> SELECT * FROM testtable;
+----+---------+---------------+---------+
| id | name    | phone         | role    |
+----+---------+---------------+---------+
|  1 | Andy    | 010-1234-5678 |         |
|  2 | Brian   | 010-4321-8765 | student |
|  3 | Emily   | 011-4321-5678 |         |
|  4 | Charlie | 017-1234-8389 |         |
+----+---------+---------------+---------+
```

위처럼 WHERE 뒤의 조건을 만족하는 row의 데이터를 수정할 수 있다.
```
mysql> UPDATE testtable SET role='student' WHERE phone LIKE '010%';

mysql> UPDATE testtable SET role='teacher' WHERE phone NOT LIKE '010%';

mysql> SELECT * FROM testtable;
+----+---------+---------------+---------+
| id | name    | phone         | role    |
+----+---------+---------------+---------+
|  1 | Andy    | 010-1234-5678 | student |
|  2 | Brian   | 010-4321-8765 | student |
|  3 | Emily   | 011-4321-5678 | teacher |
|  4 | Charlie | 017-1234-8389 | teacher |
+----+---------+---------------+---------+
```

위 예시는 전화번호가 010으로 시작하는 사람은 student, 아닌 사람은 teacher로 role 을 정해준 예시

## 삭제 (DELETE)
`DELETE`명령어로 데이터 삭제 <br />
`DELETE FROM 테이블명 WHERE 조건`
```
mysql> DELETE FROM testtable WHERE id=3;

mysql> SELECT * FROM testtable;
+----+---------+---------------+---------+
| id | name    | phone         | role    |
+----+---------+---------------+---------+
|  1 | Andy    | 010-1234-5678 | student |
|  2 | Brian   | 010-4321-8765 | student |
|  4 | Charlie | 017-1234-8389 | teacher |
+----+---------+---------------+---------+
```

### 전체삭제
`DROP TABLE`, `DROP DATABASE` 명령어로 전체 삭제
```
mysql> DROP TABLE testtable;
mysql> DROP DATABASE testdb;
```


## 마무리
MySQL 기본 사용법에 대해 정리했습니다. `phpmyadmin`같은 gui 클라이언트를 이용하면 훨씬 직관적이고 편하게 볼 수 있지만, php와의 연동 등을 하려면 기본 명령어는 숙지하고 있어야 해서 정리해 보았습니다.
