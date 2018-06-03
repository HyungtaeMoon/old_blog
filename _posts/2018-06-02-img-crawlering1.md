---
layout: post
title:  "웹사이트 이미지 크롤링하는 방법"
date:   2018-06-02 17:56:04 +0700
categories: [python]
---
`웹사이트`  `이미지 크롤링 방법`  `html가져오기`

**아래의 내용은 순수하게 개인의 학습을 목적으로 공부하는 자료입니다.**
<br>
**자료와 관련하여 저작권 침해 등의 문제 발생 시에는 바로 삭제를 하도록 하겠습니다.**
<br>
<br>
##선행학습
웹사이트를 parssing하기 위해서는 내 로컬에 저장할 경로를 지정
<br>
조건식에 의해서 필요한 정보만을 취한다.
<br>
<br>
**웹사이트 parser 를 위한 모듈**
```
import os #내장모듈


import requests #서드파티 모듈
from bs4 import BeautifulSoup
```
<br>
**os 모듈**
<br>
웹페이지의 데이터를 내 로컬에 저장하기 위한 모듈.
**requests 모듈**
<br>
url 주소를 html 형식으로 변경해주는 모듈
<br>
**BeautifulSoup 모듈**
<br>파씽한 데이터를 보기 쉽게, 원하는 속성만을 뽑아낼 수 있도록 도와주는 모듈
<br>
**서드파티 모듈??**
<br>
파이썬을 더 쉽고 빠르게 이용할 수 있도록 개발자가 독자적으로 개발한 모듈
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
`네이버 웹툰 파씽하기 - 이번 포스팅 메인 자료`
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
<br>

>> 웹페이지를 저장할 경로를 지정
>> 파일경로와 크롤링 대상 페이지를 미리 변수선언
>> if 문에서 코딩이 길어지지 않도록 해준다.

<br>
```
file_path = '내 로컬에 저장경로 설정'

url_episode_list = '가져오고자 하는 웹페이지 주소'


params = {
  예시) 'titleId':651673
}

* 가져오고자 하는 웹페이지 주소에서 타이틀만 따로 빼서 딕셔너리로 바꿔놓자. 이렇게 해두면 나중에 타이틀 아이디만 바꾸어서 간편하게 크롤링을 할 수 있다.
```
<br>
<br>
 웹페이지를 저장할 때 `어떤 파일`을 `어떠한 확장자로`만들고 `덮어쓰기 or 새로운 파일을 만들지`를 설정하는 방법을 알아본다.
<br>
```
if os.path.exists(저장할 경로):
  html(변수명) = open(저장경로, '데이터 가공방식').모드

  데이터 가공방식: rt, wt
  모드: read(), write(쓰고자 하는 파일명, 변수명)
```
<br>
<br>
```
else:
  response = requests.get(가져올 웹페이지 주소)

  html(변수명) = response.text
  open(저장경로, '데이터 가공방식').모드(변수명)


테스트 해보니 변수명(html)은 다른 텍스트로 해도 되지만 변수명은 이해하기 쉽도록 html 로 하자.
```
<br>
<br>
> 여기까지가 웹페이지 주소에 있는 html 형식의 파일을 내 로컬에 저장한 것이다.

<br>
<br>
현재까지 작업한 내용을 출력해본다.
```
print(html)
```
url 에서 추출한 html 의 데이터가 나온다. 여기서 원하는 속성값만 출력하기 위해 `BeautifulSoup` 모듈을 사용해야만 한다.
<br>
```
soup = BeautifulSoup(변수명, 'lxml')

soup를 변수명으로 지정한 것은 하나의 약속이라고 생각하자. soup 대신에 다른 변수명을 지정해도 되지만 soup라고 설정해야 나중에 알아보기 쉽다.

lxml 은 내장 파써보다 더 개선된 버전이다. 그냥 soup와 lxml은 짝꿍이라고 생각하자.
```
<br>
<br>
`BeautifulSoup의 사용방법`은 아래와 같다.
```
>> print(soup.title)
<title>유미의 세포들 :: 네이버 만화</title>
제목만 추출하기


>> print(soup.prettify())
html파일을 띄어쓰기 해주어 가독성을 개선. 내용이 무진장 길어지니 이 포스팅에서 결과값은 pass


>> print(soup.find_all('a'))
a 링크 부분만 출력하기


>> print(soup.head)
html의 head 부분만 출력하기
```
<br>
<br>
> 작업한 내용을 요약하면 아래와 같다..

1) url 주소에서 내 로컬로 저장(`os module`)
<br>
2) html 형식으로 저장(`requests module`)
<br>
3) 원하는 tag, list 부분만 추출(`BeautifulSoup`)
