---
layout: post
title:  "여러 버전의 Xcode 동시에 사용하기"
date:   2024-02-10 09:58:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-10-using-various-versions-of-xcode/01.png'
tags:   [xcode]
tags_color: '#1e6ea0'
featured: true
---
오늘은 iOS 개발을 하시는 분들에게 도움이 될 만한 내용을 공유해보려고 합니다. 바로 여러 버전의 Xcode를 사용하는 방법인데요. 때로는 프로젝트의 요구 사항이나 특정 기능을 사용하기 위해 이전 버전의 Xcode를 사용해야 할 때가 있죠. 이 포스트가 그런 상황을 효과적으로 다루는데 도움이되지 않을까 합니다. 

### 1. Xcode 버전 다운로드 및 이름 변경

우선, 필요한 버전의 Xcode를 다운로드해야 합니다. 모든 버전의 Xcode는 Apple의 공식 개발자 페이지에서 찾아볼 수 있어요. 아래 링크를 통해 방문해 주세요.

- [Apple 개발자 다운로드](https://developer.apple.com/download/all/?q=xcode)

이곳에서 필요한 Xcode 버전을 검색해 다운로드할 수 있습니다. 예를 들어, Xcode 13이 필요하다면, 이 페이지에서 "Xcode 13"을 검색한 후 다운로드 버튼을 클릭하면 돼요.

![Apple 개발자 다운로드 페이지]({{site.baseurl}}/images/posts/2024-02-10-using-various-versions-of-xcode/02.png)
*Apple 개발자 다운로드 페이지*

다운로드한 후, 이전에 설치한 Xcode 버전을 덮어쓰지 않게 하고 쉽게 구별하기 위해서는 파일의 이름을 변경하는 것이 좋습니다. 예를 들어, 저는 버전 번호를 포함해서 파일 이름을 **`Xcode_13`**과 같이 변경했어요. 이 방법을 사용하면 같은 컴퓨터에서 여러 버전의 Xcode를 쉽게 관리할 수 있습니다. 다운로드한 Xcode 애플리케이션을 애플리케이션 폴더로 옮기기 전에 적절히 이름을 변경해 주세요.

### 2. 터미널 실행

다운로드하고 이름을 변경한 Xcode 버전을 가지고 있으면, 다음 단계는 터미널을 실행하는 것입니다. 터미널은 Mac에서 강력한 명령 실행 환경을 제공해요. Finder에서 "응용 프로그램" > "유틸리티" > "터미널"을 찾거나 Spotlight 검색을 사용해 빠르게 열 수 있습니다.

### 3. Xcode 실행 명령 입력

터미널을 열고, 다운로드한 Xcode 버전을 실행하기 위한 명령어를 입력해야 합니다. Xcode 13을 다운로드하고 **`Xcode_13.app`**으로 이름을 변경하고 애플리케이션 폴더에 넣었다고 가정하면, 터미널에 다음 명령어를 입력하세요:

```shell
/Applications/Xcode_13.app/Contents/MacOS/Xcode
```

이 명령어는 애플리케이션 폴더에서 **`Xcode_13.app`** 애플리케이션을 직접 실행합니다.

### 4. Xcode 사용 시작

명령어를 입력한 후, 지정된 버전의 Xcode가 실행됩니다. 처음 이 버전을 실행하는 경우, 추가 구성요소를 설치해야 할 수도 있어요. 이러한 구성요소를 설치하라는 메시지를 따라 설치를 완료하면, Xcode 사용을 시작할 수 있습니다.

!['추가 구성요소 설치 필요' 팝업 알림]({{site.baseurl}}/images/posts/2024-02-10-using-various-versions-of-xcode/03.png)
*'추가 구성요소 설치 필요' 팝업 알림*

## 이해를 돕기 위한 예제 코드

여러 버전의 Xcode를 관리하면서 특정 프로젝트에 대해 버전을 빠르게 전환하고 싶을 때, 터미널을 사용하는 것이 매우 편리합니다. 예를 들어, Xcode 12와 Xcode 13 사이를 자주 바꿔가며 사용해야 한다면, 각 버전에 대한 터미널 별칭을 설정할 수 있어요:

```shell
alias xcode13='/Applications/Xcode_13.app/Contents/MacOS/Xcode'
alias xcode12='/Applications/Xcode_12.app/Contents/MacOS/Xcode'
```

이러한 별칭을 설정하면 터미널에서 **`xcode13`** 또는 **`xcode12`**를 입력하기만 하면 각각의 Xcode 버전을 쉽게 실행할 수 있습니다. 이 방법은 개발 과정을 더욱 신속하고 효율적으로 만들어줍니다.

## 결론
여러 버전의 Xcode를 사용하는 방법을 알고 있으면, 프로젝트 요구 사항에 따라 개발 환경을 유연하게 조정할 수 있게 됩니다. 이 포스트가 개발하실때 도움이 되기를 바라며, 기술적인 질문이나 궁금증이 있다면 언제든지 댓글로 남겨주세요. 💻 🖖