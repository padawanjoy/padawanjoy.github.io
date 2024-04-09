---
layout: post
title:  "Android 앱 개발에서 PackageManager$ NameNotFoundException 오류 해결하기"
date:   2024-01-25 17:10:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-25-name-not-found-exception-error-in-android/01.jpg'
tags:   [android, google, error, dev]
tags_color: '#a1c648'
featured: true
---
Android 앱 개발을 하다보면 **`android.content.pm.PackageManager$NameNotFoundException`** 오류를 겪게되는 경우가 있습니다. 이 오류는 PackageManager를 사용하여 다른 앱에 대한 정보를 검색하려고 할 때 발생할 수 있는데요. 해당 오류가 왜 발생하는지와 해결 방법을 알아보겠습니다.

![android.content.pm.PackageManager$NameNotFoundException]({{site.baseurl}}/images/posts/2024-01-25-name-not-found-exception-error-in-android/02.png)
*android.content.pm.PackageManager$NameNotFoundException*

이 오류의 주요 원인은 Android 11에서 "패키지 공개 상태"에 대한 변경이 있었기 때문입니다. Android 11 이상을 타겟팅하는 앱은 더 이상 기기에 설치된 다른 앱 목록을 바로 알 수 없도록 바뀌었습니다. 대신, 매니페스트 파일에 명시적으로 선언된 앱에 대한 정보에만 접근할 수 있습니다. 마치 iOS에서 다른 앱의 설치 여부를 판단하려면 plist 파일의 Queried URL Schemes에 다른 앱의 URL Scheme 값을 포함해야만 하는 것과 비슷하다고 볼 수 있죠.

이 변경으로 인해 Android 11 이상을 타겟팅하는 앱은 다음과 같은 API를 사용할 경우 문제를 겪을 수 있습니다:

* **PackageManager.getPackageInfo()**
* **PackageManager.getInstalledPackages()**
* **PackageManager.queryIntentActivities()**
* **PackageManager.getInstalledApplications()**
* **bindService()**

개발하는 앱의 targetSdkVersion이 안드로이드 11 이상이라면, **`AndroidManifest.xml`** 파일에 **`<queries>`** 요소를 추가해서 쿼리할 패키지 이름 또는 인텐트 필터 서명을 포함해야 합니다.

패키지 이름과 인텐트 필터를 지정하는 방법은 다음과 같습니다:

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

모든 앱에 대한 정보를 쿼리해야 하는 경우에 **`QUERY_ALL_PACKAGES`** 권한을 사용할 수도 있는데요. 하지만 이 권한을 사용하면 Google Play에 앱을 업로드할 때 더 엄격한 심사 과정을 거쳐야 할 수 있으므로, 반드시 필요한 경우가 아니라면 사용하지 않는 것이 좋습니다.

정리해보자면, 이 오류를 해결하기 위해서는:

* Android 11 이상을 타겟팅하는 경우 **`AndroidManifest.xml`**에 **`<queries>`** 요소를 추가합니다.
* **`<queries>`** 요소에 패키지 이름이나 인텐트 필터를 지정합니다.
* 반드시 필요한 경우에만 **`QUERY_ALL_PACKAGES`** 권한을 사용합니다.

이 글이 Android 앱 개발 중에 **`PackageManager$NameNotFoundException`** 오류를 만났을 때, 도움이 되기를 바랍니다.