---
layout: post
title:  "개발자를 위한 안드로이드 루팅 탐지하기"
date:   2024-02-14 08:53:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-14-guide-to-detecting-android-rooting-for-developers/01.png'
tags:   [android, detecting, rooting]
tags_color: '#a1c648'
featured: true
---
[지난 번 iOS 탈옥 감지에 대한 글](https://padawanjoy.com/blog/guide-to-detecting-ios-jailbreaking-for-developers)에 이어, 이번에는 안드로이드 기기에서 루팅을 탐지하는 방법에 대해 자세히 알아보겠습니다. 루팅은 사용자에게 안드로이드 기기의 운영 체제에 더 깊은 접근을 제공하지만, 보안 위험도 함께 동반합니다. 앱 개발자로서, 사용자의 보안을 보장하기 위해 루팅된 기기를 탐지하고 대응하는 것이 중요합니다.

## 루팅이란?

루팅은 제조업체나 네트워크 운영자가 설정한 제한을 우회하여 안드로이드 기기에서 더 깊은 시스템 접근을 허용하는 과정입니다. 이를 통해 더 많은 사용자 정의 옵션과 일반적으로 접근할 수 없는 앱을 설치할 수 있게 됩니다.

## 루팅 탐지 원리

루팅된 기기를 탐지하는 것은 기본적으로 기기가 표준 안드로이드 환경에서 벗어났는지 여부를 확인하는 것을 포함합니다. 이를 위해 여러 방법이 사용될 수 있으며, 그 중에는:

- **시스템 파일 및 디렉토리 접근:** 루팅된 기기는 보통 **`/system`** 폴더에 접근할 수 있습니다. 앱이 이러한 폴더에 접근할 수 있다면, 기기가 루팅되었을 가능성이 높습니다.
- **SU(SuperUser) 바이너리 검사:** 대부분의 루팅 과정은 'su' 바이너리를 설치합니다. 이 바이너리의 존재 여부를 확인하는 것은 기기가 루팅되었는지 결정하는 실용적인 방법입니다.
- **시스템 속성 검사:** 특정 시스템 속성 값은 루팅된 기기에서만 변경될 수 있습니다. 이러한 값들을 검사하는 것은 루팅을 감지하는 데 도움이 될 수 있습니다.

## 예제 코드

루팅을 탐지하는 간단한 Java 코드 스니펫은 다음과 같습니다:

```java
public boolean isRooted() {
    return checkSUExistence() || checkSystemProperties();
}

private boolean checkSUExistence() {
    String[] suPaths = {
        "/system/bin/su", "/system/xbin/su", "/su/bin/", "/sbin/su",
        "/data/local/xbin/su", "/data/local/bin/su", "/system/sd/xbin/su",
        "/system/bin/failsafe/su", "/data/local/su"
    };
    for (String path : suPaths) {
        if (new File(path).exists()) return true;
    }
    return false;
}

private boolean checkSystemProperties() {
    try {
        Process process = Runtime.getRuntime().exec(new String[] { "/system/bin/getprop", "ro.secure" });
        BufferedReader bufferedReader = new BufferedReader(
                new InputStreamReader(process.getInputStream()));
        String line = bufferedReader.readLine();
        if (line.equals("0")) return true;
    } catch (IOException e) {
        // 예외 처리
    }
    return false;
}
```

이 코드는 SU 바이너리와 시스템 속성의 존재 여부를 확인하여 기기가 루팅되었는지 여부를 결정합니다.

## 지속적인 대응 및 업데이트의 중요성

새로운 루팅 방법이 지속적으로 등장하기 때문에, 한 번의 탐지 로직으로는 모든 경우를 커버할 수 없습니다. 새로운 루팅 기술에 대응하기 위해서는 앱을 정기적으로 업데이트하고, 보안 커뮤니티와의 소통을 유지하는 것이 중요합니다. 이를 통해 앱과 사용자 데이터의 보안을 강화할 수 있습니다.

## 결론

안드로이드 앱 개발에서 루팅 탐지는 사용자의 보안을 보장하고 악의적인 활동으로부터 앱을 보호하는 데 중요한 역할을 합니다. 본 포스트가 안드로이드 앱 개발과 보안에 관심 있는 모든 분들에게 유익한 정보를 제공했기를 바랍니다.