---
layout: post
title:  "반복문 이해하기 (2): while 및 do-while 반복문으로 조건 기반 반복 이해하기"
date:   2024-03-06 11:03:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-06-understanding-loops-2-exploring-while-and-do-while-loops-for-condition-based-repetition/01.webp'
tags:   [javascript, js-dev-course, loops, while, do-while]
tags_color: '#db9e00'
featured: true
---
이번에는 지난 포스트에 이어 JavasScript 반복문에 대해 알아보려고 합니다. 반복문 중에서도 'while'과 'do-while' 반복문에 대해 살펴보려하는데요. 이 두 반복문은 특정 조건에 기반하여 코드 블록을 반복 실행하며, 프로그램 내에서 다양한 반복 작업을 수행하는 데 매우 유용합니다.

## 목차
1. [while 반복문의 기본 구조](#while-반복문의-기본-구조)
2. [do-while 반복문의 기본 구조](#do-while-반복문의-기본-구조)
3. [while vs do-while](#while-vs-do-while)
4. [while 및 do-while 반복문 사용하기](#while-및-do-while-반복문-사용하기)
5. [결론 및 다음 포스트 예고](#결론-및-다음-포스트-예고)

## while 반복문의 기본 구조
**`while`** 반복문은 지정된 조건이 참인 동안 코드 블록을 계속 실행합니다. 구조는 다음과 같습니다:

```javascript
while (조건) {
  // 조건이 참일 때, 실행될 코드
}
```

예를 들어, 1부터 5까지의 숫자를 출력하는 while 반복문은 다음과 같이 작성할 수 있습니다:

```javascript
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

## do-while 반복문의 기본 구조
**`do-while`** 반복문은 코드 블록을 한 번 실행한 다음, 지정된 조건이 참인 동안 실행을 반복합니다. 구조는 다음과 같습니다:

```javascript
do {
  // 실행될 코드 블록
} while (조건);
```

이 구조는 조건을 확인하기 전에 코드 블록을 최소 한 번 실행하고 싶을 때 유용합니다. 예를 들어:

```javascript
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
```

## while vs do-while
**`while`** 반복문과 **`do-while`** 반복문의 주요 차이점은 **`do-while`** 반복문은 시작부터 조건이 거짓이더라도 코드 블록이 최소 한 번은 실행됨을 보장한다는 것입니다.

## while 및 do-while 반복문 사용하기
이제 여러분이 직접 반복문을 사용해 보세요. 사용자에게 "계속하시겠습니까? (yes/no)"를 묻고 답변이 'yes'가 될 때까지 반복하는 프로그램을 **`while`** 또는 **`do-while`** 반복문을 사용하여 작성해 보세요. JavaScript의 **`prompt`**() 함수를 사용할 수 있습니다:

```javascript
let answer;
do {
  answer = prompt("계속하시겠습니까? (yes/no)");
} while (answer !== "yes");
```

## 결론 및 다음 포스트 예고
JavaScript에서 조건 반복을 위한 'while' 및 'do-while' 반복문에 대해 살펴봤습니다. 다음 포스트에서는 '함수의 기초: JavaScript에서 함수 정의 및 호출하기'를 다룰 예정입니다. 함수는 JavaScript에서 중요한 역할을 하므로 꼭 봐주세요!