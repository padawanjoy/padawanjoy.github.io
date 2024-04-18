---
layout: post
title: "GitHub 블로그 만들기 3 - Jekyll 테마 적용하기"
date:   2024-04-18 10:45:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-18-part3-applying-a-jekyll-theme/00.webp'
tags: [github, blog, github-pages, ruby, rbenv, Jekyll]
tags_color: '#4a8e46'
featured: true
---
[지난 포스트](https://padawanjoy.com/blog/part2-create-a-jekyll-project-structure)에서 Jekyll 프로젝트 구조를 적용해 보았습니다. 지난 포스트에서 진행했던 내용에 이어서, 이쁘고 멋진 Jekyll 테마를 찾아 우리 블로그에 적용하는 방법을 알아보도록 하겠습니다.

## 목차
- [Jekyll 테마 적용하기](#jekyll-테마-적용하기)
    - [jekyll 테마 선택](#jekyll-테마-선택)
    - [테마 다운로드](#테마-다운로드)
    - [다운받은 테마의 젬(gem) 의존성 설치](#다운받은-테마의-젬gem-의존성-설치)
    - [테마 적용 확인](#테마-적용-확인)
- [테마 수정하기](#테마-수정하기)
- [블로그 업로드](#블로그-업로드)
    - [GitHub에 업로드](#github에-업로드)
    - [블로그 확인](#블로그-확인)
- [마무리](#마무리)

<br>
## Jekyll 테마 적용하기 
Jekyll 프로젝트 구조를 적용하고 보여지는 기본 테마는 조금 밋밋했죠. 다행히 이쁘고 멋진 jekyll 테마가 아주 많이 있습니다. 다양한 테마를 살펴보고 우리가 원하는 테마를 어떻게 적용하면 되는지 알아보겠습니다. 

### jekyll 테마 선택
아래 사이트들에 정말 다양한 테마들이 많이 있습니다. jekyll 테마들을 살펴보고 마음에 드는 테마를 찾아봅시다.
- [http://jekyllthemes.org/](http://jekyllthemes.org/)
- [https://jekyllthemes.io/free](https://jekyllthemes.io/free)
- [http://themes.jekyllrc.org/](http://themes.jekyllrc.org/)
- [https://github.com/topics/jekyll-theme](https://github.com/topics/jekyll-theme)

### 테마 다운로드
마음에 드는 테마를 찾았으면 다운로드 버튼을 클릭해서 테마를 다운로드 받거나, 해당 테마의 github 페이지로 이동해서 다운로드 받습니다.

다운로드 받은 테마의 압축을 해제하고, 폴더와 파일들을 모두 복사해서 내 블로그 폴더 안에 붙여넣기 합니다. 이미 동일 파일명이 있는 경우 덮어쓰기를 해주세요.

### 다운받은 테마의 젬(gem) 의존성 설치
내 블로그 폴더에 다운로드 받은 테마의 폴더와 파일을 넣어줬습니다. 이제 다운로드 받은 테마의 의존성을 설치해 주어야 합니다. 다음 명령어로 의존성들을 설치해 주세요.
```sh
bundle install
```

### 테마 적용 확인
의존성 설치가 완료되었다면, 다시 한번 로컬 서버를 구동하여 다운로드 받은 테마가 내 블로그에 제대로 적용되었는지 확인해 보겠습니다. 
```sh
bundle exec jekyll serve
```
브라우져에서 **`http://127.0.0.1:4000/`** 또는 **`http://localhost:4000/`** 으로 접속해서 테미가 잘 적용되었는지 확인합니다. 

단, 테마에 따라서, http://127.0.0.1:4000/ 또는 http://localhost:4000/ 가 아닌 **`하위 경로`**까지 입력해야 하는 경우가 있을 수 있습니다. 터미널에 출력된 내용 중에 **`Server address`** 라는 부분을 확인하면 정확한 로컬 접속 주소를 알 수 있습니다. 
```sh
done in 1.149 seconds.
Auto-regeneration: enabled for '/Users/padawanjoy/Documents/Padawan_Joy/padawanjoy.github.io'
Server address: http://127.0.0.1:4000/Type-on-Strap/
Server running... press ctrl-c to stop.
```

![테마 적용 확인하기]({{site.baseurl}}/images/posts/2024-04-18-part3-applying-a-jekyll-theme/01.webp)
다운로드 받은 테마로 잘 적용된 모습입니다.

## 테마 수정하기
다운로드 받은 테마는 수정도 할 수 있습니다. 일반적으로 config.xml 파일을 수정하면 되는데요. 테마별로 자세한 수정 방법은 다운받은 테마의 github 페이지 또는 Readme.md 파일에서 확인할 수 있습니다. 개발에 익숙한 사람은 직접 소스 수정을 해서 커스터마이징도 할 수 있는데요. 단, 이때는 테마에 적용된 라이선스를 꼭 확인하고 수정을 해야겠습니다. 

## 블로그 업로드
새로운 테마가 적용된 우리의 블로그를 GitHub 저장소에 업로드를 해야 온라인 상에 공개가 되겠죠?

### GitHub에 업로드
아래와 같은 방법으로 GitHub에 Push를 하게 되면 수정한 파일들이 저장소로 업로드가 되고, 그럼 자연스럽게 호스팅까지 완료가 됩니다. 
```sh
padawanjoy@MacStudio padawanjoy.github.io % git add *
padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Applied new theme"
padawanjoy@MacStudio padawanjoy.github.io % git push
```

### 블로그 확인
**`https://yourusername.github.io`** 에 접속해서 정상적으로 적용한 테마가 보여지는지, 블로그를 확인해 줍니다. 단, git push를 수행한 후 변경 사항이 적용되는 데에는 시간이 소요될 수 있으니 몇 분 후에 새로고침하면서 확인해 주세요.

## 마무리
GitHub Pages 블로그에 jekyll 테마를 어떻게 적용하는지, 자세히 알아보았습니다. 다른 완성형 블로그 서비스에 비하면 GitHub Pages 블로그와 Jekyll 테마를 사용하는 것은 분명 쉽지 않습니다. 처음 적용해보며 어려움을 겪는 분들에게 부족하지만 이 포스트가 도움이 되길 바랍니다.