---
layout: post
title: Raspberry Pi 한글설정
date: 2017-12-05 00:00:03 +09:00
comments: true
visible: 1
---

한국사람은 한글을 사용해야죠. 한글로 언어를 바꿔보겠습니다.


## Intro
### 준비물
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

Raspbian repo 업데이트와 업그레이드 <br/>
위 내용과 관련된 사항은 [이곳](https://leechoong.github.io/articles/2017-12/Raspberry-Pi-Update)에서 다루고 있습니다.

## 한글폰트 패키지 다운로드
```
$ sudo apt-get install ibus ibus-hangul fonts-unfonts-core
```
`ibus`, `ibus-hangul`, `fonts-unfonts-core` 을 설치합니다.

## 한글 설정
`시작메뉴` &rarr; `Preferences` &rarr; `Raspberry Pi Configuration` <br/>
&rarr; `Localisation 탭` <br/>

<figure>
<img src="/assets/posts/20171205/301.png" width="500" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

### Locale
&rarr; `Set Locale...` <br/>
<figure>
<img src="/assets/posts/20171205/302.png" width="400" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

- Language: ko (Korean)
- Country: KR (Republic of Korea)
- Character Set: UTF-8

으로 변경.

### Timezone
&rarr; `Set Timezone...` <br/>

<figure>
<img src="/assets/posts/20171205/303.png" width="300" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

- Area: Asia
- Location: Seoul

### Keyboard
&rarr; `Set Keyboard...` <br/>

<figure>
<img src="/assets/posts/20171205/304.png" width="400" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

`Korea, Republic of` &rarr; `Korean(101/104 Key configuration)`

## 한/영 전환 단축키 설정
데스크탑 우측 상단 언어 `우클릭` <br/>
`기본설정` &rarr; `입력방식` <br/>

<figure>
<img src="/assets/posts/20171205/305.png" width="500" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

&rarr; `기본설정`

<figure>
<img src="/assets/posts/20171205/306.png" width="300" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

`Shift + space 제거` &rarr; `추가` <br/>

<figure>
<img src="/assets/posts/20171205/307.png" width="400" align="middle">
<figcaption align="middle">
</figcaption>
</figure>
<br/>

원하는 `단축키` 입력 후 확인

## 마무리
한글 설정을 마쳤습니다. 현재 Stretch버젼은 아직 확인해 보지 못해서 안될 수도 있습니다. 확인되는되로 수정하겠습니다. <br/>
다음엔 **VNC** 를 통해 원격으로 접속하여 거추장스러운 추가 모니터를 없애겠습니다.
