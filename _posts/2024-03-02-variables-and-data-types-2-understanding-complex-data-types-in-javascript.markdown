---
layout: post
title:  "변수와 데이터 타입 (2): JavaScript에서 복잡한 데이터 타입 이해하기"
date:   2024-03-02 21:57:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-02-variables-and-data-types-2-understanding-complex-data-types-in-javascript/01.webp'
tags:   [javascript, js-dev-course, data-type, object, array, function]
tags_color: '#db9e00'
featured: true
---
이번 글에서는 JavaScript의 복잡한 데이터 타입에 대해 탐구해보려고 합니다. 복잡한 데이터 타입을 이해하는 것은 데이터를 더 효율적으로 관리하고 다양한 프로그래밍 요구 사항을 충족하는 데 도움이 됩니다.

## 목차
1. [객체: 데이터 구조의 기초](#객체-데이터-구조의-기초)
2. [배열: 리스트 관리](#배열-리스트-관리)
3. [함수: 동작의 단위](#함수-동작의-단위)
4. [실습: 객체와 배열 사용하기](#실습-객체와-배열-사용하기)
5. [결론 및 다음 포스트 미리보기](#결론-및-다음-포스트-미리보기)

## 객체: 데이터 구조의 기초
객체는 키-값 쌍으로 구성된 데이터 구조입니다. 예를 들어, 사용자 정보를 저장하려면 다음과 같은 객체를 사용할 수 있습니다:

```javascript
let user = {
  name: "John",
  age: 30,
  isStudent: false
};
```
객체를 사용하면 관련 데이터를 한 곳에 조직화할 수 있으며, **`user.name`** 또는 **`user['age']`**를 사용하여 데이터에 액세스할 수 있습니다.

## 배열: 리스트 관리
배열은 여러 값을 순서대로 저장하는 데 사용됩니다. 예를 들어, 좋아하는 책 목록을 배열로 표현할 수 있습니다:

```javascript
let books = ["Harry Potter", "The Hobbit", "Pride and Prejudice"];
```

배열의 각 요소는 인덱스를 통해 액세스할 수 있으며, **`books[0]`**은 "Harry Potter"를 반환합니다.

## 함수: 동작의 단위
함수는 특정 작업을 수행하는 코드 묶음입니다. 예를 들어, 두 숫자를 더하는 함수는 다음과 같이 작성할 수 있습니다:

```javascript
function add(a, b) {
  return a + b;
}
```

이 함수를 **`add(5, 3)`**로 호출하면 8을 반환합니다.

## 실습: 객체와 배열 사용하기

이제 객체와 배열을 함께 사용하여 도서관에 대한 정보를 담고 있는 객체를 생성해 봅시다:

```javascript
let library = {
  books: ["Harry Potter", "The Hobbit", "Pride and Prejudice"],
  displayBooks: function() {
    this.books.forEach(book => {
      console.log(book);
    });
  }
};

library.displayBooks();
```

이 코드는 콘솔에 도서관의 모든 책을 표시합니다.

## 결론 및 다음 포스트 미리보기
오늘 우리는 JavaScript의 복잡한 데이터 타입인 객체, 배열, 함수에 대해 배웠습니다. 이러한 개념을 이해하고 활용하는 것은 JavaScript 코드를 더 풍부하고 다양하게 만드는데 도움이 될 수 있습니다.. 다음 포스트에서는 '연산자와 표현식: JavaScript 연산자로 데이터 조작하기'를 탐구할 예정입니다. 기대해주세요!