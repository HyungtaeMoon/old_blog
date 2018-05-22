---
layout: post
title:  "new posting"
date:   2018-05-22 14:32:04 +0700
categories: [python, security]
---

```python
>>> #hex_encode = 'summonagus'.encode('hex')
>>> hex_encode = '73756d6d6f6e61677573'
>>> chip  = ''.join([ str(int(a)*2) if a.isdigit() and int(a) == 3 else str(int(a)/2) if a.isdigit() and int(a) == 6 else a for a in hex_encode ])
>>>
>>> hex_encode
'73756d6d6f6e61677573'
>>> chip
'76753d3d3f3e31377576'
>>>
>>>
```

1) 모든 포스팅은 순수하게 개인의 공부 목적으로 작성됩니다.

2) 포스팅의 톤 앤 매너는 아주 편한 말투를 사용할 수 있습니다.

﻿3) 틀린 내용은 댓글을 통해 알려주시면 감사한 마음으로 수정을 하도록 하겠습니다.

4) 포스팅 내용과 관련하여 저작권 문제 발생 시 언제든지 삭제를 진행하겠습니다.
<p><p>

### 함수는 한마디로,
자주 사용하는 혹은 복잡한 수식을 미리 저장했다가 필요할 때 꺼내쓰는 것


함수는 크게 2가지로 나눌 수가 있습니다.
<br>
1) 파이썬에서 정의한 빌트인 함수
sum, enumerate, join, split 등
자세한 내용은 to be continue...


2) 사용자가 정의한 def 함수

(1) def 함수의 기본 형식
<br><br>
def 함수명(매개변수[parameters]):
  동작(또는 인수[arguments])
<br><br>
매개변수(함수로 전달되는 값의 변수)
인수(함수로 전달되는 값)
﻿<br>
[추가설명]
함수를 정의할 때는 매개변수(parameter)
함수를 호출할 때는 인자(arguments)라고 불린다﻿
﻿<br>
매개변수와 인자를 혼동해서 사용하기도 한다는데 아직 갈 길이 먼 것 같다.
<br>
즉, 매개변수는 변수(variable)
인자는 값(value)로 보는 것이 일반적이다.
매개변수는 함수의 정의의 한 부분으로 변하지 않지만
인자는 호출할 때마다 값이 바뀔 수 있다.
﻿* 위키백과 참조
<br><br>


1-1. 리턴값이 있는 함수 정의

수정했다!!!
        ```Python
        >>> def reuturn_true():
        >>>  return True
        >>> return_true()
        >>>
        >>>
        ```

<br><br>
[해설] return_true() 에 return True 값을 받는다.
Bool(true or false) 값을 가진다
받는 값은 참(true)로 출력은 true가 된다
<br><br>

1-2. 매개변수를 사용하는 함수 정의
<br>
```python
def print_arguments(sth):
        print(sth)
print_arguments('ABC')
#ABC
```
<br><br>

실제 예제
```python
def call_function():
    print('call funcition!')

call_function()
# call function!
```
<br><br>
[해설]
1) call_function 이란 함수를 생성
2) 괄호() 안에 print('call function!') 형식의 str 을 함수에 내장
3) call_function()를 실행하면 안에 print 문이 내장되어 있어 바로 출력.
<br><br>
이와 같은 구조를 가지게 되는데 이 안에서도 2가지로 분류가 됩니다.
﻿<br><br>
﻿
위치인자: 순서대로 인자를 전달
키워드인자: 매개변수의 이름을 지정하여 인자값은 매개변수를 따른다
<br><br>
위치인자와 키워드인자를 동시에 쓰면
1순위: 위치인자 // 2순위: 키워드인자

<br><br>
[위치 인자]

```python
def students(name, age, gender):
    return {'name' : name, 'age' : age, 'gender' : gender}
﻿
student('hyungtae.moon', 34, 'male')
# {name : hyungtae.moon, age : 34, gender : male)
﻿```

<br><br>

[키워드 인자]

```python
>>> def students(name, age, gender):
>>>   return {'name' : name, 'age' : age, 'gender' : gender}
>>> def student(age = 34, name = 'hyungtae.moon', gender='male')
>>>
>>> {'name' : 'hyungtae.moon', 'age' : 34, 'gender' : 'male'}
```

<br><br>

```python
>>> #hex_encode = 'summonagus'.encode('hex')
>>> hex_encode = '73756d6d6f6e61677573'
>>> chip = ''.join([ str(int(a)*2) if a.isdigit() and int(a) == 3 else str(int(a)/2) if a.isdigit() and int(a) == 6 else a for a in hex_encode ])
>>>
>>> hex_encode
'73756d6d6f6e61677573'
>>> chip
'76753d3d3f3e31377576'
>>>
>>>
```


```python
>>> #hex_encode = 'summonagus'.encode('hex')
>>> hex_encode = '73756d6d6f6e61677573'
>>> chip  = ''.join([ str(int(a)*2) if a.isdigit() and int(a) == 3 else str(int(a)/2) if a.isdigit() and int(a) == 6 else a for a in hex_encode ])
>>>
>>> hex_encode
'73756d6d6f6e61677573'
>>> chip
'76753d3d3f3e31377576'
>>>
>>>
```
