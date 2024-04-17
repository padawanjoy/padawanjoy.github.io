---
layout: post
title: "GitHub 블로그 만들기 2 - Jekyll 구조 적용하기"
date:   2024-04-17 23:42:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-17-part2-create-a-jekyll-project-structure/00.webp'
tags: [github, blog, github-pages, ruby, rbenv, jekyll]
tags_color: '#4a8e46'
featured: true
---
[지난 포스트](https://padawanjoy.com/blog/part1-building-your-first-github-pages-blog)에서 GitHub Pages 블로그 생성에 대해 알아봤습니다. 이번 포스트에서는 생성한 GitHub Pages를 꾸며서 정말 블로그처럼 보이도록 만들어 보겠습니다.

## 목차
- [Jekyll에 대해](#jekyll에-대해)
- [ruby 설치하기](#ruby-설치하기)
    - [rbenv 설치](#rbenv-설치)
    - [설치 가능한 버전별 ruby 목록 조회](#설치-가능한-버전별-ruby-목록-조회)
    - [원하는 버전의 ruby 설치](#원하는-버전의-ruby-설치)
    - [정상 설치 확인](#정상-설치-확인)
    - [설치한 ruby 버전 사용](#설치한-ruby-버전-사용)
- [Jekyll 구조 적용하기](#jekyll-구조-적용하기)
    - [Jekyll와 Bundler 설치](#jekyll와-bundler-설치)
    - [index.html 제거](#indexhtml-제거)
    - [Jekyll 구조 적용](#jekyll-구조-적용)
    - [젬(gem) 의존성 설치](#젬gem-의존성-설치)
- [블로그 확인하기](#블로그-확인하기)
    - [로컬에서 구동](#로컬에서-구동)
- [마무리](#마무리)

<br>
## Jekyll에 대해
GitHub Pages를 멋지고 이쁜 블로그 형태로 꾸미기 위해 Jekyll를 사용하려고 합니다. Jekyll은 블로그 중심의 정적 웹사이트를 만들기 위한 오픈 소스입니다. Ruby로 작성되었고, 마크다운(Markdown)이나 HTML 파일로 콘텐츠를 작성하고 이를 정적 파일로 변환하여 웹사이트를 구성합니다. GitHub Pages와 같은 서비스와 통합되어 사용되고, 템플릿, 레이아웃 등을 지원하여 웹사이트의 구조를 쉽게 관리할 수 있게 해줍니다. 이 Jekyll을 어떻게 우리 GitHub Pages에 적용하는지 알아보죠.

## ruby 설치하기
jekyll 테마를 사용하기 위해서는 먼저 ruby를 설치헤야 합니다. Mac OS에는 기본적으로 ruby가 설치되어있지만, 다음의 방법으로 ruby를 새로 설치해 보겠습니다. 

### rbenv 설치
rbenv는 여러 버전의 ruby를 관리하는 도구입니다. rbenv는 시스템에 여러 버전의 Ruby를 설치하고, 프로젝트 별로 다른 ruby 버전을 사용할 수 있도록 해줘서 편리합니다. 아래 예시 명령어와 같이 rbenv를 설치합니다. 
```sh
padawanjoy@MacStudio / % cd yourgithubblogpath
padawanjoy@MacStudio sampleusername.github.io % brew install rbenv
```

### 설치 가능한 버전별 ruby 목록 조회 
이제 ruby를 설치해 봅시다. 우리가 설치할 수 있는 버전이 어떤게 있는지 먼저 확인해 보겠습니다. 아래와 같은 명령어로 설치 가능한 버전별 ruby 목록을 조회할 수 있습니다.
```sh
rbenv install -l

3.0.6
3.1.4
3.2.2
jruby-9.4.3.0
mruby-3.2.0
picoruby-3.0.0
truffleruby-23.0.0
truffleruby+graalvm-23.0.0
```

### 원하는 버전의 ruby 설치
조회된 목록에서 설치하고자하는 버전을 확인합니다. 
예를 들어, 버전 3.1.4의 ruby는 다음과 같이 설치할 수 있습니다. 
```sh
rbenv install 3.1.4
```

### 정상 설치 확인
원하는 버전의 ruby가 잘 설치되었는지 확인해 봐야겠죠?
다음 명령어로 rbenv에 설치된 전체 ruby 버전들의 목록을 뽑을 수 있습니다. 
```sh
rbenv versions

    system
    2.7.4
    2.7.5
  * 2.7.6 (set by /Users/padawanjoy/.rbenv/version)
    3.1.4
```
출력된 목록에서 설치한 버전이 보여지면 잘 설치가 된 것 입니다.

### 설치한 ruby 버전 사용
다음 명령어를 실행해서 설치한 ruby 버전을 사용하는 것으로 설정해 보겠습니다. 예를 들어, 3.1.4 버전을 사용한다고 설정하는 방법은 다음과 같습니다. 
```sh
rbenv global 3.1.4
```

## Jekyll 구조 적용하기
ruby 사용 환경 준비가 완료되었습니다. 이제 본격적으로 Jekyll 테마를 적용해보겠습니다. 

### Jekyll와 Bundler 설치
Jekyll와 Bundler를 설치해 보겠습니다. Bundler는 Ruby 프로그래밍 언어에서 사용하는 의존성 관리 도구입니다. Ruby 프로젝트를 진행할 때, 다양한 라이브러리(젬, gems)를 사용하게 되는데, 각 라이브러리들이 서로 다른 버전의 다른 라이브러리들과 호환되어야 하는 경우가 잦습니다. Bundler는 이러한 의존성들을 적절히 관리해주며, 프로젝트가 필요로 하는 모든 젬들이 올바른 버전으로 설치되도록 도와줍니다.

아래 명령어로 Jekyll와 Bundler를 모두 설치해 보겠습니다.
```sh
gem install jekyll bundler
```

### index.html 제거
Jekyll 테마를 적용하기에 앞서, 불필요한 파일을 제거해주는게 좋습니다. 지난 포스트에서 만들었던 index.html 파일을 제거해 주겠습니다. 만약 지난 포스트에서 index.html을 만들지 않았거나, 지난 포스트를 보지 않고 지금 이 포스트부터 보는 경우, index.html 파일이 없을테니 이 단계는 건너뛰어도 됩니다. 
```sh
rm -f index.html 
```

### Jekyll 구조 적용
이제 우리 블로그를 Jekyll 구조로 변환하겠습니다. 
```sh
jekyll new ./ 
```
위 명령어를 수행하면 관련 파일과 폴더들이 다운로드 되면서 jekyll 테마를 위한 프로젝트 구조가 적용됩니다. 

이 과정에서 간혹 다음과 같은 오류가 발생할 수도 있다.
```sh
Conflict: /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io exists and is not empty.
Ensure /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io is empty or else try again with '—force' to proceed and overwrite any files.
```
이런 오류가 발생하면 **`--force`** 옵션을 붙여서 명령어를 수행하면 됩니다. 
```sh
jekyll new ./ —force 
```

### 젬(gem) 의존성 설치
프로젝트의 루트 디렉토리를 보면 Gemfile이라는 파일이 있을텐데요. 여기에는 모든 젬(gem) 의존성이 명시되어있습니다. 이 의존성들을 설치해 주겠습니다. 설치 명령어는 다음과 같습니다. 
```sh
bundle install
```

## 블로그 확인하기 
지금까지의 과정을 통해 우리 블로그는 jekyll가 적용된 블로그가 되었습니다. 이 블로그를 GitHub에 업로드하기 전에 제대로 jekyll가 적용된건지 확인을 해봐야겠죠?

### 로컬에서 구동
아래 명령어로 로컬 서버를 구동하여 우리 블로그를 미리 확인해 볼 수 있습니다.
```sh
bundle exec jekyll serve
```
이제 브라우져에서 **`http://127.0.0.1:4000/`** 또는 **`http://localhost:4000/`** 으로 접속해보면 jekyll 기본 형태가 적용된 우리 블로그 모습을 확인할 수 있습니다. 

![로컬에서 Jekyll 블로그 미리보기]({{site.baseurl}}/images/posts/2024-04-17-part2-create-a-jekyll-project-structure/01.webp)

실행 중인 서버는 터미널(명령프롬프트)에서 Mac을 사용하는 경우 **`Cmd+C`**, Windows를 사용하는 경우 **`Ctrl+C`**를 입력하면 중지시킬 수 있습니다. 

## 마무리
우리 블로그를 jekyll 프로젝트 구조로 적용해 보았습니다. 이제 다양한 jekyll 테마들을 찾아보고 적용하는 단계가 남았는데요. 이에 대한 내용은 다음 포스트에서 자세히 알아보도록 하겠습니다. 