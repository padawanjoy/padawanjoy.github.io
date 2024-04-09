---
layout: post
title:  "함수의 기초: JavaScript에서 함수 정의하기 및 호출하기"
date:   2024-03-07 10:48:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-07-the-basics-of-functions-defining-and-calling-functions-in-javascript/01.webp'
tags:   [javascript, js-dev-course, function]
tags_color: '#db9e00'
featured: true
---
JavaScript에 대해 살펴볼 때, 정말 중요하고 필수적인 부분이 바로 '함수'에 대한 이해입니다. 함수는 JavaScript에서 코드 재사용을 가능하게 하고 프로그램을 더 체계적으로 만드는 근본적인 구성 요소입니다. 이 글에서는 함수의 기본 개념, 함수 정의 방법, 그리고 함수 호출 방법에 대해 살펴볼 것입니다.

## 목차
1. [함수란 무엇인가?](#함수란-무엇인가)
2. [함수 정의하기](#함수-정의하기)
3. [함수 호출하기](#함수-호출하기)
4. [매개변수와 인자](#매개변수와-인자)
5. [실습: 간단한 함수 만들기](#실습-간단한-함수-만들기)
6. [결론 및 다음 포스트 예고](#결론-및-다음-포스트-예고)

## 함수란 무엇인가?
함수는 특정 작업을 수행하도록 지정된 코드의 묶음입니다. 한 번 작성되면 여러 번 재사용될 수 있어 코드 중복을 줄입니다.

## 함수 정의하기
JavaScript에서 함수를 정의하는 방법은 여러 가지가 있지만, 가장 기본적인 형태는 다음과 같습니다:

```javascript
function sayHello() {
  console.log("Hello!");
}
```

이 코드에서 **`sayHello`**는 함수의 이름이며, 중괄호 안의 코드는 함수가 호출될 때 실행됩니다.

## 함수 호출하기
함수를 정의한 후, 그 이름에 **`()`**를 추가하여 호출할 수 있습니다. 예를 들어:

```javascript
sayHello();  // "Hello!"를 출력합니다.
```

## 매개변수와 인자
함수는 매개변수를 통해 입력값을 받아들일 수 있어, 함수의 유연성을 높여줍니다:

```javascript
function sayHello(name) {
  console.log("Hello, " + name + "!");
}

sayHello("John");  // "Hello, John!"을 출력합니다.
```

## 실습: 간단한 함수 만들기
두 숫자를 받아 그 합을 반환하는 함수를 작성해 보세요:

```javascript
function add(num1, num2) {
  return num1 + num2;
}

console.log(add(5, 3));  // 8을 출력합니다.
```

## 결론 및 다음 포스트 예고
JavaScript에서 함수를 정의하고 호출하는 방법에 대해 배웠습니다. 프로그래밍에서 중요한 역할을 하는 함수를 이해하는 것은 매우 중요합니다. 다음 포스트에서는 '스코프와 클로저: JavaScript의 변수 스코프와 클로저 이해하기'로 더 깊이있는 내용을 다뤄보겠습니다. 더 고급 주제로 넘어가기 전에 지금까지 알아봤던 기본 사항들을 한번 더 살펴봐도 좋을 것 같습니다.