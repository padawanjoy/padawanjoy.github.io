---
layout: post
title:  "Chrome에서 다크 모드와 라이트 모드 쉽게 테스트하기"
date:   2024-04-21 15:39:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-21-easily-test-dark-mode-and-light-mode-in-chrome/01.webp'
tags:   [dark-mode, light-mode, chrome]
tags_color: '#ff9600'
featured: true
---
오늘날 웹사이트나 하이브리드 모바일 앱 개발 시 사용자의 눈 보호와 배터리 소모 감소 등 사용자 편의성을 최우선으로 고려하는 것이 아주 중요해졌는데요. 이런 이유로 '다크 모드'는 개발자나 기획자가 고려해야할 중요 기능이 되었습니다. 개발을 하면서 '다크 모드'와 '라이트 모드'를 확인할 때 Google Chrome을 사용하면 굉장히 편리해서 이에 대해 소개해 보겠습니다.

## 목차
- [다크 모드의 중요성과 추세](#다크-모드의-중요성과-추세)
- [Chrome으로 다크 모드/라이트 모드 테스트하기](#chrome으로-다크-모드라이트-모드-테스트하기)
    - [Chrome으로 확인하는 방법](#chrome으로-확인하는-방법)
- [마무리](#마무리)

<br>
## 다크 모드의 중요성과 추세
다크 모드는 배경을 어둡게 하여 텍스트와 인터페이스 요소가 돋보이게 하는 디자인 테마입니다. 눈의 피로를 줄이고, 저조도 환경에서 가독성을 향상시키며, OLED 또는 AMOLED 디스플레이를 사용하는 기기에서 배터리 소모를 줄일 수 있어서 많은 이점이 있죠. macOS, Windows, iOS, Android와 같은 주요 운영 체제들에서는 이제 '다크 모드'를 기본적으로 지원하고 있습니다. 운영 체제들 뿐만 아니라 Instagram, Facebook, YouTube 등 개별 서비스들도 사용자가 설정할 수 있도록 다크 모드 기능을 옵션으로 제공하고 있죠.

## Chrome으로 다크 모드/라이트 모드 테스트하기
운영/개발하는 서비스에 '다크 모드' 기능을 지원하는지 여부는 사용자의 첫 인상에 큰 영향을 줄 수 있습니다. 많은 서비스들에게 '다크 모드' 기능을 지원하고 있는데, 내가 만든 서비스에서는 제공하지 않는다면 뭔가 부족해 보이고, 신경 쓰지 않는다는 느낌을 줄 수 있겠죠? 

이렇게 중요해진 '다크 모드' 기능을 개발하기는 해야할텐데, 이를 위해 개발에 사용하는 노트북, 디바이스 등의 설정을 매번 바꿔가며 확인하는 것은 여간 번거로운 일이 아닐겁니다. 그런데 Chrome을 사용하면 기기 설정을 매번 바꾸지 않아도 손 쉽게 '다크 모드'와 '라이트 모드' 전환이 가능해서 편리한데요. Chrome 개발자 도구를 이용하면 됩니다.

### Chrome으로 확인하는 방법
1. Google Chrome을 열고 개발/운영하는 웹사이트 또는 하이브리드 모바일 앱을 열어줍니다.
2. 오른쪽 상단의 세 점 메뉴를 클릭하고 [More tools] > [Developer tools]를 선택하거나 **`Ctrl+Shift+I (Windows)`** 또는 **`Cmd+Opt+I (Mac)`** 단축키를 사용하여 개발자 도구를 엽니다.
![[More tools] > [Developer tools]]({{site.baseurl}}/images/posts/2024-04-21-easily-test-dark-mode-and-light-mode-in-chrome/02.webp)
*오른쪽 상단의 세 점 메뉴를 클릭하고 [More tools] > [Developer tools]를 선택합니다.*
3. 개발자 도구 탭에서 [Rendering]을 선택합니다. (보이지 않는 경우 아래 이미지와 같이 [More tools] 에서 [Rendering]을 찾습니다.)
4. Rendering 탭에서 페이지 렌더링과 관련된 다양한 옵션을 볼 수 있습니다. **`[Emulate CSS media feature prefers-color-scheme]`** 옵션을 찾습니다.
5. 이 옵션을 클릭하면 '**`no emulation`**', '**`prefers-color-scheme: light`**', '**`prefers-color-scheme: dark`**' 중에서 선택할 수 있습니다. 다크 모드가 적용되는지 확인하려면 '**`prefers-color-scheme: dark`**'를 선택합니다.
![prefers-color-scheme Options]({{site.baseurl}}/images/posts/2024-04-21-easily-test-dark-mode-and-light-mode-in-chrome/03.webp)
*prefers-color-scheme 옵션*
6. 선택한 옵션에 따라 웹사이트 또는 하이브리드 모바일 앱 화면은 즉시 다크 모드 또는 라이트 모드로 전환됩니다. 이를 통해 개발 중인 애플리케이션의 스타일이 사용자의 시스템 설정에 따라 올바르게 적용되는지를 실시간으로, 손 쉽게 확인할 수 있습니다.

## 마무리
웹 및 앱 개발자로서 사용자 경험을 최우선으로 하는 것은 매우 중요합니다. 다크 모드와 라이트 모드를 제대로 지원하는 것은 사용자 친화적인 인터페이스 디자인의 기본이 되었는데요. Chrome 개발자 도구를 사용하여 다크 모드와 라이트 모드를 테스트하는 방법으로 보다 효율적인 개발/운영을 해봅시다!😀