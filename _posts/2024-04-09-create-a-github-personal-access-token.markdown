---
layout: post
title: "GitHub Personal Access Token(PAT) 만들기"
date: 2024-04-09 09:58:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-09-create-a-github-personal-access-token/00.webp'
tags:   [github, git, personal-access-token, pat]
tags_color: '#4a8e46'
featured: true
---
개발을 하거나 프로젝트를 관리하다보면 소스 코드의 버전 관리가 꼭 필요하죠. 이를 위해 GitHub을 많이 이용하게 됩니다. GitHub의 API를 통해 GitHub과 상호 작용을 하려면 GitHub Personal Access Token(PAT)을 사용하게 되는데요. 이번 포스트에서 바로 이 GitHub Personal Access Token을 어떻게 만들 수 있는지를 알아보겠습니다. 

## 목차
- [Git과 GitHub에 대해](#git과-github에-대해)
  - [Git](#git)
  - [GitHub](#github)
- [GitHub Personal Access Token이 필요한 이유](#github-personal-access-token이-필요한-이유)
- [GitHub Personal Access Token 만들기](#github-personal-access-token-만들기)
  - [Step 1: GitHub에 접속하기](#step-1-github에-접속하기)
  - [Step 2: 프로필 이미지 클릭하기](#step-2-프로필-이미지-클릭하기)
  - [Step 3: Settings 메뉴 클릭하기](#step-3-settings-메뉴-클릭하기)
  - [Step 4: Developer Settings 클릭하기](#step-4-developer-settings-클릭하기)
  - [Step 5: Personal access tokens로 이동하기](#step-5-personal-access-tokens로-이동하기)
  - [Step 6: Generate new token 클릭하기](#step-6-generate-new-token-클릭하기)
  - [Step 7: GitHub 계정 비밀번호 입력하기](#step-7-github-계정-비밀번호-입력하기)
  - [Step 8: token에 대한 Note 작성하기](#step-8-token에-대한-note-작성하기)
  - [Step 9: 필요한 scope 선택하기](#step-9-필요한-scope-선택하기)
  - [Step 10: 생성 버튼 클릭하기](#step-10-생성-버튼-클릭하기)
  - [Step 11: 토큰 정보 저장해두기](#step-11-토큰-정보-저장해두기)
- [마무리](#마무리)

<br>
## Git과 GitHub에 대해
GitHub Personal Access Token을 알아보기 전에, Git이 무엇인지, 그리고 GitHub은 무엇인지를 간단하게 알아보고 가겠습니다. 

### Git
Git은 분산 버전 관리 시스템(DVCS)으로, 여러 사람이 공동으로 작업하는 프로젝트에서 소스 코드의 버전(변경 이력)을 관리하는 데 사용됩니다. 2005년 리눅스 토르발스에 의해 개발되었고, 프로젝트의 소스 코드를 효율적으로 관리할 수 있게 해주었죠. Git을 사용하면 개발자들은 로컬 컴퓨터에서 작업을 하면서도 변경 사항을 추적하고, 이전 버전으로 쉽게 돌아갈 수 있으며, 다른 개발자와 변경 사항을 쉽게 공유할 수 있어서 현재 가장 많이 사용되는 버전 관리 시스템 중 하나입니다. 

### GitHub
GitHub은 Git을 사용하는 프로젝트를 위한 웹 기반 호스팅 서비스로, 개발자가 소프트웨어 프로젝트를 위한 버전 관리 및 협업 기능을 사용할 수 있게 해줍니다. GitHub을 사용하면 개발자들이 자신의 프로젝트를 공개하거나, 다른 프로젝트에 기여하거나, 타인의 프로젝트를 복제(clone)할 수도 있습니다. 또한, 이슈 추적, 코드 리뷰, 프로젝트 관리 등 다양한 협업 도구를 제공하여 프로젝트의 효율적인 진행을 도와주기 때문에 정말 많이 사용되는 서비스가 되었습니다. 

## GitHub Personal Access Token이 필요한 이유
GitHub Personal Access Token은 사용자가 로컬 환경이나 애플리케이션에서 GitHub의 리소스와 안전하게 상호작용할 수 있게 해주는 인증 토큰입니다. GitHub과 상호작용을 할 때, username과 password가 필요한데, 이 password 대신 Personal Access Token을 사용하는 것이죠. 그럼, 왜 비밀번호가 아니라 GitHub Personal Access Token을 사용하는 것 일까요?

- **보안 강화**: GitHub 계정 비밀번호를 직접 사용하는 것은 보안상 취약점이 될 수 있습니다. Personal Access Token은 혹시나 노출이 되더라도, 할당된 권한 이외에는 접근이 제한되기 때문에 피해를 줄일 수 있습니다. 
- **접근 제어**: Personal Access Token에는 디테일하게 권한을 설정해서 부여할 수 있습니다. 예를 들어, 특정 API에 대한 읽기 권한만 부여하거나, 리포지토리 관리 권한을 제한적으로 부여할 수 있습니다.
- **비밀번호 변경에 따른 영향 최소화**: Personal Access Token은 GitHub 계정의 비밀번호와 독립적으로 작동합니다. 비밀번호를 변경하더라도 토큰은 영향을 받지 않기 때문에, 인증이 필요한 서비스나 통합에 대한 접근이 비밀번호 변경과 상관없이 지속적으로 유지된다는 장점이 있습니다. 
- **모니터링 용이성**: Personal Access Token을 사용하면, 어떤 토큰이 어떤 서비스에 사용되었는지 추적하기가 쉬워집니다. 의심스러운 활동이 감지될 경우 즉각적으로 토큰을 폐기해서 더 이상 접근할 수 없도록 조치할 수도 있죠.

## GitHub Personal Access Token 만들기 
본격적으로 GitHub Personal Access Token을 어떻게 만들 수 있는지, 한 단계 한 단계씩 자세히 알아보겠습니다.

### Step 1: GitHub에 접속하기
[GitHub](https://github.com/)에 접속해서 로그인을 합니다.

### Step 2: 프로필 이미지 클릭하기 
![프로필 이미지 클릭하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/01.webp)

오른쪽 상단에 위치한 프로필 이미지를 클릭하세요. 

### Step 3: Settings 메뉴 클릭하기 
![Settings 메뉴 클릭하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/02.webp)

드롭다운 메뉴에서 'Settings'을 선택하세요.

### Step 4: Developer Settings 클릭하기 
![Developer Settings 클릭하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/03.webp)

Settings 페이지 메뉴 중에서 Developer Settings를 클릭합니다. 

### Step 5: Personal access tokens로 이동하기 
![Personal access tokens로 이동하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/04.webp)

Developer Settings 페이지 메뉴 중에서 Personal access tokens을 선택하고, 서브 메뉴에서 Tokens (classic)을 클릭합니다. 

### Step 6: Generate new token 클릭하기
![Generate new token 클릭하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/05.webp)

'Generate new token' 펼침 버튼을 클릭하고, 'Generate new token (classic)'을 클릭하세요.

### Step 7: GitHub 계정 비밀번호 입력하기 
![GitHub 계정 비밀번호 입력하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/06.webp)

토큰을 생성할 수 있는 권한을 가진 사용자인지 확인하기 위해 GitHub 계정의 로그인 비밀번호를 입력합니다. 

### Step 8: token에 대한 Note 작성하기
![token에 대한 Note 작성하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/07.webp)

새로 생성할 토큰에 대한 Note를 작성합니다. 일반적으로 토큰의 이름, 사용 목적, 프로젝트 이름 등을 입력해서 다른 토큰과 구분할 수 있도록 작성합니다.  

### Step 9: 필요한 scope 선택하기
![필요한 scope 선택하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/07_1.webp)

토큰이 가질 권한 범위를 선택해 줍니다.

### Step 10: 생성 버튼 클릭하기 
![생성 버튼 클릭하기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/08.webp)

이제 'Generate token' 버튼을 클릭하여 토큰을 생성하세요.

### Step 11: 토큰 정보 저장해두기 
![토큰 정보 저장해두기]({{site.baseurl}}/images/posts/2024-04-09-create-a-github-personal-access-token/09.webp)

토큰이 드디어 발급되었습니다. 발급된 토큰은 지금 바로 이 때만 확인할 수 있습니다. 다른 페이지로 이동하기 전에 반드시 복사해서 안전한 곳에 저장해둡니다.

## 마무리
GitHub Personal Access Token 만드는 방법을 알아봤습니다. 다른 포스트에서 이 토큰을 어떨 때 사용하는지 또 알아볼 기회가 있을 것 같네요. 토큰 생성이 어려운 내용은 아니지만 처음 생성하는 분들에게는 생소할 수 있으니, 이 포스트가 도움이 되었으면 좋겠네요. 😁