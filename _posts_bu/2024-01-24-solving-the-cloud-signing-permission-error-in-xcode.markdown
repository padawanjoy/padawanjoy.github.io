---
layout: post
title:  Xcode에서 Cloud Signing Permission 오류 해결하기
date:   2024-01-24 10:11:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-24-solving-the-cloud-signing-permission-error-in-xcode/01.png'
tags:   [apple, ios, xcode, error, dev]
tags_color: '#3f95ff'
featured: true
---
안녕하세요, Apple 개발자 여러분! Xcode에서 앱을 개발할 때 가끔 머리 아픈 문제들을 만나곤 합니다. 그 중 하나가 'Cloud Signing Permission 오류'입니다. 이 글에서는 이 오류를 해결하기 위한 쉽고 명확한 단계를 안내해 드리겠습니다.

첫째, 이 오류는 주로 Xcode에서 앱을 빌드하거나 아카이브할 때, 또는 앱 심사를 위한 바이너리 업로드 과정에서 발생합니다. 오류 메시지는 다음과 같습니다:

![Cloud signing permission 오류]({{site.baseurl}}/images/posts/2024-01-24-solving-the-cloud-signing-permission-error-in-xcode/02.png)
*Cloud signing permission 오류*

오류 메시지 내용은 클라우드 관리 배포 인증서에 대한 액세스 권한을 부여받지 못했기 때문에 멤버쉽 계정 주인 또는 관리자에게 해당 권한을 요청해야한다는 내용인데요. 참여하고 있는 Apple Developer Program에서 Account Holder 또는 Admin 권한을 가지고 있다면 발생되지 않는 문제이지만, 일반 개발자 권한으로 등록되어있다면 이런 문제가 발생할 수 있습니다. 이 문제는 아래 방법들로 해결할 수 있습니다. 

첫 번째 가장 확실하면서 간단한 해결책은 계정 소유자나 관리자에게 관리자 권한을 요청하는 것입니다. [Users and Access page](https://appstoreconnect.apple.com/access/developers)에서 부여된 권한을 확인하고 수정할 수 있습니다.

그러나 모든 개발자에게 관리자 권한을 부여하는게 옮은 것은 아니겠죠. 외부 개발자와 일하는 경우도 있을테고요. 그런 경우에는 [Users and Access page](https://appstoreconnect.apple.com/access/developers)에서 본인 계정을 선택하고, Access to Cloud Managed Distribution Certificate 옵션을 활성화하면 오류를 해결할 수 있습니다.

!['Access to Cloud Managed Distribution Certificate' 옵션]({{site.baseurl}}/images/posts/2024-01-24-solving-the-cloud-signing-permission-error-in-xcode/03.png)
*'Access to Cloud Managed Distribution Certificate' 옵션*

요약하자면, 클라우드 서명 권한 오류를 해결하기 위한 해결책은 다음과 같습니다:

- 방법 1: Apple Developer Program의 관리자 권한을 얻습니다.
- 방법 2: Users and Access page에서 'Access to Cloud Managed Distribution Certificate' 옵션을 활성화 합니다.

이 글이 여러분의 개발 작업에 도움이 되기를 바랍니다.🖖