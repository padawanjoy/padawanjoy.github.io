---
layout: post
title:  "Chrome에서 다크 모드와 라이트 모드 쉽게 테스트하기"
date:   2024-02-23 12:55:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/01.webp'
tags:   [dark-mode, light-mode, chrome]
# tags_color: '#844eae'
featured: true
---
오늘날 웹사이트나 하이브리드 모바일 앱 개발 시 사용자의 눈 보호와 배터리 소모 감소 등 사용자 편의성을 최우선으로 고려하는 것이 아주 중요해졌는데요. 이런 이유로 '다크 모드'는 개발자에게 필수 기능이 되었습니다. 사용자가 자신의 선호에 따라 인터페이스를 쉽게 전환할 수 있는 기능을 제공하는 것이 개발자들의 필수 고려 사항이 되었는데요. 이 글에서 Google Chrome을 사용하여 웹사이트나 앱의 다크 모드와 라이트 모드를 쉽게 테스트하는 방법을 단계별로 알아보겠습니다.

## 다크 모드의 중요성과 추세

다크 모드는 배경을 어둡게 하여 텍스트와 인터페이스 요소가 돋보이게 하는 디자인 테마입니다. 눈의 피로를 줄이고, 저조도 환경에서 가독성을 향상시키며, OLED 또는 AMOLED 디스플레이를 사용하는 기기에서 배터리 소모를 줄일 수 있습니다. macOS, Android, Windows와 같은 주요 운영 체제에서 기본적으로 이 기능을 지원합니다. Facebook, YouTube, Twitter 등 대형 서비스들도 사용자 선호에 따라 다크 모드 옵션을 제공합니다.

## Chrome으로 다크 모드/라이트 모드 테스트하기

Chrome 개발자 도구는 웹사이트가 다크 모드를 지원하는지 쉽게 테스트할 수 있는 방법을 제공합니다.

1. Google Chrome을 열고 테스트하려는 웹사이트로 이동합니다.

2. 오른쪽 상단의 세 점 메뉴를 클릭하고 [More tools] > [Developer tools]를 선택하거나 **`Ctrl+Shift+I (Windows)`** 또는 **`Cmd+Opt+I (Mac)`** 단축키를 사용하여 개발자 도구를 엽니다.
<br>
![[More tools] > [Developer tools]]({{site.baseurl}}/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/02.webp)
*오른쪽 상단의 세 점 메뉴를 클릭하고 [More tools] > [Developer tools]를 선택합니다.*

3. 개발자 도구 탭에서 [Rendering]을 선택합니다. (보이지 않는 경우 아래 이미지와 같이 [More tools] 에서 [Rendering]을 찾습니다.)

4. Rendering 탭에서 페이지 렌더링과 관련된 다양한 옵션을 볼 수 있습니다. [Emulate CSS media feature prefers-color-scheme] 옵션을 찾습니다.

5. 이 옵션을 클릭하면 '**`no emulation`**', '**`prefers-color-scheme: light`**', '**`prefers-color-scheme: dark`**' 중에서 선택할 수 있습니다. 다크 모드가 적용되는지 확인하려면 '**`prefers-color-scheme: dark`**'를 선택합니다.
<br>
![prefers-color-scheme Options]({{site.baseurl}}/images/posts/2024-02-23-easily-test-dark-mode-and-light-mode-in-chrome/03.webp)
*prefers-color-scheme 옵션*

6. 선택한 옵션에 따라 웹사이트는 즉시 다크 모드 또는 라이트 모드로 전환됩니다. 이를 통해 개발 중인 웹사이트의 스타일이 사용자의 시스템 설정에 따라 올바르게 적용되는지 실시간으로 확인할 수 있습니다.

## 결론

웹 및 앱 개발자로서 사용자 경험을 최우선으로 하는 것은 매우 중요합니다. 다크 모드와 라이트 모드를 제대로 지원하는 것은 사용자 친화적인 인터페이스 디자인의 기본입니다. Chrome 개발자 도구를 사용하여 다크 모드와 라이트 모드를 테스트하는 방법으로 효과적인 개발이 되길 바랍니다.