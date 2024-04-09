---
layout: post
title:  "변수와 데이터 타입 (1): JavaScript에서 기본 데이터 타입 다루기"
date:   2024-03-01 16:39:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-01-variables-and-data-types-1-handling-basic-data-in-javascript/01.webp'
tags:   [javascript, js-dev-course, variable, data-type, number, string, boolean, 'null', undefined]
tags_color: '#db9e00'
featured: true
---
JavaScript에 대해 알아보는 두 번째 포스트에 오신 것을 환영합니다! 오늘은 JavaScript의 핵심 요소인 '변수'와 '데이터 타입'에 대해 자세히 알아보겠습니다. 데이터를 저장하고 처리하며 코드를 활성화하는 데 있어서 이 개념들을 이해하는 것은 매우 중요합니다.

## 목차
1. [변수란 무엇인가?](#변수란-무엇인가)
2. [JavaScript의 데이터 타입](#javascript의-데이터-타입)
3. [변수 선언 및 초기화](#변수-선언-및-초기화)
4. [실습: 변수 사용의 간단한 예제](#실습-변수-사용의-간단한-예제)
5. [결론 및 다음 포스트 미리보기](#결론-및-다음-포스트-미리보기)

## 변수란 무엇인가?
변수는 데이터를 저장하기 위한 컨테이너입니다. JavaScript에서는 **`var`**, **`let`**, **`const`** 키워드를 사용해 변수를 선언할 수 있습니다. 예를 들어, 상점에서 사과 가격을 저장하고 확인하고 싶다면 **`let applePrice = 100;`**과 같은 변수를 사용할 수 있습니다.

## JavaScript의 데이터 타입
JavaScript에는 여러 가지 데이터 타입이 있지만, 기본 타입인 숫자(Number), 문자열(String), 그리고 불리언(Boolean)에 초점을 맞춰서 이야기해 보겠습니다.

- **Number**: 모든 종류의 숫자를 나타냅니다. 예: **`let age = 25;`**
- **String**: 텍스트를 나타내며 따옴표로 둘러싸입니다. 예: **`let name = "Alice";`**
- **Boolean**: 논리적 값을 나타내며 true 또는 false의 두 가지 값 중 하나를 가질 수 있습니다. 예: **`let isStudent = true;`**

## 변수 선언 및 초기화
변수를 선언한다는 것은 변수를 생성한다는 것을 의미합니다. 변수를 선언할 때는 **`let`** 또는 **`const`**를 사용할 수 있으며, 초기화하는 동안 값에 할당할 수 있습니다.

```javascript
let message; // 선언
message = 'Hello, JavaScript!'; // 초기화
```

## 실습: 변수 사용의 간단한 예제
이제 배운 내용을 적용해 볼 간단한 예제를 해보겠습니다. 가지고 있는 책의 수를 변수에 저장해 봅시다.

```javascript
let numberOfBooks = 30;
alert('I have ' + numberOfBooks + ' books.');
```

이 코드는 화면에 'I have 30 books.'라는 메시지를 표시합니다.

## 결론 및 다음 포스트 미리보기
오늘은 JavaScript에서 변수와 기본 데이터 타입에 대해 배웠습니다. 간단한 내용이지만 이러한 기초 이해가 기반이 되어야 좋은 코딩을 할 수 있겠죠. 다음 포스트에서는 '변수와 데이터 타입 (2): 복잡한 데이터 타입 이해하기'를 다룰 예정입니다. 계속해서 관심 가져주세요!