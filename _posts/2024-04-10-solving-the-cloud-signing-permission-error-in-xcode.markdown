---
layout: post
title:  Cloud Signing Permission 오류 해결하기
date:   2024-04-10 22:32:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-10-solving-the-cloud-signing-permission-error-in-xcode/01.webp'
tags:   [apple, ios, xcode, error, dev]
tags_color: '#3f95ff'
featured: true
---
Xcode를 이용해서 개발을 하다보면 'Cloud Signing Permission 오류'가 발생할 때가 있습니다. 이 오류는 주로 Xcode에서 앱을 빌드하거나 아카이브할 때, 또는 앱 심사를 위한 바이너리를 업로드하는 과정에서 발생하는데요. 이 오류를 해결하는 방법을 한번 살펴보도록 하겠습니다.

## 목차
- [오류 메시지와 원인](#오류-메시지와-원인)
- [해결 방법 1](#해결-방법-1)
- [해결 방법 2](#해결-방법-2)
- [마무리](#마무리)

<br>
## 오류 메시지와 원인
'Cloud Signing Permission 오류'의 메시지는 다음 이미지와 같습니다. 

![Cloud signing permission 오류]({{site.baseurl}}/images/posts/2024-04-10-solving-the-cloud-signing-permission-error-in-xcode/02.webp)
*Cloud signing permission 오류*

클라우드 관리 배포 인증서에 대한 액세스 권한이 없으니, 멤버십 계정 담당자 또는 관리자에게 해당 권한을 요청해야한다는 내용의 메시지인데요. 참여하고 있는 Apple Developer Program에서 Account Holder 또는 Admin 권한을 가지고 있다면 해당 오류는 발생되지 않습니다. 그러나 현재 Xcode에 설정된 계정이 일반 개발자 권한의 계정이라면 이와 같은 문제가 발생할 수 있습니다.

## 해결 방법 1
가장 확실하면서 간단한 해결 방법은 Apple Developer Program의 계정 소유자나 관리자에게 관리자 권한을 요청하는 것 입니다. 앱 관리 이상의 권한을 소유하고 있다면 [Users and Access 페이지](https://appstoreconnect.apple.com/access/developers)에서 각 계정별로 부여된 권한을 확인하고 제한적으로나마 권한을 수정할 수도 있습니다. 그러나 모든 개발자에게 관리자 권한을 부여하는 것은 옳은 접근법이 아니겠죠. 외부 개발자와 일하는 경우도 있을테고요.

## 해결 방법 2
또 다른 해결 방법은 오류 메시지에서 직접적으로 언급되고 있는 클라우드 관리 배포 인증서에 대한 액세스 권한을 부여하는 것 입니다. [Users and Access 페이지](https://appstoreconnect.apple.com/access/developers)에서 문제가 되고 있는 본인의 계정을 선택해 볼까요? Access to Cloud Managed Distribution Certificate 옵션이 체크되어있지 않은 것을 확인할 수 있습니다. 

!['Access to Cloud Managed Distribution Certificate' 옵션]({{site.baseurl}}/images/posts/2024-04-10-solving-the-cloud-signing-permission-error-in-xcode/03.webp)
*'Access to Cloud Managed Distribution Certificate' 옵션*

Access to Cloud Managed Distribution Certificate 옵션을 체크해주면 오류를 해결할 수 있습니다. 

## 마무리
요약하자면, Cloud signing permission 오류를 해결하기 위한 해결책은 다음과 같습니다.

- **방법 1**: Apple Developer Program의 관리자 권한을 얻습니다.
- **방법 2**: Users and Access page에서 'Access to Cloud Managed Distribution Certificate' 옵션을 활성화 합니다.

간단히 해결할 수 있는 오류이지만, 갑자기 이런 오류가 발생하면 난감하죠. 오류 해결하실 때 도움이 이 포스트가 도움이 되었으면 좋겠네요.🖖