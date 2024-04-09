---
layout: post
title:  "스코프와 클로저: JavaScript에서 변수 스코프와 클로저 이해하기"
date:   2024-03-08 09:36:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-08-scope-and-closures-understanding-variable-scope-and-closures-in-javascript/01.webp'
tags:   [javascript, js-dev-course, scope, closures]
tags_color: '#db9e00'
featured: true
---
이번에는 '스코프와 클로저'에 대해 알아보겠습니다. 이 개념들은 JavaScript의 내부 동작을 이해하는 데 중요하며, 변수가 어떻게 동작하는지에 큰 영향을 미칩니다. 오늘의 글에서는 이 주제를 탐구하고, JavaScript에서 변수의 동작에 미치는 영향을 살펴보죠.

## 목차
1. [스코프란 무엇인가?](#스코프란-무엇인가)
2. [전역 스코프 vs 지역 스코프](#전역-스코프-vs-지역-스코프)
3. [클로저란 무엇인가?](#클로저란-무엇인가)
4. [클로저의 예시](#클로저의-예시)
5. [실습: 클로저로 개인 정보 보호하기](#실습-클로저로-개인-정보-보호하기)
6. [결론 및 다음 포스트 예고](#결론-및-다음-포스트-예고)

## 스코프(Scope)란 무엇인가?
스코프는 코드의 다른 부분에서 변수에 접근할 수 있는 범위를 나타냅니다. JavaScript에는 '전역 스코프'와 '지역 스코프'가 있으며, 이는 변수가 어디서 접근 가능한지를 결정합니다.

## 전역 스코프 vs 지역 스코프
전역 스코프에 선언된 변수는 어디서든 접근할 수 있습니다. 반면, 함수 내부와 같은 지역 스코프에 선언된 변수는 해당 함수 내에서만 접근 가능합니다.

```javascript
let globalVar = "이것은 전역 변수입니다";

function myFunction() {
  let localVar = "이것은 지역 변수입니다";
  console.log(globalVar); // 접근 가능
  console.log(localVar);  // 접근 가능
}

myFunction();
console.log(localVar);  // 에러: myFunction 바깥에서는 localVar가 정의되지 않음
```

## 클로저(Closures)란 무엇인가?
클로저는 내부 함수가 외부 함수의 변수에 접근할 수 있는 기능입니다. 클로저를 통해 내부 함수는 외부 함수의 실행이 끝난 후에도 해당 함수의 변수에 접근할 수 있습니다.

## 클로저의 예시
클로저는 데이터 캡슐화와 비공개 변수를 생성하는 데 사용됩니다.

```javascript
function makeCounter() {
  let count = 0;
  return function() {
    return count++;
  };
}

let counter = makeCounter();
console.log(counter());  // 출력: 0
console.log(counter());  // 출력: 1
```

## 실습: 클로저로 개인 정보 보호하기
클로저를 사용하여 개인 정보를 보호하는 코드를 작성해 봅시다.

```javascript
function createPerson(name) {
  return {
    getName: function() {
      return name;
    }
  };
}

let person = createPerson("John");
console.log(person.getName());  // 출력 "John"
```

## 결론 및 다음 포스트 예고
이 글에서는 JavaScript에서 스코프와 클로저의 중요한 개념을 다뤘습니다. 이 주제들을 이해하면 JavaScript의 작동 방식을 이해하는 데 큰 도움이 됩니다. 다음 포스트에서는 '기본 객체: JavaScript에서 객체로 데이터 구조화하기'를 알아볼 예정입니다. 다음 글에서 봬요!