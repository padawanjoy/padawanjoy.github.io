---
layout: post
title:  "JavaScript의 Scope에 대해 이해하기"
date:   2024-02-05 16:40:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-05-understanding-scope-in-javascript/01.png'
tags:   [javascript, scope]
tags_color: '#db9e00'
featured: true
---
프로그래밍 언어에서 Scope는 변수, 함수, 그리고 다른 식별자들이 접근 가능한 범위를 의미합니다. JavaScript에서 Scope는 코드 전반에서 변수를 어떻게 그리고 어디에서 참조하고 접근할 수 있는지를 결정하는데요. 이 글에서는 JavaScript의 Scope 복잡성을 설명하고, 전역 Scope, 지역 Scope, 함수 Scope, 블록 Scope 등 다양한 유형에 대해 예시 코드와 함께 알아보겠습니다.

## 전역 Scope

전역 Scope에서 선언된 변수는 코드 어디에서나 접근할 수 있습니다. 이 변수들은 전체 스크립트에서 유효하며 함수 내부에서도 접근할 수 있습니다.

```javascript
var globalVar = 'This is a global variable';

function checkScope() {
  console.log(globalVar); // Outputs: 'This is a global variable'
}

checkScope();
console.log(globalVar); // Outputs: 'This is a global variable'
```

다만 전역 Scope의 변수는 같은 이름을 가지는 변수가 프로그램 내의 다른 곳에서 선언될 경우 예상치 못한 충돌을 발생시킬 수가 있기 때문에 이를 피하기 위해 최소한으로 사용하는 것이 좋습니다.

## 지역 Scope

지역 Scope는 특정 섹션 내에서만 유효한 변수를 의미합니다. 예를 들어, 함수 내부에서 선언된 변수들이 있습니다. 이 변수들은 함수 외부에서는 접근할 수 없습니다.

```javascript
function showLocalScope() {
  var localVar = 'This is a local variable';
  console.log(localVar); // Outputs: 'This is a local variable'
}

showLocalScope();
// console.log(localVar); // ReferenceError: localVar is not defined 오류 발생
```

지역 변수는 선언된 함수 내에서만 접근할 수 있으며, 함수 실행이 끝나면 변수의 생명도 사라집니다.

JavaScript에서 흔히 언급되는 지역 Scope에는 함수 Scope와 블록 Scope가 있는데요. 이 예시들을 더 깊이 들여다봅시다.

### 함수 Scope

JavaScript에서 함수 Scope는 함수 내부에서 선언된 변수가 해당 함수 내에서만 접근 가능함을 의미합니다. 아래 예시에서 **`var`** 키워드로 선언된 변수는 함수 Scope를 가집니다.

```javascript
function functionScopeExample() {
  var functionScoped = 'Variable within function scope';
  console.log(functionScoped); // Outputs: 'Variable within function scope'
}

functionScopeExample();
// console.log(functionScoped); // ReferenceError: functionScoped is not defined 오류 발생
```

함수 Scope는 필요한 곳에서만 변수에 접근할 수 있도록 제한하기 때문에 코드를 더 안전하고 관리하기 쉽게 만듭니다.

### 블록 Scope

ES6와 함께 도입된 **`let`**과 **`const`**는 블록 Scope를 제공합니다. 이는 조건문, 루프 등 **`{}`**로 둘러싸인 모든 블록 내에서 선언된 변수가 해당 블록 내에서만 접근 가능함을 의미합니다.

```javascript
function blockScopeExample() {
  if (true) {
    let blockScoped = 'Variable within block scope';
    console.log(blockScoped); // Outputs: 'Variable within block scope'
  }

  // console.log(blockScoped); // ReferenceError: blockScoped is not defined 오류 발생
}

blockScopeExample();
```

블록 Scope를 사용하면 변수가 유효한 곳을 더 세밀하게 제어할 수 있어, 프로그램의 복잡성을 줄이고 오류를 방지할 수 있습니다.

## Scope 체인

JavaScript에서 함수가 중첩될 때, 내부 함수는 외부 함수의 변수에 접근할 수 있습니다. 이는 Scope 체인 때문입니다. 내부 함수의 Scope 내에서 변수를 찾을 수 없는 경우, JavaScript는 외부 Scope에서 변수를 찾아나가고 그래도 없으면 그 상위의 외부 Scope에서 변수를 찾고.. 이렇게 마치 체인처럼 Scope를 확장하며 찾아나가기 때문에 Scope 체인이라고 합니다. 이렇게 찾는 과정은 전역 Scope까지 계속됩니다.

```javascript
var outerVar = 'Outer variable';

function outerFunction() {
  var innerVar = 'Inner variable';

  function innerFunction() {
    console.log(outerVar); // Outputs: 'Outer variable'
    console.log(innerVar); // Outputs: 'Inner variable'
  }

  innerFunction();
}

outerFunction();
```

Scope 체인은 변수를 검색하기 위해 외부 Scope로 순차적으로 이동하는 메커니즘을 제공하며, 코드의 가독성과 유지보수성을 향상시키는 데 중요한 역할을 합니다.

## 결론

JavaScript에서 Scope를 이해하는 것은 변수의 가시성과 수명을 관리하는 데 필수적입니다. Scope의 적절한 사용은 코드 충돌을 방지하고 프로그램의 구조를 개선하며 오류를 줄이는 데 도움이 됩니다. JavaScript 코딩을 하며 Scope를 이해하고 적용하는 데 도움이 되기를 바랍니다.