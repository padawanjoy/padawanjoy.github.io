---
layout: post
title: "GitHub 블로그 만들기: 파트 1 - GitHub Pages 블로그 구축하기"
date:   2024-01-11 16:43:00 +0900
author: padawanjoy
tags: [github, blog, github-pages]
featured: true
---

안녕하세요! 오늘은 GitHub 블로그 만드는 방법을 공유하고자 합니다. GitHub 블로그는 많은 장점을 가지고 있지만, 초보자에게는 다소 복잡해 보일 수 있습니다. 이 포스트가 그런 분들에게 도움이 되길 바라면서 적어보겠습니다.

참고로 이 포스트는 2024년 1월 Mac OS 환경 기준으로 작성하였으니 참고해서 읽어주세요.

<br>
## **시작하기 전에**

1. 먼저, [github.com](http://github.com/)으로 가서 로그인하세요. 아직 가입하지 않았다면, 가입을 먼저 해주세요.
1. 로그인 후, 대시보드에서 "Create repository" 버튼을 클릭합니다.

!["Create repository" 버튼 클릭하기]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/01.png"}})

<br>
## **레포지토리 생성하기**

1. 레포지토리 이름을 **`yourusername.github.io`** 형식으로 작성합니다. 이런 이름 형식은 GitHub 블로그가 올바르게 작동하는 데 필수적입니다.
1. "Public"을 선택하고 "Add a README file" 옵션을 체크하세요.
1. "Create repository"를 클릭하면 **`yourusername.github.io`** 레포지토리가 생성됩니다.

![레포지토리 생성하기]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/02.png"}})

<br>
## **블로그 소스 파일 다운로드하기**

1. 다음으로 "Code" 버튼을 클릭하면 나타나는 Clone address를 복사하세요.
![Clone address 복사하기]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/03.png"}})
1. 터미널(명령프롬프트)을 엽니다.
- Mac 사용자는 Cmd+Space로 “Spotlight Search”를 사용하여 터미널을 찾을 수 있습니다.
- Windows 사용자는 검색 바에서 "cmd"를 검색하여 CMD(명령프롬프트)를 열 수 있습니다.
1. 원하는 디렉토리로 이동하세요. **`cd 원하는디렉토리경로`**를 입력하여 원하는 디렉토리로 이동할 수 있습니다.
1. **`git clone 복사한CloneAddress`**를 입력하고 실행하세요.
<br>
    GitHub 인증이 필요한 경우, GitHub 사용자 이름으로 Username을, 비밀번호로는 Personal access token을 입력하면 됩니다. Personal access token이 무엇인지 모르거나 아직 생성하지 않았다면, 아래 포스트를 먼저 참고해 주세요.
    
    > [GitHub Personal Access Token 생성하기](https://padawanjoy.com/blog/generating-a-github-personal-access-token)

<br>
만약 폴더 경로 **`/Users/padawanjoy/Documents/Blog`**으로 복제(Clone)하려면 다음과 같이 입력해야 합니다.
```bash
padawanjoy@MacStudio / % cd /Users/padawanjoy/Documents/Blog
padawanjoy@MacStudio / % git clone https://github.com/padawanjoy/padawanjoy.github.io.git
```
<br>
## **블로그 만들기**

1. yourusername.github.io 폴더가 생겼을 겁니다. 이 폴더로 이동하세요.
1. "Welcome to my new GitHub Blog."라는 텍스트가 포함된 index.html 파일을 만드세요.
1. 파일이 제대로 생성되었는지 확인한 다음, 변경 사항을 Add, Commit, Push 해 주세요.

예를 들어, 복제된 폴더 이름이 _padawanjoy.github.io_라면...
```bash
padawanjoy@MacStudio Blog % cd padawanjoy.github.io
padawanjoy@MacStudio padawanjoy.github.io % echo "Welcome to my new GitHub Blog" > index.html
padawanjoy@MacStudio padawanjoy.github.io % git add *
padawanjoy@MacStudio padawanjoy.github.io % git commit -m "Initial commit"
padawanjoy@MacStudio padawanjoy.github.io % git push -u origin main
```
<br>
## **블로그 확인하기**

1. **https://github.com/yourusername/yourusername.github.io**를 방문하여 모든 것이 올바르게 Push 되었는지 확인하세요.
<br>
    아래 그림과 같이, 빨간색으로 표시된 영역에 있는 초록색 체크 표시는 _git push_가 완료되었음을 나타냅니다. _git push_가 진행 중일 때는 노란색 점이 표시됩니다.
    ![git push 완료]({{ "/images/posts/2024-01-11-Part1-Building-Your-First-GitHub-Pages-Blog/04.png"}})
1. 이제 브라우저에서 **https://yourusername.github.io**에 접속하세요. "Welcome to my new GitHub Blog!" 메시지가 보여야 합니다!

<br>
## **마무리**

GitHub 블로그 만드는 과정을 살펴봤습니다. 생각보다 복잡하지는 않죠? 이제 인터넷에 자신만의 공간이 생겼는데요. 하지만 아직 우리가 흔히 알고 있는 블로그처럼 보이지는 않습니다. 그렇다면 블로그처럼 보이도록 꾸며봐야겠죠? [다음 글에서 새로 만든 블로그를 아름답게 꾸미는 방법을 탐색할 예정이니, 기대해주세요.](https://padawanjoy.com/blog/part2-applying-a-jekyll-theme).🌟