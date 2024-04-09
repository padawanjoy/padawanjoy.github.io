---
layout: post
title:  "개발자를 위한 iOS 탈옥 탐지하기"
date:   2024-02-13 15:16:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-13-guide-to-detecting-ios-jailbreaking-for-developers/01.png'
tags:   [ios, detecting, jailbreak]
tags_color: '#3f95ff'
featured: true
---
iOS 탈옥은 사용자가 시스템 수준에서 Apple의 엄격한 보안 제한을 우회하여 더 많은 제어권을 갖게 해줍니다. 그러나 이러한 자유는 금융, 의료, 기업과 같이 민감한 데이터를 다루는 앱에 보안 위험을 가져올 수 있죠. 따라서 개발자는 자신의 앱이 탈옥된 기기에서 실행되는 것을 감지하고 대응할 수 있는 방법을 알고 있어야 합니다. 이 문서는 탈옥 감지의 원리를 설명하고, 실제 구현 예시를 제공하며, 지속적인 업데이트의 중요성을 강조합니다.

## 탈옥 감지의 원리

탈옥 감지는 탈옥으로 인해 발생할 수 있는 여러 지표, 예를 들어 비정상적인 시스템 상태, 변경된 파일 시스템, 무단으로 실행되는 프로세스, 또는 수정된 시스템 라이브러리를 확인하는 과정을 포함합니다. 주로 사용되는 방법은 다음과 같습니다:

- **시스템 파일 접근:** 탈옥된 기기는 보통 시스템 파일에 대한 접근을 허용합니다. 앱이 특정 시스템 파일이나 디렉토리에 접근할 수 있다면, 그 기기가 탈옥됐을 가능성이 높습니다.
- **시스템 호출 수정:** 탈옥 과정에서는 앱의 동작을 변경하기 위해 시스템 호출을 수정하거나 가로챌 수 있습니다. 이러한 변경을 감지하는 것은 탈옥을 나타낼 수 있습니다.
- **앱 무결성 검사:** Apple의 앱 서명 메커니즘을 우회하는 것이 탈옥의 한 목표입니다. 앱 무결성의 침해를 확인하는 것도 기기가 탈옥되었는지를 판단하는 데 도움이 될 수 있습니다.

## 예제 코드

아래는 Swift로 작성된 기본적인 탈옥 감지 기법을 활용하여 iOS 기기가 탈옥되었는지 감지하는 코드 스니펫입니다.

```swift
import Foundation

func isJailbroken() -> Bool {
    #if TARGET_OS_SIMULATOR
    return false
    #else
    let fileManager = FileManager.default
    if fileManager.fileExists(atPath: "/Applications/Cydia.app") ||
        fileManager.fileExists(atPath: "/Library/MobileSubstrate/MobileSubstrate.dylib") ||
        fileManager.fileExists(atPath: "/bin/bash") ||
        fileManager.fileExists(atPath: "/usr/sbin/sshd") ||
        fileManager.fileExists(atPath: "/etc/apt") ||
        fileManager.fileExists(atPath: "/private/var/lib/apt/") ||
        UIApplication.shared.canOpenURL(URL(string:"cydia://package/com.example.package")!) {
        return true
    }
    // 시스템 파일에 쓰기 시도 (탈옥된 기기에서만 가능)
    let testPath = "/private/\(UUID().uuidString)"
    do {
        try "test".write(toFile: testPath, atomically: true, encoding: String.Encoding.utf8)
        try fileManager.removeItem(atPath: testPath)
        return true
    } catch {
        return false
    }
    #endif
}
```

이 코드는 탈옥 감지의 기본을 보여줍니다. 하지만 탈옥 커뮤니티는 보안 연구원들이 개발한 감지 방법을 우회하려는 지속적인 노력을 하고 있으므로, 이 코드로 모든 탈옥된 기기를 감지할 수는 없습니다.

## 지속적인 대응 및 업데이트의 중요성

새로운 탈옥 방법과 우회 기술이 계속해서 나타나기 때문에, 한 번의 탈옥 감지 로직 구현만으로는 충분하지 않습니다. 앱의 보안을 유지하기 위해서는 다음 사항을 고려해야 합니다:

- **업데이트 및 대응:** 새로운 탈옥 방법과 우회 기술에 대응하기 위해 앱을 정기적으로 업데이트하고, 보안 커뮤니티와 탈옥 커뮤니티 모두를 주시해야 합니다.
- **계층화된 보안 접근:** 탈옥 감지는 앱 보안의 한 층일 뿐입니다. 데이터 암호화, 안전한 통신, 서버 측 유효성 검사와 같은 다른 보안 조치를 함께 사용해야 합니다.

## 결론

iOS 탈옥 감지는 개발자가 사용자의 데이터를 보호하고 앱을 악의적인 활동으로부터 안전하게 지키는 데 중요한 역할을 합니다. 완벽한 탈옥 감지 방법은 없기때문에, 새로운 탈옥 방법과 우회 기술에 지속적으로 대응하는 것이 중요한데요. 여기 제시된 원리와 예제 코드를 앱의 보안을 강화하는 최소한의 조치라고 생각하고, 작게나마 도움이 되었으면 좋겠네요.