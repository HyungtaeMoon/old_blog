---
layout: post
title:  "쭉 읽어보는 django"
date:   2018-06-15 13:56:04 +0700
categories: [python]
---
`쭉 풀어쓰는 장고`
<br>
<br>
> 의식의 흐름대로 쓰는 장고

오늘도 새로운 프로젝트를 시작한다. 작업을 하기위해 디렉토리를 생성한다(`mkdir study`)그리고 이번 프로젝트는 다른 사람들과 같이 작업하기 위해서 github 에 업데이트를 해야 한다.(`git init`)깃에 무작정 업데이트하면 파일이 호환되지 않을 수가 있다. 그래서 `vi .gitignore`를 작업 프로젝트의 최상위에 생성해놓았다.
<br>
<br>
이번 프로젝트는 최신 버전으로 진행해서 다행이기는 하지만 그래도 혹시 모르니 이 프로젝트에 독립적으로 가상환경을 구성해놔야 한다. 안그러면 나중에 파이썬 자체를 업데이트하면 버전이 꼬일 수가 있다.(아마도?)그래서 파이썬 가상환경을 x버전으로 설치한다. `pyenv virtualenv 3.6.5 study`
