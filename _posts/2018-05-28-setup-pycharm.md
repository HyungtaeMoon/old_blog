---
layout: post
title:  "파이참 환경설정"
date:   2018-05-28 18:20:04 +0700
categories: [python]
---
1) 작업 공간 생성(git의 새로운 repo)
- git repo 명은 `crawler`
<br>
2) 로컬에 작업 공간 생성
```
/projects/
  crawler
    pyenv virtualenv 3.6.5 fc-crawler
    pyenv local fc-crawler
    -------------------------
    git init
    git remote add origin 'git의 http주소'
    git remote -v
    나의 경로 확인
```
** push는 항상 할 필요 없고, commit 만 수시로 해서 히스토리를 남겨놓자.
