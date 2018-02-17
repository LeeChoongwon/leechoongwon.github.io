---
layout: post
title:  파이썬 03 자료형(문자열)
categories:
  - Python
date: 2018-01-27 00:00:03 +09:00
comments: true
visible: 1
---

파이썬의 자료형 중 문자열에 대해 정리합니다.


## 문자열
문자열은 string 이라 하며, 말 그대로 문자를 표현하는 자료형입니다. <br >
예를 들어, 'hello', 'hello world', '12345' 등이 모두 문자열 입니다. 의아해 하실 수 도 있는게, '12345'는 얼핏 보면 정수형 같지만, `''`로 둘러쌓여서 표현된 문자열 입니다.

### 생성 방법
`''` 나 `""` 같은 `인용부호` 를 이용하여 문자열을 생성합니다.

```py
>>> 'hello'
'hello'
>>> "hello"
'hello'
```

조금 더 긴 문장을 문자열로 나타내려면, `''' '''` 혹은 `""" """` 처럼 3개의 따옴표를 이용하면 됩니다.

```py
>>> '''She stared
...  through the window
...  at the stars.'''
'She stared\n through the window\n at the stars.'
```

`'''`을 작성하게 되면, 인터프레터에서 엔터키를 누르더라도, 명령이 실행되지 않고, 다음줄에 작성할 수 있도록 넘어갑니다.

### 다른 자료형을 문자열로 변환 str()
int 나, float 등의 다른 자료형을 문자열로 변환시킬 수 있는데, 이때 `str()`을 사용합니다.

```py
>>> type(3.14)
<class 'float'>
>>> str(3.14)
'3.14'
>>> type(str(3.14))
<class 'str'>
>>> str(3.14)
'3.14'
```

type()으로 3.14의 자료형을 알아보면 실수형(float)입니다. <br />
str(3.14)를 실행하게 되면, 3.14가 ''의 인용부호 안에 들어가 문자열로 변환됩니다. <br />
역시 자료형을 확인해보면, 문자열(str) 이 출력됩니다.


## 줄바꿈, 간격 띄우기(tab) (이스케이프 코드)
줄바꿈을 나타내고 싶을때, 간격 벌림을 나타내고 싶을 때 사용하는 코드 입니다. <br />
줄바꿈 \n <br />
```py
>>> a = 'hello, \n My name is \n Python.'
>>> print(a)
hello,
 My name is
 Python.
>>>
```
파이썬 인터프레터가, a변수의 문자열을 읽다가, `\n`을 만나면 줄을 바꾸게 됩니다. <br />

수평 탭 \t <br />
```py
>>> b = 'I watched the storm\tso beautiful yet terrific'
>>> print(b)
I watched the storm	    so beautiful yet terrific
```

마찬가지로, `\t`를 만나면 수평 탭을 실행하여 간격을 띄우게 됩니다.

## 문자열 결합, 복제
두개 이상의 문자열을 결합할 수 도 있으며, 한 문자열을 여러면 출력할 수도 있습니다.

### 결합
`+` 기호를 이용하여 결합을 할 수 있습니다.
```py
>>> a = 'Almost before'
>>> b = 'we knew it,'
>>> c = 'we had left the ground.'
>>> a + b + c
'Almost beforewe knew it,we had left the ground.'
>>> print(a,b,c)
Almost before we knew it, we had left the ground.
```

### 복제
`*` 곱셈 기호를 이용하여 문자열을 복제합니다.
```py
>>> a = 'dog' *4
>>> b = 'cat' *2
>>> c = 'happy' *3
>>> a + b + c
'dogdogdogdogcatcathappyhappyhappy'
>>> print(a, b, c)
dogdogdogdog catcat happyhappyhappy
```

여기서, a + b + c 를 출력하면, 문자열의 형대로 출력이 되며, <br />
print() 명령어로 출력하게 되면, 특별한 자료형이 없는 상태로 출력되는데, 이때, 각 변수 사이에 `space`가 들어가게 되어 간격이 벌어집니다.

<!-- ad -->

## 인덱싱
문자열을 작성하게되면, 각 문자마다 고유의 번호가 매겨지는데 이 번호를 `오프셋`이라 하고, 오프셋을 이용하여 문자열에서 문자를 추출하는 것을 `인덱싱`이라 합니다.

### 오프셋
문자열의 오프셋은 0 부터 시작합니다.

```py
>>> alphabet = 'abcdefghijklmnopqrstuvwxyz'
```
alphabet이라는 변수에 a부터z 까지의 문자를 작성하였습니다. <br />
이때, 첫번째 문자는 a, 마지막 26번째 문자는 z입니다. <br />
그런데 오프셋은 0이 시작입니다. 그렇기 때문에 첫번째 문자를 나타내고 싶으면, `alphabet[0]`을 작성하여야 합니다.

```py
>>> alphabet[0]
'a'
>>> alphabet[17]
'r'
>>> alphabet[25]
'z'
```

0부터 시작하므로, 26번째는 25가 됩니다. 그렇기 때문에 'z' 를 출력하고 싶다면 `alphabet[25]`를 사용해야합니다.


오프셋은 `음수`값을 사용할 수도 있습니다. <br />
알파벳이 총 26자인것을 알기 떄문에 마지막 3개의 문자를 출력한다 하면,
```py
>>> alphabet[23]
'x'
>>> alphabet[24]
'y'
>>> alphabet[25]
'z'
```
이렇게 하면 되지만, 더 복잡한 문자열이고 문자의 총 개수를 모를 경우가 있을 수 있습니다. 그럴때는 음수 오프셋을 사용하면 되는데, 맨 뒤에서부터 -1, -2, -3 ... 할당되어 있습니다.

```py
>>> alphabet[-1]
'z'
>>> alphabet[-2]
'y'
>>> alphabet[-3]
'x'
```

> 첫번째 문자가 0 이니 마지막 문자도 -0 이지 않을까 생각할 수 있는데, -0도 0이기 때문에 -1부터 시작합니다.

## 슬라이싱
인덱싱으로 문자를 뽑아낼 수 있었는데, 단어를 출력하려면, 인덱싱을 여러번하여 결합해주어야 합니다. 번거로운 과정이기 때문에, 슬라이싱을 도입할 수 있습니다.
```py
>>> alphabet = 'abcdefghijklmnopqrstuvwxyz'
```

마찬가지로 alphabet변수에 a부터z까지 나열하여 작성하였습니다. <br />
이때 a부터d까지 출력하고 싶다고 한다면,
```py
>>> alphabet[0:4]
'abcd'
```

이렇게 작성해주면 되는데, 살펴보면 [x:y] 는 x =< < y를 나타냅니다. 오프셋 x부터 포함하여, y오프셋 직전까지를 나타내는 것입니다.

x나 y를 빈칸으로 두게 되면 맨 끝까지를 표현하는 것으로
```py
>>> alphabet[13:]
'nopqrstuvwxyz'
>>> alphabet[:7]
'abcdefg'
```

이렇게 y가 비어있으면 맨 마지막 오프셋까지, x가 비어있으면 맨 첫 오프셋까지를 나타냅니다.

## 마무리
여기까지 기본 자료형인 불리언, 정수형, 실수형, 문자열을 정리하였습니다. <br />
다음엔 고급 자료형인 `리스트(list)`, `튜플(tuple)`, `딕셔너리(dictionary)`, `셋(set)`을 알아보겠습니다.
