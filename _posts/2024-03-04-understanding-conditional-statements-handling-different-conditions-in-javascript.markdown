---
layout: post
title:  "조건문 이해하기: JavaScript에서 다양한 조건 처리하기"
date:   2024-03-04 12:51:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-04-understanding-conditional-statements-handling-different-conditions-in-javascript/01.webp'
tags:   [javascript, js-dev-course, conditional-statements, if-else, switch]
tags_color: '#db9e00'
featured: true
---
이번 포스트에서는 JavaScript의 조건문에 대해 배울 예정입니다. 조건문을 사용하면 다양한 조건에 따라 다른 동작을 수행할 수 있으며, 프로그램의 흐름을 제어하는 데 중요한 역할을 합니다.

## 목차
1. [조건문이란?](#조건문이란)
2. [if문](#if문)
3. [else if문과 else문](#else-if문과-else문)
4. [switch문](#switch문)
5. [실습: 조건문 사용 예제](#실습-조건문-사용-예제)
6. [결론 및 다음 포스트 미리보기](#결론-및-다음-포스트-미리보기)

## 조건문이란?
조건문은 조건의 참 또는 거짓을 평가하고 그에 따라 코드 블록의 실행 여부를 결정합니다. 이를 통해 프로그램이 다양한 상황에 적절하게 반응할 수 있습니다.

## if문
**`if`**문은 조건문의 가장 기본적인 형태입니다. 지정된 조건이 참인 경우 코드 블록을 실행합니다. 예를 들어, 사용자가 18세 이상인지 확인하려면 다음과 같이 작성할 수 있습니다:

```javascript
let age = 20;
if (age >= 18) {
  console.log("성인입니다.");
}
```

## else if문과 else문
**`else if`**문은 여러 조건을 순차적으로 테스트하는 데 사용됩니다. **`else`**문은 모든 조건이 거짓일 때 실행될 코드 블록을 정의합니다:

```javascript
if (age < 13) {
  console.log("아이입니다.");
} else if (age < 18) {
  console.log("청소년입니다.");
} else {
  console.log("성인입니다.");
}
```

## switch문
**`switch`**문은 변수의 다른 조건에 따라 다른 동작을 수행하는 데 사용됩니다. 각 경우는 **`case`** 키워드로 표시됩니다:

```javascript
let grade = 'A';
switch (grade) {
  case 'A':
    console.log("우수한 성적입니다.");
    break;
  case 'B':
    console.log("평균 성적입니다.");
    break;
  // additional cases
  default:
    console.log("성적 정보가 없습니다.");
}
```

## 실습: 조건문 사용 예제
이제 조건문을 사용하여 간단한 예제를 만들어 보겠습니다. 사용자의 점수에 따라 다른 메시지를 출력하는 코드는 다음과 같습니다:

```javascript
let score = 85;
if (score >= 90) {
  console.log("A등급");
} else if (score >= 80) {
  console.log("B등급");
} else {
  console.log("C등급 이하");
}
```

## 결론 및 다음 포스트 미리보기
JavaScript에서 조건문을 사용하여 프로그램의 흐름을 제어하는 방법을 알아봤습니다. 프로그래밍의 기본 요소인 만큼 다양한 예제로 연습하는 것이 좋습니다. 다음 포스트에서는 '반복문 이해하기 (1): for 반복문으로 반복 작업 수행하기'를 다룰 예정입니다. 계속해서 확인해 주세요!