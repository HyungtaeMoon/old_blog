---
layout: post
title:  "웹사이트 이미지 크롤링하는 방법"
date:   2018-06-02 17:56:04 +0700
categories: [python]
---
`웹사이트``이미지 크롤링 방법`

**아래의 내용은 순수하게 개인의 학습을 목적으로 공부하는 자료입니다.**
<br>
**자료와 관련하여 저작권 침해 등의 문제 발생 시에는 바로 삭제를 하도록 하겠습니다.**
<br>
<br>
##선행학습
`웹사이트를 parser하기 위해서는 내 로컬에 저장할 경로를 지정하고, 조건식에 의해서 필요한 정보만을 취한다.`
**웹사이트 parser 를 위한 모듈**
```
import os #내장모듈

import requests #서드파티 모듈
from bs4 import BeautifulSoup
```
**os 모듈** 웹페이지의 데이터를 내 로컬에 저장하기 위한 모듈.
**requests 모듈** url 주소를 html 형식으로 변경해주는 모듈
**BeautifulSoup 모듈** 파씽한 데이터를 보기 쉽게, 원하는 속성만을 뽑아낼 수 있도록 도와주는 모듈
<br>
**서드파티 모듈은 파이썬을 더 쉽고 빠르게 이용할 수 있도록 개발자가 독자적으로 개발한 모듈**
<br>
<br>
`서드 파티 모듈 설치방법`
```
터미널 창

[설치하기]
>> pip install <서드파티 모듈명>

[설치한 모듈 확인하기]
>> pip list

[BeautifulSoup 설치]
>>pip install beautifulsoup4

[requests 설치]
>> pip install requests
```
<br>
<br>
`네이버 웹툰 파씽하기`
```python
import os

import requests
from bs4 import BeautifulSoup

file_path = 'data2/test_list.html'

url_episode list = 'https://comic/webtoon/list.nhn'

params = {
  'titleId':703845,
}

if os.path.exists(file_path):
  html = open(file_path, 'rt').read()
else:
  response = requests.get(url_episode_list, params)

  html = response.text
  open(file_path, 'wt').write(html)

soup = BeautifulSoup(html, 'lxml')
```
<br>
##코딩 분석하기
<br>
<br>
**선행학습**
웹페이지를 저장할 경로를 지정한다. 파일경로와 웹페이지 주소를 미리 설정하여 코딩을 간결하게 진행한다.
```
file_path = '내 로컬에 저장경로 설정'

url_episode_list = '가져오고자 하는 웹페이지 주소'


params = {
  예시) 'titleId':651673
}
* 가져오고자 하는 웹페이지 주소에서 타이틀만 따로 빼서 코딩해두자. 타이틀 아이디만 바꾸면 다른 웹툰도 바로 크롤링이 가능하니 따로 빼두는 것이 나중에 확인할 때도 편하다.
```
<br>
<br>
**선행학습**
웹페이지를 저장할 때 `어떤 파일`을 `어떠한 확장자로`만들고 `덮어쓰기를 할지 새로 파일을 만들지`를 구성하는 방법을 알아본다.
<br>
```
if os.path.exists(저장할 경로):
  변수명= open(저장경로, '데이터 가공방식').모드

  데이터 가공방식: rt, wt
  모드: read(), write(쓰고자 하는 파일명, 변수명)
```
<br>
<br>
```
else:
  response = requests.get(가져올 웹페이지 주소)

  변수명 = response.text
  open(저장경로, '데이터 가공방식').모드(변수명)
```
여기까지가 웹페이지 주소에 있는 html 형식의 파일을 내 로컬에 저장한 것이다.
<br>
현재까지 작업한 내용을 출력해본다.
```
print(html)
```
무지막지한 html주소가 나온다. 여기서 원하는 속성값만 출력하려면 BeautifulSoup 모듈을 사용하는 것이 좋다.
<br>
```
soup = BeautifulSoup(변수명, 'lxml')

soup를 변수명으로 지정한 것은 하나의 약속이라고 생각하자. soup 대신에 다른 변수명을 지정해도 되지만 soup라고 해놔야 알아보기 쉽다.
lxml 은 기본적으로 지원하는 파써보다 더 개선된 버전이다. 그냥 soup와 lxml은 짝꿍이라고 생각하자.
```
print(soup)자체로는 모듈의 장점이 드러나지 않는다.
<br>
BeautifulSoup의 사용방법은 아래와 같다.
```
>> print(soup.title)
<title>유미의 세포들 :: 네이버 만화</title>
제목만 출력하기


>> print(soup.prettify())
html파일을 사람이 알아보기 쉽도록 해준다. 내용이 무진장 길어지니 출력값은 pass

>> print(soup.find_all('a'))
a 링크 부분만 출력하기


>> print(soup.head)
html의 head 부분만 출력하기
```
이와같이 BeautifulSoup를 이용하면 원하고자 하는 html의 데이터 값만 따로 가져올 수 있다.
