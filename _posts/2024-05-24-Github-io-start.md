---
layout: post
title:  "GitHub io 시작하기"
author: jhieee
date:   2024-05-26 00:06:31
tags: [githubio]
description: ''
categories: [githubio]
---

# Github 블로그 시작하기

기억력이 좋지 않아 기록하는 습관을 들여보자 해서 네이버메모, 에버노트, Notion 순으로 기록을 저장하였다. 기록하면서 직장 동료들에게 링크를 전달해주면서 공유하는 것에 기쁨을 느껴서 노션을 블로그로 호스팅해서 사용해보았다. 노션 블로그로서의 단점이 있어 블로그를 시작하려고 한다.
 블로그는 플랫폼이 많은데 브랜치, 네이버 블로그 등 을 알아보다 직업이 개발자라 Github 사용이 많아 github io 로 결정했다.

## Github 템플릿

github io 를 사용하기 위해 아래 홈페이지에서 템플릿을 찾아야한다. 물론 한땀 한땀 나에게 맞게 개발할 수 있지만.. 굳이 그럴 필요가 있나 ?

[jekyllthemes](https://jekyllrb.com/docs/themes/) 에서 템플릿을 찾아보자,

> Jekyll 는 설치형 블로그로 정적 사이트 생성기의 하나고 Ruby 언어를 기반으로 만들어짐 ([나무위키 참고](https://namu.wiki/w/jekyll))

(chirpy)](https://chirpy.cotes.page/posts/getting-started/) 로 결정
https://github.com/cotes2020/jekyll-theme-chirpy 에서 Source 를 땡겨오자.

![_blog reposition 생성_](/assets/img/github-io-start/init_1.png)
_blog reposition 생성_

Fork 후 Repository name 명을 {ID}.github.io 로 repository 를 생성한다.

![branch 설정](/assets/img/github-io-start/init_2.png)
_branch 설정_

Setting -> Pages -> Branch 를 main 으로 지정 후 save 를 누르면 {id}.github.io 로 접속이 가능하다.

## 로컬 환경 세팅

과연 이게 필요할까 싶지만.. 설정해보았음

### gcc 설치
```bash
brew install gcc
```

### Ruby 설치

```bash
brew install rbenv ruby-build

# 설치 완료 후 버전 확인
rbenv versions 

# 설치 가능한 버전 확인 3.3.1 으로 설치함
benv install -l 

rbenv install 3.3.1

rbenv global 3.3.1

rbenv versions # 확인

```

zshrc 에 설정

```bash
vi ~/.zshrc

# 맨 하단에 복붙 후 저장
export PATH=/opt/homebrew/bin:$PATH
[[ -d ~/.rbenv  ]] && \
  export PATH=${HOME}/.rbenv/bin:${PATH} && \
  eval "$(rbenv init -)

source ~/.zshrc
```

### 빌드를 위한 gem 설치
```bash
gem install bundler

rbenv rehash

bundle install

bundle exec jekyll serve
```

default 인 4000번 포트로 열려 127.0.0.1:4000 으로 접속 

## 포스팅
_posts 폴에더 YYYY-MM-DD-제목.md 로 생성하면 완료
더 자세한건 깃헙을 참고하자.


### 빌드 에러

### 1. "URL" is not an HTTPS link

![error_1 설정](/assets/img/github-io-start/error_1.png)

> http://jekyllthemes.org/ is not an HTTPS link

post 의 하이퍼링크에 url 이 http 가 있으면 빌드 시 실패 된다.

### 2. 'a' tag is missing a reference

![error_2 설정](/assets/img/github-io-start/error_2.png)

> athors 설정

athors 작성자 설정을 하지 않으면 빌드가 실패한다.

_data/authors.yml 파일을 생성하여 authors 를 추가하고 posts 의 md 파일에 author 를 추가하자 

```yaml
## _data/authors.yml
jhieee:
  name: jinhyunglee
```

```md
# md 파일
---
layout: post
title:  "GitHub io 시작하기 상세"
author: jhieee
date:   2024-05-26 00:06:31
tags: [githubio]
description: ''
categories: [githubio]
---
```
