---
layout: post
title: Raspberry Pi 시작하기
categories:
  - RaspberryPi
date: 2017-12-05 00:00:01 +09:00
comments: true
visible: 1
---
초소형 컴퓨터 라즈베리파이에 대해 알아보고 사용해보자.


## Intro
**라즈베리 파이(Raspberry Pi)** 는 영국 잉글랜드의 라즈베리 파이 재단이 학교와 개발도상국에서 기초 컴퓨터 과학의 교육을 증진시키기 위해 개발한 신용카드 크기의 **싱글 보드 컴퓨터** 이다. <br/>
라즈베리 파이 재단은 `데비안`과 `아치 리눅스` ARM 배포판의 다운로드를 제공하고, 주요 프로그래밍 언어로 `파이썬`의 사용을 촉진하며, BBC 베이직을 지원한다. `C`, `C++`, `자바`, `펄`, `루비`, `스퀵 스몰토크` 등의 언어가 사용 가능하다. [^1] <br/>

<figure>
<img src="/assets/posts/20171205/101.png" width="400" align="middle">
<figcaption align="middle">
&uarr; 라즈베리파이 2 Model B
</figcaption>
</figure>
<br/>

### Raspberry Pi 프로젝트 예시
Raspberry Pi는 매우 다양한 프로젝트에 사용되고 있다. <br/>
[[예시 1](http://www.itworld.co.kr/slideshow/92451)] <br/>
[[예시 2](http://www.itpro.co.uk/mobile/21862/raspberry-pi-top-31-projects-to-try-yourself-1)]

## Raspbian 설치
운영체제 설치를 하겠습니다.
라즈베리파이에서 사용가능한 운영체제는 진행할 프로젝트에 따라 여러 종류가 있지만, 저는 많은 분들이 사용하고 계시는 `Raspbian OS Jessie`를 설치해 보도록 하겠습니다.

### 준비물
- 라즈베리파이 (필자는  3으로 진행)
- micro SD카드 (8GB 이상 권장)
- micro SD카드 리더기
- HDMI 케이블과, 연결가능한 모니터
- 전원케이블 및 어답터 (5V, 2.5A)

### 이미지(img) 다운로드
[Raspbian 다운로드](https://www.raspberrypi.org/downloads/Raspbian/) <br/>

<figure>
<img src="/assets/posts/20171205/102.png" width="700" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

(2017년 7월 23일에 작성한 글이라 Raspbian JESSIE WITH DESKTOP (Release date 20170705) 가 가장 최신 버젼입니다. 지금은 `Raspbian Stretch with Desktop`으로 업데이트 되었습니다.)

### Win32Diskimager 다운로드
[다운로드](https://sourceforge.net/projects/win32diskimager/) <br/>

<figure>
<img src="/assets/posts/20171205/103.png" width="700" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

다운받고 설치.

<!-- ad -->

### OS imaging
준비한 micro SD 카드를 리더기를 이용하여 컴퓨터에 연결 후, 설치된 `Win32Diskimager`을 실행. <br />

<figure>
<img src="/assets/posts/20171205/104.png" width="500" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

Image File 에서 다운로드 받은 `####-##-##-Raspbian-jessie.img` 파일을 선택하고, Device 에서는 연결한 micro SD 카드의 드라이브명을 선택합니다. <br />
`Write` 를 클릭하여 SD카드에 Raspbian OS를 이미징.

## Raspbian 부팅

`Write Complete` 되면 SD카드 연결을 안전하게 해제한 후, Raspberry Pi에 삽입. <br/>
데스크탑이 보이면 성공

## 주의사항
- **SD카드를 먼저 삽입 후, 전원을 인가할 것** <br/>
  전원을 주면 자동으로 부팅되기 때문에 컴퓨터를 키고 OS가 저장되어있는 디스크를 연결하는것과 같음
- **라즈베리파이3의 경우 5V전압에 2.5A이상 전류 추천**

## 마무리
Raspbian OS는 흔히 사용하는 운영체제이다. 다양한 운영체제를 경험하고 싶으면 NOOBS(New Out Of Box Software)를 추천한다. [NOOBS 다운로드](https://www.raspberrypi.org/downloads/noobs/)
<br/>
<br/>


[^1]: 출처: [wikipedia](https://ko.wikipedia.org/wiki/라즈베리_파이)
