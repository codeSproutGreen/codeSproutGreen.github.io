---
title:  "[Jekyll] 블로그 포스팅하는 방법"
excerpt: "md 파일에 마크다운 문법으로 작성하여 Github 원격 저장소에 업로드 해보자. 에디터는 Visual Studio code 사용! 로컬 서버에서 확인도 해보자. "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
 
date: 2022-01-10
last_modified_at: 2022-01-10
---



#테스트 소제목
<br>
안녕?

#첫 블로그

안녕


# 로컬 서버 띄우기 안되는 이유
bundler exec jekyll serve 실행 시 에러가 발생한다 -> .gemspec 파일 열어보니 git 명령어 부분발견
-> git 을 실행할 수 있도록 환경변수 등록이 안 된 것.
나는 git bash windows 버전을 설치했다

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


