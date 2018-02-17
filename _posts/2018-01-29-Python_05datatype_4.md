---
layout: post
title:  파이썬 05 자료형(딕셔너리)
categories:
  - Python
date: 2018-01-29 00:00:02 +09:00
comments: true
visible: 1
---

앞선 포스팅에서, 리스트와 튜플에 대해 알아보았습니다. 이번에는 조금 다르게 생긴 키와 값의 대응으로 이루어진 `딕셔너리`입니다.


## 딕셔너리
딕셔너리는 키:값 (Key:Value) 로 이루어져 있습니다. <br />
기본 형태는 {Key1:Value1, Key2:Value2, Key3:Value3, Key4:Value4, ...} 입니다.

### 딕셔너리 생성
딕셔너리명 = {Key1:Value1, Key2:Value2, Key3:Value3, Key4:Value4..} 이렇게 생성 가능합니다.

```py
>>> co = {'Microsoft':'Gates', 'Facebook':'Zuckerberg'}
```
> 주의해야할 점이, key값이 중복 될 경우, 뒤에 있는 key값만 유효하게 된다.

### 딕셔너리 추가
기존 딕셔너리에 새로운 `키:값` 을 추가하는 방법입니다. <br />
`딕셔너리명[추가할Key] = 추가할Value` 의 명령으로 추가됩니다.

```py
>>> co = {'Microsoft':'Gates', 'Facebook':'Zuckerberg'}
>>> co['Google'] = 'Page'
>>> co
{'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page'}
```

Value값이 단일 문자열이나 숫자 외에, 리스트의 추가도 가능합니다.
```py
>>> co['Apple'] = ['Jobs', 'Wozniak']
>>> co
{'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
```

### 딕셔너리 삭제
기존 딕셔너리에서 특정 키:값을 삭제하는 방법입니다. Key를 삭제하게 되면 대응되는 Value는 자동으로 같이 삭제됩니다.
`del 딕셔너리명[키]`

```py
>>> del co['Apple']
>>> co
{'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page'}
```

### 인덱싱, 슬라이싱?
딕셔너리는 리스트, 튜플과 다르게 인덱스가 할당되어 있지 않습니다. 순서가 중요하지 않다는 뜻입니다. 리스트와 튜플에서의 인덱싱은 불가능하며, 오직 Key값으로 Value를 리턴할 수 있습니다.

```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co['Microsoft']
'Gates'
>>> co['Apple']
['Jobs', 'Wozniak']
>>> co['Apple'][1]
'Wozniak'
```

이렇게 숫자가 아닌 Key 값을 통해 Value값을 얻습니다.

> Key 'Apple'의 Value인 ['Jobs', 'Wozniak'] 은 리스트(list)이기 때문에 인덱싱이 가능하다


## 딕셔너리 함수
### keys()
딕셔너리에서 Key값만 리턴할 수 있는 함수입니다. <br />
`딕셔너리명.keys()`
```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co.keys()
dict_keys(['Microsoft', 'Facebook', 'Google', 'Apple'])
```
> python 3.0 이상부터 dict_keys 객체가 리턴되는데, 이는 리스트로 변환할때의 메모리 낭비를 방지하기 위해서 이렇게 리턴된다고 한다. 리스트로 사용하고 싶으면 list()로 간단히 변경할 수 있다.

```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co.keys()
dict_keys(['Microsoft', 'Facebook', 'Google', 'Apple'])
>>> list(co.keys())
['Microsoft', 'Facebook', 'Google', 'Apple']
```

### values()
딕셔너리의 Value 값들만 리턴합니다. <br />
`딕셔너리명.values()`

```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co.values()
dict_values(['Gates', 'Zuckerberg', 'Page', ['Jobs', 'Wozniak']])
>>> list(co.values())
['Gates', 'Zuckerberg', 'Page', ['Jobs', 'Wozniak']]
```

### items()
딕셔너리의 Key와 Value의 쌍을 리턴합니다.
`딕셔너리명.items()`
```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co.items()
dict_items([('Microsoft', 'Gates'), ('Facebook', 'Zuckerberg'), ('Google', 'Page'), ('Apple', ['Jobs', 'Wozniak'])])
>>> list(co.items())
[('Microsoft', 'Gates'), ('Facebook', 'Zuckerberg'), ('Google', 'Page'), ('Apple', ['Jobs', 'Wozniak'])]
```

### get()
앞서 딕셔너리에서 key를 통해 value를 리턴할 때 사용했던 `딕셔너리명[Key]`와 동일한 기능을 하는 함수입니다. <br />
`딕셔너리명.get(Key)`
```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> co.get('Google')
'Page'
>>> co.get('Facebook')
'Zuckerberg'
```

### 존재 여부 확인 in
딕셔너리 안에 특정 Key값이 존재하는지 확인합니다.
`Key in 딕셔너리명`
```py
>>> co = {'Microsoft': 'Gates', 'Facebook': 'Zuckerberg', 'Google': 'Page', 'Apple': ['Jobs', 'Wozniak']}
>>> 'Apple' in co
True
>>> 'Amazon' in co
False
```

## 마무리
딕셔너리는 키:값의 대응으로 이루어진, 기존과 조금 다른 형태의 자료형입니다. 시퀀스가 없기 때문에, 딕셔너리에서 데이터를 찾을 때, 원하는 Key만 지정해서 탐색할 수 있어 메모리의 낭비를 줄일 수 있습니다.
