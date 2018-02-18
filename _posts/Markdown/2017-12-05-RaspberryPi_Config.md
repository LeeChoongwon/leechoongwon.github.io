---
layout: post
title: Raspberry Pi 초기설정
categories:
  - RaspberryPi
date: 2017-12-05 00:00:02 +09:00
comments: true
visible: 1
---

전 포스팅에서 운영체제를 설치했습니다. 이번에는 초기설정을 하겠습니다.


## Intro
### 준비물
- `Raspbian`이 설치된 라스베리파이
- 키보드, 마우스

## GUI (Graphic User Interface) 설정
`시작메뉴` &rarr; `preferences` &rarr; `Raspberry Pi Configuration` <br/>
&rarr; `Interfaces 탭`
- **SSH** (네트워크를 통해 라즈베리파이에 접속 시 필요)
- **VNC** (네트워크를 통해 원격 접속 시 필요)

두 항목을 `enabled` 로 바꿔줍니다.

## raspi-config 사용
```
$ sudo raspi-config
```
위 명령어를 입력하면
<figure>
<img src="/assets/posts/20171205/201.png" align="middle">
<figcaption align="middle">
&uarr;raspi-config
</figcaption>
</figure>

1. Change User Password 유저 암호 변경
2. Hostname 호스트네임 변경
3. Boot Options 부팅 설정
4. Localisation Options 언어 및 지역 변경
5. Interfacing Options 인터페이스 설정
6. Overclock 오버쿨럭
7. Advanced Options 고급설정

다음과 같은 항목이 나옵니다.

### 비밀번호 변경
**보안을 위해 비밀번호는 꼭 바꿔줍시다** <br/>
초기 비밀번호는 *raspberrry*. <br/>
`1. Change User Password` 에 접속하여 비밀번호 변경

### Hostname 변경
초기 Hostname 은 Raspberry Pi <br/>
`2. Hostname` 에서 변경.

### SD카드 용량 확장
처음 Raspbian을 설치하면, OS가 차지하지 않는 공간이 빈 별도의 파티션으로 존재하게 된다. <br/>
`7. Advanced Options` &rarr; `A1 Expand Filesystem`

## 재부팅
명령어
```
$ sudo reboot
```
혹은

 `시작메뉴` &rarr; `Shutdown...` &rarr; `Reboot`


## 마무리
초기설정을 마쳤습니다. 다음은 한글설치를 진행하겠습니다.
