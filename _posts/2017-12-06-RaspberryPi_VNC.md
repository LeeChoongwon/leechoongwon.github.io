---
layout: post
title: Raspberry Pi 원격접속
categories: tutorial
tags: raspberrypi
date: 2017-12-06 00:00:01 +09:00
comments: true
visible: 1
---

지금까지 여분의 모니터와 HDMI 케이블로 연결해서 설정을 진행했습니다. 여분의 모니터가 없으면, 매번 모니터 바꿔끼워주는게 상당히 귀찮은 일입니다. <br />
지금부터 라즈베리파이의 화면을 윈도우, 맥 등 사용하시는 PC의 화면에 출력하고 작업할 수 있도록 하겠습니다.

## 목차
{:.no_toc}

0. toc
{:toc}


## Intro
### 준비물
- Raspbian이 설치된 라즈베리파이

## / 라즈베리파이에서 설정
### VNC 활성화
`시작메뉴` &rarr; `기본설정` &rarr; `Raspberry Pi Configuration` &rarr; `Interfaces  탭`

- VNC 를 `Enable` 로 변경.
- VNC서버가 제대로 실행되고 있는지 확인. 상단바에 `VNC 로고`가 있다면 정상 작동중. 만약 없다면 **재부팅** 후 확인.

### 네트워크 확인
```
$ ifconfig
```

명령어를 입력하면 네트워크 관련 정보들이 출력되는데
무선 네트워크를 사용하면 `wlan0`밑에, 유선랜을 사용하면 `eth0` 밑에 `inet addr:` 에서 현재 라즈베리파이의 ip주소를 확인. <br/>
*IP 주소는 ###.###.###.### 총 12자리 입니다.*

### VNC Server 실행
<figure>
<img src="/assets/posts/20171206/101.png" width="400" align="middle">
<figcaption align="middle">
&uarr; VNC Server 실행화면
</figcaption>
</figure>
<br/>


## / PC에서 설정
PC에서 원격접속을 할 프로그램을 다운로드 받습니다.
[다운로드 링크](https://www.realvnc.com/download/vnc/)

<figure>
<img src="/assets/posts/20171206/102.png" width="400" align="middle">
<figcaption align="middle">
&uarr; VNC Connect 홈페이지
</figcaption>
</figure>
<br/>

본인의 PC 운영체제에 맞는 프로그램을 다운로드 받습니다. <br/>
저는 `macOS`로 진행하겠습니다.

### VNC 실행
설치한 프로그램 실행 후,
`Enter a VNC Server address or search` 에 라즈베리파이의 IP주소를 입력합니다.

- Username: pi
- Password: 초기설정 시, 지정한 비밀번호

까지 입력하면 라즈베리파이의 화면이 PC의 화면에 출력되는것을 볼 수 있습니다.

## / 마무리
이제 모니터 없이 라즈베리파이 작업을 할 수 있습니다. 키보드 마우스도 모두 사용할 수 있어서 간편합니다.
