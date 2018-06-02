---
layout: post
title:  "웹사이트 이미지 크롤링하는 방법"
date:   2018-06-02 17:56:04 +0700
categories: [python]
---
`웹사이트``이미지 크롤링 방법`

**아래의 내용은 순수하게 개인의 학습을 목적으로 공부하는 자료입니다.**
<br>
**자료와 관련하여 저작권 침해 문제 발생 시에는 바로 삭제를 하도록 하겠습니다.**
<br>
<br>
이미지를 크롤링하기 위해서는 필요한 모듈들이 있다.
우선 필요한 모듈들을 `import` 시켜야 한다.
<br>
```python
import os #기본모듈

import requests #서드파티 모듈
from bs4 import BeautifulSoup
```
**서드파티 모듈??**
파이썬에는 기본적인 라이브러리 모듈 외에 많은 개발자가 파이썬을 더 쉽고 빠르게 이용할 수 있도록 독자적인 모듈을 개발해왔는데 그것이 서드파티 모듈이다.
<br>
이 서드파티 모듈을 설치하는 방법은 `pip install <서드파티모듈명>`을 터미널 창에서 실행시키면 된다.
<br>
<br>
`os모듈 사용 방법을 이용하여 html 다운로드 하기`
```
import os

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
```
imort os 모듈을 실행해야 아래의 라이브러리 데이터가 적용이 된다. os 모듈은 원하는 파일에 대한 데이터를 `내 로컬에 가져오고 조건식에 의해서 디렉토리 생성`까지 해주는 모듈이다.
<br>
file_path = '디렉토리 생성 또는 경로 지정'

url_episode_list = 리스트 정리
