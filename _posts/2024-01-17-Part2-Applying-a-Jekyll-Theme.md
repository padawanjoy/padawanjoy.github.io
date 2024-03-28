---
layout: post
title: "GitHub 블로그 만들기: 파트 2 - Jekyll 테마 적용하기"
date:   2024-01-17 12:37:00 +0900
author: padawanjoy
tags: [github, blog, github-pages, ruby, rbenv, Jekyll]
featured: true
---
안녕하세요. 지난 번에 [GitHub 블로그를 시작하는 방법](https://padawanjoy.com/blog/part1-building-your-first-github-pages-blog)을 알아봤는데요. 이제 Jekyll 테마를 적용하여 블로그를 꾸며보겠습니다.

<br>
## **Ruby 설치하기**
먼저 Jekyll 테마를 사용하려면 Ruby를 설치해야 합니다. Mac OS에는 Ruby가 기본적으로 포함되어 있지만, 새로 설치해 보겠습니다.

* #### **rbenv로 Ruby 버전 관리하기**
rbenv는 여러 버전의 Ruby를 관리하는 도구입니다. 여러 버전의 Ruby를 설치할 수 있고, 프로젝트 별로 환경이나 요구사항에 맞게 서로 다른 버전의 Ruby를 사용할 수 있게 해줍니다.

* #### **rbenv 설치하기**
GitHub 블로그 폴더로 이동하여 rbenv를 설치합니다.
```bash
padawanjoy@MacStudio / % cd yourgithubblogpath
padawanjoy@MacStudio padawanjoy.github.io % brew install rbenv
```

* #### **Ruby 버전 확인 및 설치하기**
사용 가능한 Ruby 버전 목록을 확인하고, 설치하고자 하는 버전을 설치합니다. 
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv install -l
3.0.6
3.1.4
3.2.2
jruby-9.4.3.0
mruby-3.2.0
picoruby-3.0.0
truffleruby-23.0.0
truffleruby+graalvm-23.0.0
```
예를 들어, 버전 3.1.4를 선택한 경우 다음과 같이 설치합니다:
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv install 3.1.4
```

<br>
## **Ruby 버전 설정하기**
새로 설치한 Ruby 버전을 시스템의 기본값으로 설정합니다.
```bash
padawanjoy@MacStudio padawanjoy.github.io % rbenv global 3.1.4
```

<br>
## **Jekyll 및 Bundler 설치하기**
이제 Jekyll과 Bundler를 함께 설치합니다.
```bash
padawanjoy@MacStudio padawanjoy.github.io % gem install jekyll bundler
```

<br>
## **기존 index.html 파일 제거하기**
지난 포스트에서 테스트를 위해 index.html 파일을 생성했다면, 이제 제거해 주겠습니다.
```bash
padawanjoy@MacStudio padawanjoy.github.io % rm -f index.html
```

<br>
## **Jekyll 블로그 구조 생성하기**
블로그를 Jekyll 구조로 변환합니다.
```bash
padawanjoy@MacStudio padawanjoy.github.io % jekyll new ./
```
만약 다음과 같은 문제가 발생하면 --force 옵션을 사용합니다.
```bash
Conflict: /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io exists and is not empty.
Ensure /Users/padawanjoy/Documents/Padawan_Joy/padawanjoy•github.io is empty or else try again with '—force' to proceed and overwrite any files.

padawanjoy@MacStudio padawanjoy.github.io % jekyll new ./ --force
```

<br>
## **Bundle Install로 Jekyll 설정 완료하기**
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle install
```

<br>
## **로컬에서 Jekyll 블로그 미리보기**
아래 명령어로 로컬 서버를 구동하여 블로그를 확인합니다. 
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve
```
브라우저에서 `http://127.0.0.1:4000/` 또는 `http://localhost:4000/`을 방문하여 Jekyll이 적용된 블로그를 확인합니다.

![로컬에서 Jekyll 블로그 미리보기]({{ "/images/posts/2024-01-17-Part2-Applying-a-Jekyll-Theme/01.png"}})

로컬 서버를 중지하려면, Mac을 사용하는 경우 `Cmd+C`, Windows를 사용하는 경우 `Ctrl+C`를 누르세요.

<br>
## **Jekyll 테마 선택 및 적용하기**
다양한 사이트를 둘러보고 마음에 드는 Jekyll 테마를 찾아 다운로드 합니다.
- [http://jekyllthemes.org/](http://jekyllthemes.org/)
- [https://jekyllthemes.io/free](https://jekyllthemes.io/free)
- [http://themes.jekyllrc.org/](http://themes.jekyllrc.org/)
- [https://github.com/topics/jekyll-theme](https://github.com/topics/jekyll-theme)

<br>
## **테마 적용하기**
다운로드한 테마의 파일과 폴더를 복사하여 블로그 폴더에 붙여넣으세요. 동일한 이름의 파일이 이미 있다면 덮어쓰세요.

<br>
## **Bundle로 테마 설치하기**
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle install
```

<br>
## **테마 적용 확인하기**
로컬 서버를 실행하여 새 테마가 적용되었는지 확인하세요.
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve
```
테마에 따라 `http://127.0.0.1:4000/` 또는 `http://localhost:4000/`에 추가로 서브 패스(하위 경로)를 입력해야 할 수 있습니다. 정확한 주소는 터미널 출력의 'Server address' 섹션을 확인하여 알아낼 수 있습니다.
```bash
padawanjoy@MacStudio padawanjoy.github.io % bundle exec jekyll serve

[...] (생략)

done in 1.149 seconds.
Auto-regeneration: enabled for '/Users/padawanjoy/Documents/Padawan_Joy/padawanjoy.github.io'
Server address: http://127.0.0.1:4000/Type-on-Strap/
Server running... press ctrl-c to stop.

```
![테마 적용 확인하기]({{ "/images/posts/2024-01-17-Part2-Applying-a-Jekyll-Theme/02.png"}})
테마가 성공적으로 적용되었습니다.

<br>
## **테마 수정하기 (커스터마이징)**
config.xml 파일을 수정하여 각 테마를 커스터마이징할 수 있습니다.

자세한 커스터마이징 지침은 다운로드한 테마의 GitHub 페이지에서 찾을 수 있습니다. 개발에 익숙한 사람들은 소스 코드를 직접 수정하여 테마를 원하는대로 개선시킬 수도 있습니다. 단, 변경을 진행하기 전에 테마에 적용된 라이선스를 반드시 확인하세요.

<br>
## **업데이트된 블로그를 GitHub에 업로드하기**
```bash
padawanjoy@MacStudio padawanjoy.github.io % git add *
padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Applied new theme"
padawanjoy@MacStudio padawanjoy.github.io % git push -u origin main
```

<br>
## **블로그 확인하기**
`https://yourusername.github.io`를 방문하여 새 테마가 적용된 블로그를 확인하세요. git push를 수행한 후 변경 사항이 적용되는 데에는 시간이 소요될 수 있습니다.

GitHub 블로그에 Jekyll 테마를 어떻게 적용하는지 알아봤습니다. 멋진 블로그를 만드는데 도움이 되었길 바랍니다!