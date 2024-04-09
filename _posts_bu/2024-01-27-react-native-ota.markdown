---
layout: post
title:  "React Native의 OTA 기능을 이용한 앱 업데이트"
date:   2024-01-27 22:53:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-27-react-native-ota/01.png'
tags:   [react-native, ota, code-push, expo, eas, firebase-app-distribution]
tags_color: '#6b96df'
featured: false
---
오늘은 React Native에서의 OTA(Over-the-Air) 업데이트 기능에 대해 살펴보려고 합니다. 이 글을 통해 OTA의 기초를 탐구하고, 마이크로소프트의 CodePush를 살펴보며, CodePush 외에 OTA 기능을 위해 사용할 수 있는 다른 도구들도 알아보겠습니다.

## OTA 업데이트란 무엇인가요?
일반적인/전통적인 업데이트 방법은 사용자가 업데이트 내용을 확인하고 버튼을 클릭해서 다운로드와 설치 과정을 거치는 것을 의미합니다. 이와 달리, OTA(Over-the-Air) 업데이트는 무선으로 사용자의 장치에 직접 업데이트를 배포하는 방법입니다. 사용자가 신경쓰거나 별도 조치를 하지 않아도 자동으로 업데이트되는 기술인 것이죠. 이 기능은 앱의 소규모 변경 사항이나 버그 수정을 빠르게 배포하는 데 특히 유용합니다. React Native의 영역에서는 마이크로소프트의 CodePush가 이러한 OTA 업데이트를 구현하는 데 자주 사용되는 도구입니다.

## CodePush와 OTA 업데이트 탐색하기
### 1. CodePush란 무엇인가요?
* CodePush는 마이크로소프트가 제공하는 React Native 및 Cordova 애플리케이션을 위한 클라우드 서비스로, 개발자가 모바일 앱을 업데이트할 수 있게 합니다.
* 사용자는 앱을 다시 설치하거나 스토어 업데이트를 기다리지 않고도 최신 JavaScript 번들과 에셋을 받을 수 있습니다.

![CodePush 기능을 포함한 마이크로소프트의 앱 센터]({{site.baseurl}}/images/posts/2024-01-27-react-native-ota/02.png)
*CodePush 기능을 포함한 마이크로소프트의 앱 센터*

### 2. 작동 방식
* 애플리케이션은 시작할 때 CodePush 서버에서 업데이트 사항이 있는지 확인합니다.
* 업데이트가 있다면 새로운 JavaScript 번들과 에셋이 다운로드되어 애플리케이션에 적용됩니다.
* 사용자는 앱을 사용할 때 업데이트된 내용이 적용된 서비스를 바로 사용할 수 있습니다.

### 3. 장점
* 빠른 버그 수정과 기능 업데이트가 가능합니다.
* 앱 스토어 심사 프로세스를 거치지 않고 배포가 가능합니다.
* 사용자가 항상 최신 버전을 사용하도록 할 수 있습니다.

### 4. 고려 사항
* OTA 업데이트는 네이티브 코드에 영향을 주지 않으므로 네이티브 코드 변경이 포함된 업데이트는 여전히 전통적인 방법의 앱 스토어 배포가 필요합니다.
* 일부 앱 스토어는 OTA 업데이트를 허용하지 않을 수 있으므로 정책을 확인하고 적용하는 것이 필요합니다.

## 다른 OTA 업데이트 도구 탐색하기
Microsoft의 CodePush 외에도 React Native에서 OTA 업데이트 기능을 구현하기 위한 여러 대안 도구들이 있습니다. 몇 가지를 간략히 살펴보겠습니다:

### 1. Expo Updates
* React Native 애플리케이션 개발을 위한 프레임워크인 Expo는 자체 OTA 업데이트 기능을 제공합니다.
* Expo를 사용하는 앱은 Expo Updates API를 통해 자바스크립트 코드와 에셋을 업데이트할 수 있습니다.
* Expo 프로젝트가 아닌 순수 React Native 프로젝트에서도 사용할 수 있습니다.

### 2. React Native Auto Updater
* 이 라이브러리는 React Native 앱에 자동 업데이트 기능을 제공합니다.
* GitHub이나 다른 서버에서 앱 업데이트를 호스팅할 수 있습니다.
* 오랜 시간 유지보스가 안되고 있는 라이브러리이기 때문에 사용에 주의가 필요합니다.

### 3. EAS (Expo Application Services)
* EAS는 Expo 외부에서 더 많은 맞춤화가 필요한 애플리케이션을 위해 설계되었습니다.
* Expo 프로젝트의 빌드, 배포, 업데이트 관리를 지원합니다.
* EAS에 Expo Updates 기능이 포함되어 있습니다.

### 4. Firebase App Distribution
* Google 플랫폼인 Firebase는 앱 업데이트를 테스트 사용자에게 신속하게 배포할 수 있는 App Distribution 서비스를 제공합니다.
* 주로 베타 테스팅에 사용되며, 실제 앱 스토어 업데이트를 대체하지는 않습니다.

## 마무리
React Native 앱 개발에서 OTA 업데이트는 큰 편의성을 제공하는 기능입니다. 업데이트를 신속하게 배포하여 앱 품질을 유지하고 사용자 경험을 향상시키는 데 도움이 됩니다. 위에서 언급된 다양한 도구들 중에서 앱과 운영 환경에 가장 잘 맞는 것을 선택하는 것이 중요합니다. 이 글이 여러분의 앱 개발에 도움이 되기를 바랍니다! 🚕 💻