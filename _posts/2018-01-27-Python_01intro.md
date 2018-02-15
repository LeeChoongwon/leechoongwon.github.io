---
layout: post
title:  파이썬 01 intro
categories: Python
date: 2018-01-27 00:00:01 +09:00
comments: true
image-sm:
---

파이썬(Python) 이란?

## 목차
{:.no_toc}

0. toc
{:toc}

## 파이썬
### intro
파이썬(영어: Python)은 1991년 프로그래머인 귀도 반 로섬(Guido van Rossum)이 발표한 고급 프로그래밍 언어로, `플랫폼 독립적이며 인터프리터식`, `객체지향적`, `동적 타이핑(dynamically typed) 대화형 언어`이다. 파이썬이라는 이름은 귀도가 좋아하는 코미디 〈Monty Python's Flying Circus〉에서 따온 것이다.
파이썬은 비영리의 파이썬 소프트웨어 재단이 관리하는 개방형, 공동체 기반 개발 모델을 가지고 있다. C언어로 구현된 C파이썬 구현이 사실상의 표준이다. <br />
( 출처: [wikipedia](https://ko.wikipedia.org/wiki/파이썬) )

### 파이썬 특징
#### 파이썬은 인간다운 언어이다
파이썬은 사람이 생각하는 방식을 그대로 표현할 수 있는 언어이다.

#### 무료이다
오픈 소스이기 때문에 무료이다. 다양한 개발 환경에 설치 가능하며, C와 더불어 연동하여 사용 가능하기 때문에 강력하다.

#### 문법이 쉽다
프로그래밍 경험이 있는 사람들은 일주일정도면, 파이썬으로 원하는 기능을 구현할 수 있다고 한다.

#### 간결하다
가독성이 좋고, `({ })`같은 괄호의 향연이 없다.

#### 개발 속도가 빠르다
다양한 라이브러리 지원과, 간결한 문법으로 개발속도가 빠르다.


## 파이썬의 철학
### Zen of Python
```py
>>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

`easter egg` 로 인터프레터에 `import this` 를 입력하면, 파이썬의 철학을 출력할 수 있습니다. <br />

### 번역

아름다움이 추함보다 좋다. <br />
명시가 암시보다 좋다. <br />
단순함이 복잡함보다 좋다. <br >
복잡함이 꼬인 것보다 좋다. <br />
수평이 계층보다 좋다. <br />
여유로운 것이 밀집한 것보다 좋다. <br />
가독성은 중요하다. <br />
특별한 경우라는 것은 규칙을 어겨야 할 정도로 특별한 것이 아니다. <br />
허나 실용성은 순수성에 우선한다. <br />
오류 앞에서 절대 침묵하지 말지어다. <br />
명시적으로 오류를 감추려는 의도가 아니라면.  <br />
모호함을 앞에 두고, 이를 유추하겠다는 유혹을 버려라.  <br />
어떤 일에든 명확한 - 바람직하며 유일한 - 방법이 존재한다.  <br />
비록 그대가 우둔하여 그 방법이 처음에는 명확해 보이지 않을지라도.  <br />
지금 하는게 아예 안하는 것보다 낫다. 아예 안하는 것이 지금 *당장*보다 나을 때도 있지만.  <br />
구현 결과를 설명하기 어렵다면, 그 아이디어는 나쁘다.  <br />
구현 결과를 설명하기 쉽다면, 그 아이디어는 좋은 아이디어일 수 있다.  <br />
네임스페이스는 대박 좋은 아이디어다 -- 마구 남용해라! <br />
