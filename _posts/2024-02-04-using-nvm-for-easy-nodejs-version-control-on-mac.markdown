---
layout: post
title:  "Mac에서 NVM을 사용한 쉬운 Node.js 버전 관리"
date:   2024-02-04 21:42:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-04-using-nvm-for-easy-nodejs-version-control-on-mac/01.png'
tags:   [nvm, node-js]
# tags_color: '#6b96df'
featured: false
---
Node.js로 작업하는 개발자라면 다양한 프로젝트에서 Node.js의 여러 버전을 관리하는게 필요할텐데요. 이럴때 Node Version Manager (NVM)을 사용하면 여러 버전의 Node.js를 쉽게 설치하고 관리할 수 있습니다. 이 글에서는 NVM의 기본 사항, 장점, 그리고 사용하는 방법에 대해 살펴보겠습니다. 이 포스트는 Mac OS 플랫폼을 기준으로 작성되었습니다.

## NVM이란?

NVM은 Node Version Manager의 약자로, 여러 버전의 Node.js 설치하고 관리할 수 있게 해주는 도구입니다. 이를 사용하면  Node.js 버전 간, 원활한 전환을 할 수 있고, 다양한 프로젝트에 대해 다른 버전의 Node.js를 사용할 수 있습니다. 각 Node.js 버전을 독립적으로 분리함으로써, NVM은 동일한 시스템에서 여러 버전을 충돌 없이 유지할 수 있게 해줍니다.

## NVM 사용의 이점

NVM을 사용하면 여러 가지 이점이 있습니다:

**1. 버전 관리의 용이성**: NVM을 사용하면 몇 가지 간단한 명령어로 다양한 Node.js 버전을 설치하고 전환할 수 있습니다. 이는 다른 Node.js 버전을 요구하는 여러 개발 프로젝트에서 작업할 때 특히 유용합니다.

**2. 프로젝트별 버전 설정**: **`.nvmrc`** 파일을 통해 각 프로젝트에 사용할 Node.js 버전을 지정할 수 있습니다. 이는 팀원들 사이의 개발 환경을 동기화하는 데 도움이 됩니다.

**3. 설치 및 업데이트 간소화**: NVM을 통한 Node.js 설치는 간단하며, 새로운 버전이 출시될 때마다 업데이트하는 것도 마찬가지로 쉽습니다.

## Mac OS에서 NVM 설치 및 사용하기

### 설치

Mac OS에서 NVM을 설치하는 것은 아주 간단한데요. zsh 터미널을 열고 다음을 입력하면 됩니다:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

이 명령어는 NVM 설치 스크립트를 다운로드하여 실행하게 됩니다. 설치 후, **`~/.zshrc`** 파일에 다음 환경 설정이 포함되어야 합니다:

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

### Node.js 버전 설치하기

NVM을 사용하여 특정 버전의 Node.js를 설치하는 방법을 알아보겠습니다. 예를 들어, Node.js 버전 14.17.0을 설치하려면 다음 명령어를 사용하세요:

```sh
nvm install 14.17.0
```

### 버전 목록 확인하고 전환하기 

설치되어있는 모든 Node.js 버전을 보려면 다음을 입력하세요:

```sh
nvm ls
```

특정 버전으로 전환하려면 다음과 같이 실행합니다:

```sh
nvm use 14.17.0
```

### 프로젝트별 Node.js 버전 설정하기

프로젝트 디렉토리에 **`.nvmrc`** 파일을 생성하고 원하는 Node.js 버전을 지정하세요. 예를 들어, 버전 **`14.17.0`**을 사용하려면 해당 버전 번호를 **`.nvmrc`** 파일에 작성하세요. 그런 다음 프로젝트 디렉토리에서 다음 명령어를 실행하면 자동으로 해당 버전으로 전환됩니다:

```sh
nvm use
```

프로젝트 환경이나 기타 이유로 인해 다양한 Node.js 버전을 관리해야 하는 경우가 자주 있습니다. 이 포스트가 그런 상황에서 도움이 되기를 바랍니다. NVM으로 Node.js 버전 관리가 더 효율적이고 쉽게 개선되기를 바라면서 다음 포스트에서 봐요! 🧑🏻‍💻