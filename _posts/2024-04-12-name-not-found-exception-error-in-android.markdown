---
layout: post
title:  "Android의 PackageManager NameNotFoundException 오류 해결하기"
date:   2024-04-12 08:42:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-12-name-not-found-exception-error-in-android/01.webp'
tags:   [android, google, error, dev, package-manager-name-not-found-exception]
tags_color: '#a1c648'
featured: true
---
최근 기존에 개발했었던 Android 앱의 **`targetSdkVersion`**을 높이니 **`android.content.pm.PackageManager$NameNotFoundException`**라는 오류가 발생했습니다. 이렇게 개발 환경, 프로젝트 환경을 최신화하다보면 생각하지 못했던 오류가 발생하기도 하는데요. 이 오류는 왜 발생하는 것인지, 어떻게 해결하면 되는지 한번 알아보겠습니다. 

## 목차
- [오류 원인](#오류-원인)
- [해결 방법](#해결-방법)
- [마무리](#마무리)

<br>
## 오류 원인
기존에 잘 동작하던 Android 앱에서 제가 수정한건 **`targetSdkVersion`** 뿐이었습니다. **`targetSdkVersion`**를 수정하니 다음과 같은 오류 메시지가 발생했죠.

![android.content.pm.PackageManager$NameNotFoundException]({{site.baseurl}}/images/posts/2024-04-12-name-not-found-exception-error-in-android/02.webp)
*android.content.pm.PackageManager$NameNotFoundException*

오류 메시지를 살펴보면, **`PackageManager`**와 관련된 오류라는 것을 알 수 있습니다. 이 오류는 **`PackageManager`**를 사용하여 다른 앱에 대한 정보를 검색하려고 할 때 발생할 수 있는데요.

이 오류의 원인은 Android 11에서 **`"패키지 공개 상태"`**에 대한 변경이 있었기 때문입니다. Android 11 이상을 타겟팅하는 앱은 더 이상 기기에 설치된 다른 앱 목록을 바로 알 수 없도록 바뀌었습니다. 그런데 **`PackageManager`**를 사용해서 다른 앱의 정보를 조회하려고 하니까 오류가 발생했던 것이죠.

## 해결 방법
그럼 Android 11 이상을 타겟팅하는 경우에는 다른 앱의 정보를 조회할 수 없는 것 일까요? 더 이상 **`PackageManager`**를 사용할 수 없는 것 일까요? 그렇지 않습니다. Android 11 이상을 타겟팅하는 경우에도 다른 앱의 정보를 **`PackageManager`**를 사용해서 조회할 수 있습니다.

다만, 정보를 조회할 다른 앱에 대한 정보를 매니페스트 파일에 명시적으로 선언을 해둬야 하는 방식으로 변경이 된 것 뿐입니다. 아무 앱의 정보나 조회하는 것이 아니라, 사전에 미리 정의해둔 앱에 대해서만 조회할 수 있도록 한 것이죠. 일종의 보안성을 높이기 위한 변화라고 볼 수 있겠네요. 

iOS 개발도 하시는 분들이라면 비슷한 정책을 iOS에서 보셨을텐데요. iOS에서 다른 앱의 설치 여부 판단을 하려면 plist 파일의 Queried URL Schemes에 다른 앱의 URL Scheme 값을 미리 등록해둬야 하는 것과 비슷하죠. 

이런 변경으로 인해 Android 11 이상을 타겟팅하는 앱은 다음과 같은 API를 사용할 경우 **`android.content.pm.PackageManager$NameNotFoundException`**라는 오류가 발생할 수 있습니다. 

* **PackageManager.getPackageInfo()**
* **PackageManager.getInstalledPackages()**
* **PackageManager.queryIntentActivities()**
* **PackageManager.getInstalledApplications()**
* **bindService()**

그럼, 수정하는 방법을 확인해 봅시다.

개발하는 앱의 targetSdkVersion이 안드로이드 11 이상이라면, **`AndroidManifest.xml`** 파일에 **`<queries>`** 요소를 추가해서 쿼리할 패키지 이름 또는 인텐트 필터 서명을 추가해줘야 합니다. 

1. **패키지 이름 지정하기:** **`<queries>`** 내부에 **`<package>`** 태그를 사용하여 쿼리할 특정 패키지를 나열합니다.

```xml
<manifest package="com.padawanjoy.example">
    <queries>
        <package android:name="com.otherapp.example" />
    </queries>
    ...
</manifest>
```

2. **인텐트 필터 지정하기:** **`<queries>`** 내부에 **`<intent>`** 태그를 포함시켜 쿼리하고자 하는 인텐트 필터를 추가합니다.

```xml
<manifest package="com.padawanjoy.example">
    <queries>
        <intent>
            <action android:name="android.intent.action.SEND" />
            <data android:mimeType="image/jpeg" />
        </intent>
    </queries>
    ...
</manifest>
```

'이렇게 앱을 특정해서 조회하는건 번거로운데, 예전처럼 제한없이 다른 앱의 정보를 조회하는 방법은 없는건가요?'하고 궁금해하실 수도 있을텐데요. 모든 앱에 대한 정보를 쿼리해야 하는 경우에 **`QUERY_ALL_PACKAGES`** 권한을 사용하면 제한없이 조회가 가능합니다. 하지만 이 권한을 사용하면 Google Play에 앱을 업로드할 때 더 엄격한 심사 과정을 거쳐야 할 수 있니, 반드시 필요한 경우가 아니라면 사용하지 않는 것이 좋겠습니다. 

## 마무리
정리해보자면, **`android.content.pm.PackageManager$NameNotFoundException`**라는 오류는 Android 11 이상이 타겟팅일때 다른 앱의 정보를 조회하는 정책이 변경되어 발생하는 것이고, 오류 해결을 위해서는 조회할 다른 앱을 **`AndroidManifest.xml`**에 미리 정의해야 합니다.

* Android 11 이상을 타겟팅하는 경우 **`AndroidManifest.xml`**에 **`<queries>`** 요소를 추가하고,
* **`<queries>`** 요소에 패키지 이름이나 인텐트 필터를 지정합니다.
* 반드시 필요한 경우에만 **`QUERY_ALL_PACKAGES`** 권한을 사용합니다.

이렇게 요약할 수 있겠네요. 갑자기 잘 돌아가던 앱에서 **`PackageManager$NameNotFoundException`**라는 오류가 발생했을 때 도움이 되기를 바라며 글 마치겠습니다. 😎