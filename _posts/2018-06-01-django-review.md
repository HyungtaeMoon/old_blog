---
layout: post
title:  "[설정] 장고 환경설정 방법"
date:   2018-06-01 17:56:04 +0700
categories: [python]
---
`Django` `환경설정` `수업따라가기`
<br>
<br>
#### # 장고(Django)환경 설정 방법
<br>
<br>
`django 디렉토리 생성`
```
> mkdir 디렉토리명(생성)

> cd 디렉토리명(진입)
```
<br>
`내 깃허브에 new repository 생성`
<br>
```
> git 홈페이지
https://github.com/

> 새로운 .git 저장소 만들기
git init

```
<br>
`.gitignore 생성`
```
> gitignore 홈페이지
https://www.gitignore.io/

> 추가 항목
python django, macos, linux, git, pycharm+all

> create버튼 클릭

> 생성한 텍스트 파일을 .gitignore에 붙여넣기
vi .gitignore
```
<br>
`requirements 기록하기`
```
pip freeze > requirements.txt

다른 개발자가 동일한 환경에서 설정해서 구현하도록
requirements.txt는 현재 버전의 정보를 저장
```
<br>
`블로그 설치하기`
```
python manage.py startapp
```
<br>
`migration 추가하기`
```
python manage.py makemigrations

python manage.py migrate
```
<br>
`가상환경 설정`
```
> 가상환경 설치하기
pyenv virtualenv 3.6.5 [원하는 가상환경 이름 설정]

> 가상환경으로 진입하기
pyenv local [작성한 가상환경 이름]
```
<br>
<br>
`PyCharm Interpreter 설정`
```
파이참 안에서 환경 설정(Ctrl + Alr + S) 실행

Project:djangogirls-tutorial

Interpreter

Project Interpreter

나의 현재 디렉토리 위치로 설정(없으면 추가)
(설정하는 이유는 charm . 을 작업 폴더 안에서 실행하기 위함)
```
<br>
`Django 설치하기`
```
pip install django
```
<br>
`Django가 설치되었는지 확인`
```
pip --list
```
<br>
<br>
--------------------------------
<br>
<br>
`장고로 사이트 만들기`
**django-admin startproject mysite**
mysite 라는 이름의 사이트를 생성한다
(mysite 폴더가 새로 생성됨을 파이참 안에서 확인)
<br>
**폴더의 구조**
절대적인 경로는 아니고 이러한 방식으로 폴더가 구성된다 정도로 익혀두자.
```
djangogirls-tutorial/ <- 이 프로젝트의 컨테이너 폴더(Root폴더)
  app/  <- Django프로젝트 관련 코드 컨테이너 폴더
    config/  <- Django프로젝트의 설정 관련 패키지
      settings.py
  .gitignore  <- 프로젝트를 git하기 위해 필요한 파일들
  .git/
  requirements.txt
  ...
```
<br>
<br>
`경로 이해하기`
<br>
**PyCharm은 현재 프로젝트 구조에서 가장 상위폴더를 파이썬 Source의 root로 인식한다**
```
project/ <- python 실행
  project_module1.py
  project_module2.py
  pac1/
    __init__.py
    pac1_module.py
    pac2/
      __init__.py
      pac2_module.py
      pac3/
        __init__.py
```
<br>
`Q. project_module1.py 를 가져오고 싶다면?`
import project_module1
<br>
`Q. pac1 패키지 안의 pac1_module.py를 가져오고 싶다면?`
from import project_module1
<br>
`Q. pac2 패키지 안의 pac2_module를 가져오고 싶다면?`
from pac1.pac2 import pac2.pac1_module
<br>
`python을 pac1에서 시작했을 때 project_module를 가져오고 싶다면?`
불가능하다. 루트폴더 하위에서만 작업이 가능하다.
<br>
패키지와 경로는 조금 다르다.
알고 있던 경로 접근 방식은 / 였는데 패키지는 . 으로 접근을 한다. 왜냐하면 패키지가 가진 모듈은 `패키지의 속성처럼 접근`을 하기 때문이다.
<br>
<br>
폴더를 생성할 때 `Directory`와 `Python Package`의 차이점은 `Python Package`는 생성할 때 '__init__.py'파일을 같이 생성해준다.
<br>
<br>
**자주 사용하게 될 명령어 모음**
`루트폴더 지정 방법`
지정하고자 하는 `루트폴더 선택` 후 마우스 오른쪽 클릭, `Mark directory as`, `sources Root`로 지정
<br>
<br>
`프로젝트에 사용한 장고 버전 기록`
```
pip freeze (버전 확인)

Django==1.11.13
pyz==2018.04
```
<br>
<br>
```
관례적으로 requirements.txt에 버전 정보를 심는다.

pip freeze > requirements.txt
```
<br>
<br>
`loopback` 주소
127.0.0.1:8000
127.0.0.1:4000 등등
위의 주소로 ip를 보내면 밖으로 안 나가고 다시 나에게 돌아오는 주소. 굳이 다른 서버로 보내고 하는 일련의 작업들이 필요 없을 때 이 'loopback'을 사용한다.
```
장고의 경우, app 폴더 안에서

python manage.py runserver
```
<br>
<br>
블로그 생성하기
`python manage.py startapp blog`
<br>
<br>
자주 사용하는 Completion/Basic(자동완성)
`환경설정` - `Keymap` - `Ctrl + Space`
<br>
<br>
데이터 베이스 구조로 반영해주는 migrate
**변경사항 만들기**
`app 폴더` > `python manage.py makemigrations`
<br>
**변경사항 적용**
`python manage.py migrate`
<br>
<br>
<br>
**장고 관리자 페이지 만들기**
```python
파일명: admin.py

from django.contrib import admin

from .models import Post

admin.site.register(post)
```
<br>
`관리자 페이지 접근 방법(admin 생성)`
python manage.py createsuperuser
