---
title:  "첫 번째 블로그"
excerpt: "jekyll 로컬 서버를 띄워보자 "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
 
date: 2022-01-10
last_modified_at: 2022-01-10
---
# 준비물
git bash, jekyll, bundler

# 로컬 서버가 안 뜬다.
bundler exec jekyll serve 실행 시 에러가 발생한다 
-> .gemspec 파일 열어보니 git 명령어 부분발견
-> git 을 실행할 수 있도록 환경변수 등록이 안 된 것.
나는 git bash windows 버전을 설치했다.

# 그래도 안 된다.
bundler 버전이 compatible 하지 않다는 에러.
Bundler could not find compatible versions for gem “jekyll”
-> bundle update 
명령어를 수행하여 bundler를 버전을 갱신해주자

# 여전히 안 된다
webrick이 없다는 에러.
`require': cannot load such file -- webrick (LoadError)

-> bundle add webrick 
명령어를 수행하자.



