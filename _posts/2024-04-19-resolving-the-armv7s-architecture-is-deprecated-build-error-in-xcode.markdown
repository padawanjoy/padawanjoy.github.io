---
layout: post
title: "Xcode의 armv7s architecture is deprecated 빌드 오류 해결하기"
date:   2024-04-19 16:48:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-19-resolving-the-armv7s-architecture-is-deprecated-build-error-in-xcode/00.webp'
tags: [apple, ios, xcode, error, dev, armv7s]
tags_color: '#3f95ff'
featured: true
---
Xcode에서 빌드하는 프로젝트를 오랜 기간 운영하다보면 **`'armv7s architecture is deprecated'`** 오류가 발생할 때가 있습니다. 이 오류는 왜 발생하는 것인지, 어떻게 해결하면 되는지 이야기해보겠습니다.

## 목차
- [오류 현상 및 원인](#오류-현상-및-원인)
- [오류 해결하기](#오류-해결하기)
    - [('Architectures' 섹션에서) armv7s 아키텍처 제거](#architectures-섹션에서-armv7s-아키텍처-제거)
    - [(다른 섹션에서) armv7s 아키텍처 제거](#다른-섹션에서-armv7s-아키텍처-제거)
- [armv7s 제거에 대한 걱정](#armv7s-제거에-대한-걱정)
    - [기기 지원 범위](#기기-지원-범위)
    - [iOS 지원 범위](#ios-지원-범위)
    - [앱 스토어 요구사항](#앱-스토어-요구사항)
-[마무리](#마무리)

<br>
## 오류 현상 및 원인 
iOS 앱, 또는 Mac OS 앱을 Xcode를 이용해서 개발하고 빌드를 하다보면 다음과 같은 오류가 발생하기도 합니다. 

![armv7s architecture is deprecated 오류]({{site.baseurl}}/images/posts/2024-04-19-resolving-the-armv7s-architecture-is-deprecated-build-error-in-xcode/01.webp)
*armv7s architecture is deprecated 오류*

오류 메시지는 **`"The armv7s architecture is deprecated. You should update your ARCHS build setting to remove the armv7s architecture."`** 입니다. 이 오류가 발생된 이유는 뭘까요?

앱을 개발하고 오랜 시간 유지보수를 하며 운영하다 보면, 그 사이 Xcode도 업그레이드 되고, 구동되는 아이폰과 같은 기기의 새로운 출시도 있고.. 많은 변화가 생기기 마련입니다. 해당 오류는 프로젝트 코드는 오래되었는데 구동 환경과 개발 환경이 달라지며 발생되는 여러 오류 중 하나인데요.

오류 메시지는 armv7s 아키텍처가 더 이상 사용되지 않으므로 빌드 설정에서 이 아키텍처를 제거하라는 것을 알려주고 있습니다. armv7s는 이전 iPhone 모델에서 사용되던 아키텍처로, 최신 iOS 개발에서는 더 이상 필요하지 않습니다.

## 오류 해결하기 
오류를 해결하는 방법은 오류 메시지의 안내를 따르면 됩니다. armv7s 아키텍처를 빌드 설정에서 제거하면 되는 것이죠.

### ('Architectures' 섹션에서) armv7s 아키텍처 제거
1. Xcode를 열고 해당 프로젝트를 불러옵니다.
2. 프로젝트 네비게이터에서 프로젝트 파일을 선택한 다음, 상단의 'Build Settings' 탭을 클릭합니다.
3. 'Build Settings' 탭에서 'Architectures' 섹션을 찾습니다. 이 섹션에서 'Architectures' 설정 값에 armv7s가 있는지 확인합니다.
!['Build Settings' > 'Architectures' > 'Architectures'에 있는 armv7s 값]({{site.baseurl}}/images/posts/2024-04-19-resolving-the-armv7s-architecture-is-deprecated-build-error-in-xcode/02.webp)
*'Build Settings' > 'Architectures' > 'Architectures'에 있는 armv7s 값*
4. 해당 항목에서 armv7s 값을 제거합니다. (other를 클릭하면 편집할 수 있습니다.)
5. 'Product' -> 'Clean Build Folder'를 선택하여 프로젝트를 깨끗이 정리한 후, 다시 빌드해서 오류가 수정되었는지 확인합니다.

### (다른 섹션에서) armv7s 아키텍처 제거
위의 방법대로 'Build Settings' > 'Architectures' > 'Architectures'를 확인해봤지만 armv7s 값이 없을 수도 있습니다. 그럼 왜 armv7s 값이 없는데도 **`'armv7s architecture is deprecated'`** 오류가 발생한 것일까요? 다른 곳에서 armv7s 사용이 설정되어있기 때문입니다. 

1. Xcode 'Build Settings' 검색창에서 armv7s를 검색해봅니다.
2. 'Architectures'가 아닌 다른 섹션에서 armv7s 값이 설정된 것을 확인할 수 있습니다. (저같은 경우는 'User-Defined' 섹션에서 사용되었습니다.)
!['User-Defined'에 있는 armv7s 값]({{site.baseurl}}/images/posts/2024-04-19-resolving-the-armv7s-architecture-is-deprecated-build-error-in-xcode/02.webp)
*'User-Defined'에 있는 armv7s 값*
3. armv7s 값을 제거합니다.
4. 'Product' -> 'Clean Build Folder'를 선택하여 프로젝트를 깨끗이 정리한 후, 다시 빌드해서 오류가 수정되었는지 확인합니다.

## armv7s 제거에 대한 걱정
armv7s를 제거하면 오래된 구형 기기를 지원하지 못하는 것은 아닌지 걱정될 수 있습니다. 이렇게 armv7s 아키텍처를 제거하는 결정은 지원하려는 기기와 iOS 버전에 따라 달라질 수 있는데요. 하지만 현대의 앱 개발 환경에서는 대부분의 경우 armv7s 아키텍처를 포함할 필요가 없습니다. 그 이유를 살펴보겠습니다. 

### 기기 지원 범위
armv7s 아키텍처는 주로 iPhone 5와 iPhone 5C와 같은 구형 기기에 사용되었던 아키텍처입니다. 2012년~2013년에 출시된 아주 오래된 기기이죠. 이 기기들은 현재 iOS 애플리케이션의 요구 사항을 충족하지 못할 만큼 오래되었으며, 최신 iOS 버전을 실행할 수 없습니다.

### iOS 지원 범위
최신 iOS 버전은 armv7s 아키텍처를 사용하는 기기들을 지원하지 않습니다. 예를 들어, iOS 11 이상은 iPhone 5s 이상의 모델에서만 작동하는데, iPhone 5s부터는 arm64 아키텍처가 사용되었습니다.

### 앱 스토어 요구사항
애플은 앱 스토어에 제출되는 서비스에 대해 arm64 아키텍처를 지원하도록 요구하고 있습니다. 이는 앱이 최신 기기에서 원활하게 작동하도록 보장하는 데 도움이 되기 때문이며, 개발자들로 하여금 armv7s보다는 성능을 최적화할 수 있고 최신 기능도 활용할 수 있는 arm64 아키텍처에 집중을 유도하는 것이기도 합니다. 

## 마무리
Xcode에서 발생하는  **`'armv7s architecture is deprecated'`** 오류에 대해 원인은 무엇이고 어떻게 수정하면 되는지를 알아봤습니다. armv7s를 제거하면 iPhone 5 및 iPhone 5C와 같은 오래된 기기에서는 앱을 실행할 수 없게 될 수 있습니다. 하지만 이러한 기기들은 이미 대부분 시장에서 사용이 감소하고 있으며, 최신 기능 및 보안 업데이트를 지원받지 못하는 상태입니다. 사용성이 미미한 기기를 지원하기 위해 armv7s를 계속 유지하는 것 보다는, armv7s를 제거함으로써 최신 기기와 iOS 버전에 초점을 맞춰 성능과 보안을 고려하는 것이 옳은게 아닐까 생각합니다.