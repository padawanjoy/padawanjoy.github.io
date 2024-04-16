---
layout: post
title: "GitHub 블로그 만들기 1 - GitHub Pages 블로그 생성하기"
date:   2024-04-16 09:31:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-16-part1-building-your-first-github-pages-blog/00.webp'
tags: [github, blog, github-pages]
tags_color: '#4a8e46'
featured: true
---
요즘 다양한 블로그 서비스들이 많죠. 이번 포스트에서는 많은 블로그 서비스들 중에서 GitHub Pages를 이용해서 블로그 만드는 방법을 공유해보려고 합니다. GitHub 블로그는 많은 장점을 가지고 있지만, 사용자가 하나하나 직접 구성을 해야하다보니 처음 만들 때에 좀 복잡할 수 있습니다. 그럼 단계별로 하나씩 알아볼게요.

## 목차
- [GitHub Pages 서비스](#github-pages-서비스)
- [GitHub Pages 블로그 생성하기](#github-pages-블로그-생성하기)
    - [시작하기](#시작하기)
    - [Repository 생성하기](#repository-생성하기)
    - [소스 파일 다운로드하기](#소스-파일-다운로드하기)
    - [블로그 페이지 만들기](#블로그-페이지-만들기)
    - [블로그 페이지 확인하기](#블로그-페이지-확인하기)
- [마무리](#마무리)

<br>
## GitHub Pages 서비스
시작하기 전에 GitHub Pages가 무엇인지 알아볼게요. GitHub Pages는 GitHub에서 제공하는 정적 웹사이트 호스팅 서비스입니다. GitHub의 저장소(repository)에 HTML, CSS, JavaScript 파일 등을 저장하여 간단하게 웹사이트를 배포할 수 있게 해주는 서비스이죠. 이 서비스는 무료로 제공되며, 개인 프로젝트, 포트폴리오, 프로젝트 문서 등 다양한 용도로 사용될 수 있는데요. 우리는 이 서비스를 이용해서 블로그를 만들어보려고 합니다.

## GitHub Pages 블로그 생성하기

### 시작하기
1. [github.com](http://github.com/)에 로그인을 합니다. 아직 가입하지 않았다면, 가입을 먼저 해주세요.
1. 로그인 후 보여지는 대시보드 페이지에서 **`"Create repository"`** 버튼을 클릭합니다.

!["Create repository" 버튼 클릭하기]({{site.baseurl}}/images/posts/2024-04-16-part1-building-your-first-github-pages-blog/01.webp)

### Repository 생성하기
1. Repository 이름을 **`yourusername`**.github.io 형식으로 작성합니다. Owner 칸에 보여지는 user name을 동일하게 사용해서 {user name}.github.io 형식으로 꼭 작성해 주세요.
1. **`"Public"`**을 선택하고 **`"Add a README file"`** 옵션을 체크하세요.
1. 하단의 초록색 **`"Create repository"`** 버튼을 클릭하면 **`yourusername`**.github.io repository가 생성됩니다.

![repository 생성하기]({{site.baseurl}}/images/posts/2024-04-16-part1-building-your-first-github-pages-blog/02.webp)

### 소스 파일 다운로드하기
1. **`yourusername`**.github.io 이름의 Repository 가 생성되었고, 해당 페이지가 보여집니다.
1. **`"Code"`** 버튼을 클릭하면 나타나는 **`Clone address`**를 복사합니다.
![Clone address 복사하기]({{site.baseurl}}/images/posts/2024-04-16-part1-building-your-first-github-pages-blog/03.webp)
1. 터미널(명령프롬프트)을 엽니다.
 - Mac 사용자는 Cmd+Space로 “Spotlight Search”를 사용하여 **`터미널`**을 찾을 수 있습니다.
 - Windows 사용자는 검색 바에서 "cmd"를 검색하여 **`CMD(명령프롬프트)`**를 열 수 있습니다.
1. 터미널(명령프롬프트)에서 소스 파일을 다운로드 받을 경로로 이동해 주세요. **`cd 원하는디렉토리경로`**를 입력하면 이동할 수 있습니다. 
```sh
cd samplepath
```
1. 이동한 경로에 앞서 생성한 repository의 소스 파일을 다운로드 받아봅시다. 아래와 같은 명령어로 다운받을 수 있습니다. 
```sh
git clone copiedcloneaddress
```
 git clone 과정에서 permission error가 뜨면서 github 인증 정보 (username과 password)를 입력하라고 나올 수도 있습니다. username으로는 GitHub의 **`username (Owner)`**을 입력하고, password 값으로는 **`Personal access token`** 값을 입력합니다. **`Personal access token`** 값에 대한 자세한 내용은 [**`이 글`**](https://padawanjoy.com/blog/create-a-github-personal-access-token)을 참고해 주세요.
 <br>
 <br>
 만약 폴더 경로 **`/Users/padawanjoy/Documents/Blog`**으로 복제(Clone)하려면 다음과 같이 입력하면 됩니다.
 ```sh
 padawanjoy@MacStudio / % cd /Users/padawanjoy/Documents/Blog
 padawanjoy@MacStudio / % git clone https://github.com/sample/sample.github.io.git
 ```

### 블로그 페이지 만들기
1. 위의 단계까지 완료하면 다운받으려고 입력했던 경로 내에 **`yourusername`**.github.io라는 폴더가 생겼을 겁니다. 이 폴더로 이동합니다.
1. "Welcome to my new GitHub Blog."라는 텍스트가 포함된 index.html 파일을 하나 만들어보겠습니다.
1. 파일이 제대로 생성되었는지 확인하고, **`yourusername`**.github.io 폴더 내의 이런 변경 사항들을 add → commit → push 해서 GitHub repository로 업로드해 주겠습니다. 
 <br>
 <br>
 예를 들어, 복제된 폴더 이름이 _padawanjoy.github.io_라면...
 ```sh
 padawanjoy@MacStudio Blog % cd padawanjoy.github.io
 padawanjoy@MacStudio padawanjoy.github.io % echo "Welcome to my new GitHub Blog" > index.html
 padawanjoy@MacStudio padawanjoy.github.io % git add *
 padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Initial commit"
 padawanjoy@MacStudio padawanjoy.github.io % git push -u origin main
 ```

### 블로그 페이지 확인하기
1. **`https://github.com/yourusername/yourusername.github.io`**에 접속합니다. 우리가 앞서 만들었던 GitHub Pages의 Repository 주소입니다. 아래 이미지에서 표시한 부분을 통해 git push 처리가 완료되었는지 여부를 확인할 수 있습니다. 
 <br>
 <br>
 아래 그림과 같이, git push가 아직 진행 중일 때는 노란색 점으로 보여지고, git push가 완료되면 초록색 체크 표시가 보여집니다.
 ![git push 완료]({{site.baseurl}}/images/posts/2024-04-16-part1-building-your-first-github-pages-blog/04.webp)
1. git push가 완료되면, 브라우져에서 **`https://yourusername.github.io`** 으로 접속해 보겠습니다. 우리가 입력했던 “Welcome to my new GitHub Blog” 라고 뜨는 페이지를 확인할 수 있습니다. 

## 마무리
GitHub Pages 블로그를 생성하는 과정을 살펴봤습니다. 다른 완성형 블로그 서비스보다는 복잡할 . 수있지만 위 과정들을 천천히 따라하면 큰 어려움 없이 진행이 되실거에요. 하지만 아직 우리가 일반적으로 알고 있는 블로그라고 하기에는 창피한 수준이죠? 아직 블로그처럼 꾸미는 단계가 남아있기 때문입니다. 다음 글에서 지금까지 만든 페이지를 정말 블로그답게 꾸미는 방법을 알아볼테니 다음 포스트도 꼭 봐주세요!🌟