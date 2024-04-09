---
layout: post
title:  "SDKMAN!으로 자바 버전 관리하기"
date:   2024-01-29 12:17:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-29-managing-java-versions-with-sdkman/01.png'
tags:   [sdkman, java]
# tags_color: '#6b96df'
featured: false
---
이번 글에서는 Mac OS에서 다양한 자바 버전을 관리하는 방법을 알아보겠습니다. 자바 버전 관리가 복잡하다고 생각했다면, SDKMAN!이라는 도구가 큰 도움이 될 것 같습니다. 시작해볼까요?

## SDKMAN! 설치하기
먼저, SDKMAN!을 설치해야 합니다. Mac OS 터미널에서 다음 명령어를 입력하세요:

```bash
$ curl -s "https://get.sdkman.io" | bash
```

설치가 완료되면, zsh 환경에서 SDKMAN!을 초기화하기 위해 .zshrc 파일에 다음 줄을 추가해 주세요:

```bash
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
```

마지막으로, 설치를 확인해봅시다:

```bash
$ sdk version
```

모든 것이 순조롭게 진행되었다면, 버전 번호를 확인할 수 있습니다:

```bash
SDKMAN!
script: 5.18.2
native: 0.4.6
```

## SDKMAN!을 사용한 자바 관리
SDKMAN!을 설치했으니, 이 도구를 사용하여 자바 버전을 관리하는 방법을 살펴보겠습니다.

### 사용 가능한 자바 버전 목록보기
사용 가능한 자바 버전을 보려면:

```bash
$ sdk list java
```

이 명령어는 우리가 선택할 수 있는 다양한 자바 버전을 보여줍니다.

### 특정 버전 설치하기
예를 들어, **`11.0.17-zulu`** 버전이 필요해서 설치하려면 아래와 같이 할 수 있습니다:

```bash
sdk install java 11.0.17-zulu
```

설치를 하면, 이 버전을 기본값으로 사용할지를 묻는데요. 'yes'를 선택하거나 Enter를 누르세요.

### 자바 버전 제거하기
더 이상 필요 없는 자바 버전을 제거하려면 아래 명령어로 삭제할 수 있습니다:

```bash
$ sdk uninstall java 11.0.17-zulu
```

### 설치된 버전 간 전환하기
필요한 자바 버전들을 여러개 설치했다면, 아래 명령어로 내가 지금 필요한 버전으로 손쉽게 전환할 수 있습니다
예를 들어 **`11.0.1-zulu`**로 전환하려면:

```bash
$ sdk use java 11.0.1-zulu
```

그리고 현재 적용된 자바 버전을 확인하려면:

```bash
$ sdk current
```

기본값으로 적용한 자바 버전을 변경하려면 **``default``** 명령어를 사용하세요:

```bash
$ sdk default java 11.0.1-zulu
```

## 버전 업그레이드하기
최신 자바 버전으로 업그레이드하려면:

```bash
$ sdk upgrade java
```

업그레이드 후, 현재 버전이 최신 버전인지 확인할 수 있습니다.

## 마무리
이로써 SDKMAN!을 사용한 자바 버전 관리에 대해 알아보았습니다. 이 도구를 사용하면 자바 버전을 쉽게 설치, 관리, 업그레이드할 수 있습니다. 개발을 하다보면 프로젝트나 앱 유지보수 환경에 따라 다양한 자바 버전을 사용할 필요가 있을텐데, 그런 경우에 유용한 정보가 되었으면 합니다. 즐거운 코딩 하세요! 💻 🖖