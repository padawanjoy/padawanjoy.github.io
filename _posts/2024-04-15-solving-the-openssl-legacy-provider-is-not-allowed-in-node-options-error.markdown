---
layout: post
title:  "--openssl-legacy-provider is not allowed in NODE_OPTIONS 오류 해결하기"
date:   2024-04-15 09:38:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-15-solving-the-openssl-legacy-provider-is-not-allowed-in-node-options-error/01.webp'
tags:   [node-js, openssl-legacy-provider, open-ssl-error, node-options, error]
tags_color: '#538747'
featured: true
---
Node.js 개발 환경에서 가끔 발생하는 오류 **`--openssl-legacy-provider is not allowed in NODE_OPTIONS.`**가 있습니다. 이 오류의 원인은 무엇인지, 그리고 어떻게 해결하면 되는지 알아보겠습니다. 

## 목차
- [오류 원인](#오류-원인)
- [--openssl-legacy-provider 옵션에 대해](#openssl-legacy-provider-옵션에-대해)
- [해결 방법](#해결-방법)
  - [방법 1. NODE_OPTIONS 환경 변수 수정](#방법-1-node_options-환경-변수-수정)
  - [방법 2. 프로그램 실행 시 명령 옵션 설정](#방법-2-프로그램-실행-시-명령-옵션-설정)
- [마무리](#마무리)

<br>
## 오류 원인
이 오류는 Node.js 환경에서 특정 옵션이 NODE_OPTIONS라는 환경 변수에 설정되어있을 때 발생할 수 있습니다. NODE_OPTIONS는 Node.js 어플리케이션 실행 시 Node.js 런타임에 전달할 수 있는 추가적인 옵션을 설정할 수 있는 환경 변수입니다. 이 변수를 사용하면 스크립트 실행 시 명령어에 직접 옵션을 작성하지 않아도 다양한 런타임 구성을 할 수 있습니다.

**`--openssl-legacy-provider is not allowed in NODE_OPTIONS.`** 오류 메시지는 **`--openssl-legacy-provider 옵션이 NODE_OPTIONS에서 지원되지 않는다.`**라는 의미인데요. **`--openssl-legacy-provider`** 옵션을 **`NODE_OPTIONS`** 환경 변수를 통해 설정하려고 했는데, 이를 지원하지 않아서 오류가 발생한 것이죠.

## --openssl-legacy-provider 옵션에 대해
**`--openssl-legacy-provider`** 옵션은 Node.js에서 OpenSSL의 레거시 공급자를 활성화시킨다는 옵션인데요. 말이 어려운데, 하나씩 알아볼게요. 먼저, OpenSSL은 암호화 라이브러리로 웹 통신의 보안을 담당하는 SSL/TLS 프로토콜을 구현합니다. 이 라이브러리는 다양한 암호화 알고리즘과 프로토콜을 제공하는데요. OpenSSL의 레거시 공급자를 활성화하는 **`--openssl-legacy-provider`** 옵션은 쉽게 말해서 OpenSSL에서 제공하는 오래된 구식의 암호화 기능들을 사용할 수 있게 만드는 설정을 의미합니다. 최신 버전의 OpenSSL 라이브러리에서는 기본적으로 사용되지 않거나 권장되지 않는 예전 암호화 방식도 사용할 수 있게 해달라는 설정인 것이죠.

## 해결 방법

### 방법 1. NODE_OPTIONS 환경 변수 수정
이 문제를 해결하는 가장 간단한 방법은 **`NODE_OPTIONS`** 환경 변수에서 **`--openssl-legacy-provider`** 옵션을 제거하는 것입니다. 터미널에서 다음 명령어를 실행하면 됩니다. 

```sh
unset NODE_OPTIONS
```

이 명령어는 **`NODE_OPTIONS`** 환경 변수를 초기화하여 Node.js가 기본 설정으로 작동하도록 해줍니다. 이 방법은 간단하고 빠르지만, NODE_OPTIONS에 다른 중요한 설정이 있었다면 그 설정들도 함께 사라진다는 단점이 있습니다. 

### 방법 2. 프로그램 실행 시 명령 옵션 설정
**`NODE_OPTIONS`** 환경 변수에 적용된 다른 설정들을 유지하면서, 상황상 **`--openssl-legacy-provider`** 옵션 설정도 적용이 필요하다면 두 번째 방법이 해답이 될 수 있습니다. **`NODE_OPTIONS`** 환경 변수에 **`--openssl-legacy-provider`** 옵션을 설정해서 실행하는 것이 보안상 문제가 되어 오류가 발생하는 것이니, 환경 변수가 아닌 다른 방법으로 **`--openssl-legacy-provider`** 옵션을 사용하는 것이죠. 또, 우리가 직접 **`NODE_OPTIONS`** 환경 변수에 **`--openssl-legacy-provider`** 옵션을 설정한게 아니라 우리가 사용하는 프레임워크에서 설정이 되어있는 경우, 우리가 맘대로 이를 수정하는게 쉽지 않을 수 있는데 이때도 이 두번째 방법이 도움이 될 수 있습니다. 

두 번째 방법은 바로 프로그램을 실행하는 명령어에 아래와 같이 직접 **`--openssl-legacy-provider`** 옵션을 추가해서 실행을 하는 것 입니다.

```sh
node --openssl-legacy-provider your-app.js
```

이 방법은 Node.js 프로세스가 시작될 때 **`--openssl-legacy-provider`** 옵션을 적용하며, **`NODE_OPTIONS`** 환경 변수의 제한을 우회하도록 해줍니다.

## 마무리
"**`--openssl-legacy-provider is not allowed in NODE_OPTIONS`**" 오류는 Node.js 환경에서 OpenSSL 호환성 문제로 인해 발생합니다. 위에서 이야기한 방법들이 이 문제를 겪는 분들에게 도움이 되기를 바랍니다.🧩😀