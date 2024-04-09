---
layout: post
title:  "JavaScript에서 변수 선언하기: var vs. let, const"
date:   2024-02-07 09:01:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-07-declaring-variables-in-javascript-var-vs-let-const/01.png'
tags:   [javascript, var, let, const]
tags_color: '#db9e00'
featured: true
---
자바스크립트는 지속적으로 발전하고 있으며, 이 발전은 언어의 기본적인 부분, 특히 변수 선언과 같은 중요한 부분에도 영향을 미칩니다. 이번 블로그 포스팅에서는 자바스크립트에서 **`var`**, **`let`**, **`const`**를 사용하는 방법과 각각의 장단점, 그리고 어떤 상황에서 사용하는 것이 가장 적절한지에 대해 알아보겠습니다.

## JavaScript에서 변수 선언하기

자바스크립트에서는 크게 세 가지 방법으로 변수를 선언할 수 있습니다: **`var`**, **`let`**, **`const`**. 이 세 가지 방법은 비슷해 보일 수 있지만, 각각 독특한 특성을 가지고 있습니다.

### var

**`var`**는 자바스크립트의 초기 버전부터 사용되어 온 변수 선언 방식으로, 함수 레벨 스코프를 가집니다. 이는 **`var`**로 선언된 변수가 해당 변수가 선언된 함수 내에서만 유효하다는 의미입니다. 스코프(Scope)에 대한 더 자세한 설명은 [여기](https://padawanjoy.com/blog/understanding-scope-in-javascript)에서 확인하실 수 있습니다.

그러나 **`var`**는 몇 가지 단점이 있습니다. 예를 들어, 같은 스코프 내에서 변수를 중복 선언해도 아무런 오류가 발생하지 않는데, 이는 실수로 변수 값을 덮어쓸 수 있으며, 이로 인해 코드의 복잡성이 증가하고 예기치 않은 동작을 야기할 수 있습니다.

```javascript
var x = 5;
var x = 10;
console.log(x); // 10
```

또한 **`var`**로 선언된 변수는 호이스팅되어 선언 전에도 접근할 수 있으나, 이는 때때로 혼란을 야기할 수 있습니다. (호이스팅에 대한 자세한 설명은 [이 글](https://padawanjoy.com/blog/understanding-hoisting-in-javascript)을 참고하세요.)

```javascript
console.log(y); // undefined, 하지만 접근은 가능
var y = 5;
console.log(y); // 5
```

### let

**`let`**은 ES6 (ES2015)에서 도입되어, 블록 스코프 변수를 선언하는 데 사용됩니다. **`let`**으로 선언된 변수는 해당 변수가 선언된 블록 내에서만 유효합니다. 이는 코드의 이해와 관리를 용이하게 합니다.

```javascript
if (true) {
  let z = 5;
}
console.log(z); // ReferenceError: z is not defined
```

**`let`**은 **`var`**의 일부 문제를 해결합니다. 예를 들어, 같은 스코프 내에서 **`let`**으로 선언된 동일한 변수를 다시 선언하려고 하면 오류가 발생합니다.

```javascript
let a = 5;
let a = 10; // SyntaxError: Identifier 'a' has already been declared
```

### const

**`const`** 역시 ES6에서 소개되었으며, **`let`**과 같이 블록 스코프를 가집니다. 다만, **`const`**로 선언된 변수는 재할당이 불가능합니다. 이는 상수 값을 선언하는 데 사용됩니다. **`const`**로 선언된 변수는 선언과 동시에 초기화되어야 합니다.

```javascript
const b = 5;
b = 10; // TypeError: Assignment to constant variable.
```

## let과 const를 사용하는 이유

**`let`**과 **`const`**는 **`var`**의 단점을 극복하고, 코드를 더 안정적이고 예측 가능하게 만들어주는 현대적인 변수 선언 방법을 제공합니다. **`let`**은 변수의 사용 범위를 명확하게 제한하여 코드의 가독성과 유지보수성을 향상시킵니다. **`const`**는 초기에 할당된 값을 변경할 수 없게 함으로써, 의도치 않은 변수 값의 변경을 방지하고 코드의 안정성을 높여줍니다.

## 예시

이제 **`var`**, **`let`**, **`const`**를 사용한 간단한 예시를 살펴보겠습니다:

```javascript
// var 사용 예시
var name = 'Padawan Joy';
for (var i = 0; i < 5; i++) {
  console.log(name); // 'Padawan Joy'가 5번 출력됩니다.
}
console.log(i); // 5, for 루프 밖에서도 i가 접근 가능합니다.

// let 사용 예시
let age = 30;
for (let j = 0; j < 5; j++) {
  console.log(age); // 30이 5번 출력됩니다.
}
console.log(j); // ReferenceError: j is not defined, j는 for 루프 밖에서 접근 불가능합니다.

// const 사용 예시
const tool = 'Xcode';
console.log(tool); // 'Xcode'
tool = 'Android Studio'; // TypeError: Assignment to constant variable, const로 선언된 변수는 재할당 불가능합니다.
```

이 예시들은 **`var`**, **`let`**, **`const`**의 기본 사용 방법과 그 차이점을 명확하게 보여줍니다. 이러한 차이점을 이해하고 상황에 맞게 적절한 변수 선언 방법을 선택하는 것이 중요합니다.

## 결론

자바스크립트에서 **`var`**, **`let`**, **`const`**는 각각의 사용 사례와 장단점을 가지고 있습니다. 개발자로서 이러한 차이점을 이해하고, 각 상황에 가장 적합한 변수 선언 키워드를 선택하는 것이 중요한데요. 코드의 안정성, 가독성, 그리고 유지보수성을 향상시키고자 한다면, **`let`**과 **`const`**의 사용을 선호하는 것이 좋겠습니다. 그럼, 즐거운 코딩 되세요! 😊