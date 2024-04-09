---
layout: post
title:  "모던 JavaScript (ES6+) 기능 탐구 (1): 새로운 문법과 향상된 기능"
date:   2024-03-17 23:47:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-17-exploring-modern-javascript-es6-features-1-new-syntax-and-enhanced-functionality/01.webp'
tags:   [javascript, js-dev-course, es6, template-literals, arrow-functions, destructuring-assignment, default-parameters]
tags_color: '#db9e00'
featured: true
---
JavaScript가 ES6(ES2015) 이후로 지속적으로 발전하면서, 개발자들이 코드를 작성하는 방식에 혁신을 가져온 많은 새로운 기능과 문법이 도입되었습니다. 이번 글에서는 모던 JavaScript의 이러한 기능들을 살펴보고, 이것들이 우리의 코딩 스타일과 효율성에 어떤 변화를 가져다주는지 이야기해보겠습니다.

## 목차
1. [**`let`**과 **`const`**](#let과-const)
2. [템플릿 리터럴](#템플릿-리터럴)
3. [화살표 함수](#화살표-함수)
4. [구조 분해 할당](#구조-분해-할당)
5. [기본 매개변수](#기본-매개변수)
6. [결론 및 다음 포스트 미리보기](#결론-및-다음-포스트-미리보기)

## **`let`**과 **`const`**
**`var`**의 한계를 극복하기 위해, ES6에서는 블록 스코프를 갖는 **`let`**과 **`const`**가 소개되었습니다. **`let`**은 값의 재할당이 가능한 변수를 선언할 때, **`const`**는 한 번 할당하면 값이 변경되지 않는 상수를 선언할 때 사용됩니다.

```javascript
let name = "Padawan";
name = "Joy"; // 가능

const pi = 3.14;
pi = 3.14159; // TypeError 발생
```

## 템플릿 리터럴
템플릿 리터럴은 변수나 표현식을 문자열 안에 쉽게 삽입할 수 있는 방법을 제공합니다. 백틱(``)을 사용하면, 보다 읽기 쉽고 간결한 방식으로 문자열을 구성할 수 있습니다.

```javascript
let name = "Padawan Joy";
let greeting = `Hello, ${name}!`;
console.log(greeting); // "Hello, Padawan Joy!"
```

## 화살표 함수
화살표 함수는 함수 선언을 더 간결하게 할 수 있는 문법을 제공합니다. 화살표 함수는 전통적인 함수와 다른 **`this`** 바인딩을 가지며, 정의된 바깥쪽 컨텍스트의 **`this`** 값을 유지합니다.

```javascript
const add = (a, b) => a + b;
console.log(add(5, 3)); // 8
```

## 구조 분해 할당
구조 분해 할당을 사용하면, 배열이나 객체에서 값을 또는 속성을 개별 변수로 쉽게 추출할 수 있습니다. 이는 코드의 가독성을 향상시키고, 할당 과정을 단순화합니다.

```javascript
const person = {name: "Padawan Joy", age: 30};
const {name, age} = person;
console.log(name); // "Padawan Joy"
console.log(age); // 30
```

## 기본 매개변수
기본 매개변수를 사용하면, 함수의 매개변수를 기본값으로 초기화할 수 있습니다. 값이 전달되지 않거나 undefined가 전달된 경우, 기본값이 사용됩니다.

```javascript
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}

console.log(greet("Padawan Joy")); // "Hello, Padawan Joy!"
console.log(greet()); // "Hello, Guest!"
```

## 결론 및 다음 포스트 미리보기
이 글에서는 모던 JavaScript가 도입한 몇 가지 새로운 문법과 기능들을 탐구했습니다. 이 기능들은 우리의 코드를 더욱 간결하고 효율적으로 만들어 줍니다. 다음 글인 '모던 JavaScript (ES6+) 기능 탐구 (2): 실용적인 ES6+ 예제를 통한 학습'에서는 이러한 JavaScript 기능들을 실제 예제를 통해 더욱 심층적으로 살펴 볼 예정입니다. 모던 JavaScript로 코딩 능력을 한층 업그레이드하는 데 도움이 되었으면 좋겠습니다.