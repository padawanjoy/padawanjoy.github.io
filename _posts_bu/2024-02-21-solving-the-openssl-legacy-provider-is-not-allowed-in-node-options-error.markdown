---
layout: post
title:  Node.js 환경에서 "--openssl-legacy-provider is not allowed in NODE_OPTIONS" 오류 해결하기
date:   2024-02-21 13:54:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-21-solving-the-openssl-legacy-provider-is-not-allowed-in-node-options-error/01.webp'
tags:   [node-js, open-ssl-error, node-options, error]
# tags_color: '#e76797'
featured: true
---
Node.js 개발 과정에서 가끔 이해하기 어려운 오류 메시지를 만나는 경우가 있습니다. 그 중 하나가 "**`--openssl-legacy-provider is not allowed in NODE_OPTIONS.`**" 라는 오류입니다. 이 글을 통해 이 오류의 원인과 몇 가지 해결책을 소개하려 합니다.

## 왜 발생하나요?

이 오류는 특정 옵션이 NODE_OPTIONS 환경 변수에 설정되었을 때 Node.js 환경에서 발생합니다. NODE_OPTIONS는 Node.js 프로세스 시작 시 추가 옵션을 포함할 수 있는 환경 변수입니다. "**`--openssl-legacy-provider`**" 옵션은 레거시 OpenSSL 암호화 알고리즘의 사용을 가능하게 하는데, 보안상의 이유로 허용되지 않는 경우에 이 오류를 유발합니다.

근본적인 원인은 Node.js와 OpenSSL 사이의 호환성 문제입니다. OpenSSL은 Node.js에서 널리 사용되는 보안 통신을 위한 라이브러리입니다. 최신 버전의 Node.js는 OpenSSL의 최신 기능과 알고리즘을 활용하여 보안을 강화합니다. 따라서 레거시 OpenSSL 알고리즘을 사용하도록 설정된 시스템에서는 Node.js가 이를 보안 위험으로 간주하고 오류를 발생시킵니다.

## 해결책 1: NODE_OPTIONS 환경 변수 수정

이 문제를 해결하는 가장 간단한 방법은 환경 변수에서 해당 설정을 제거하는 것입니다. 터미널에서 다음 명령을 실행해보세요:

```sh
unset NODE_OPTIONS
```

이 명령은 **`NODE_OPTIONS`** 환경 변수를 초기화하여 Node.js가 기본 설정으로 작동하도록 합니다. 이 방법은 간단하고 빠르지만, NODE_OPTIONS에 다른 중요한 설정이 있었다면 그 설정들도 함께 사라집니다.

### 장점

- 적용이 간편하고 빠릅니다.
- 복잡한 설정 변경 없이 오류 해결이 가능합니다.

### 단점

- **`NODE_OPTIONS`**에 있던 다른 중요한 옵션들도 제거됩니다.

## 해결책 2: Node.js 버전 업데이트

현재 사용 중인 Node.js 버전이 오래되었다면, 최신 버전으로 업데이트하는 것을 고려해보세요. 최신 버전의 Node.js는 최신 OpenSSL 알고리즘과 호환되며, "**`--openssl-legacy-provider`**" 옵션 없이도 잘 작동합니다.

```sh
nvm install node # nvm을 사용하는 경우
```
(nvm에 대한 자세한 정보는 [이 글](https://padawanjoy.com/blog/using-nvm-for-easy-nodejs-version-control-on-mac)을 참고하세요.)

### 장점

- 최신 보안 업데이트와 기능에 접근 가능합니다.
- 향후 비슷한 호환성 문제를 방지합니다.

### 단점

- 기존 프로젝트와의 호환성 문제가 발생할 수 있습니다.
- 업데이트 과정에서 다른 의존성 문제가 발생할 수 있습니다.

## 해결책 3: 코드에서 레거시 OpenSSL 사용 허용

특정 레거시 OpenSSL 알고리즘 사용이 명시적으로 요구되는 프로젝트인 경우, 코드 내에서 이를 허용하는 설정을 할 수 있습니다. 주로 Node.js 애플리케이션에서 **`crypto`** 모듈을 사용할 때 적용됩니다.

```javascript
const crypto = require('crypto');

crypto.setFips(0); // FIPS 모드 비활성화
// 필요한 암호화 작업 수행
```

### 장점

- 프로젝트의 특정 요구 사항을 충족합니다.
- 전역 환경 변수를 변경하지 않고 문제를 해결합니다.

### 단점

- 코드를 변경해야 합니다.
- 잠재적인 보안 우려로 인해 권장되지 않습니다.

## 결론

"**`--openssl-legacy-provider is not allowed in NODE_OPTIONS`**" 오류는 Node.js 환경에서 OpenSSL 호환성 문제로 인해 발생합니다. 위에서 제공된 해결책을 통해 문제를 해결할 수 있으며, 프로젝트에 가장 적합한 방법을 선택하세요. 이러한 문제를 방지하기 위해 Node.js와 OpenSSL을 가능한 최신 상태로 유지하는 것이 좋습니다.