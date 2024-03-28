---
layout: post
title:  "배열과 배열 메소드: JavaScript에서의 효율적인 리스트 관리"
date:   2024-03-10 22:47:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-10-arrays-and-array-methods-efficient-list-management-in-javascript/01.webp'
tags:   [javascript, js-dev-course, array, array-method]
tags_color: '#db9e00'
featured: true
---
JavaScript를 사용할 때, 배열은 정보를 구조화된 방식으로 저장할 수 있는 가장 중요한 방법 중 하나입니다. 이 글에서는 JavaScript 배열의 기본사항과 배열 메소드를 활용하여 리스트를 효율적으로 관리하는 방법을 살펴보겠습니다.

## 목차
1. [배열이란?](#배열이란)
2. [배열 생성하기](#배열-생성하기)
3. [배열 메소드 소개](#배열-메소드-소개)
4. [배열 반복하기](#배열-반복하기)
5. [실습: 배열과 메소드 사용하기](#실습-배열과-메소드-사용하기)
6. [결론 및 다음 글 미리보기](#결론-및-다음-글-미리보기)

## 배열이란?
배열은 여러 값을 단일 변수에 저장하는 데 사용되는 데이터 구조입니다. 각 항목은 인덱스에 의해 참조되며, JavaScript에서 배열은 객체로 간주됩니다.

## 배열 생성하기
JavaScript에서는 값들을 대괄호 **`[]`** 내에 넣고, 쉼표로 구분하여 배열을 생성합니다:

```javascript
let numbers = [1, 2, 3, 4, 5];
let fruits = ["Apple", "Banana", "Cherry"];
```

## 배열 메소드 소개
### push() 메소드
**`push()`** 메소드는 하나 이상의 요소를 배열의 끝에 추가하고, 배열의 새로운 길이를 반환합니다.

```javascript
fruits.push("Mango");
console.log(fruits); // ["Apple", "Banana", "Cherry", "Mango"]
```

### pop() 메소드
**`pop()`** 메소드는 배열의 마지막 요소를 제거하고, 그 요소를 반환합니다.

```javascript
let lastFruit = fruits.pop();
console.log(lastFruit); // "Mango"
console.log(fruits); // ["Apple", "Banana", "Cherry"]
```

## 배열 반복하기
### forEach() 메소드
**`forEach()`** 메소드는 배열의 각 요소에 대해 한 번씩 제공된 함수를 실행합니다.

```javascript
fruits.forEach(function(fruit, index) {
    console.log(`${index + 1}: ${fruit}`);
});
// "1: Apple"
// "2: Banana"
// "3: Cherry"
```

## 실습: 배열과 메소드 사용하기
앞에서 살펴본 내용을 가지고 취미 목록을 만들고, 새로운 취미를 추가한 다음, 각 취미를 출력해 볼까요?

```javascript
let hobbies = ["Reading", "Hiking", "Cooking"];
hobbies.push("Traveling");
hobbies.forEach(hobby => {
    console.log(hobby);
});
```

## 결론 및 다음 글 미리보기
JavaScript에서의 배열과 기본 배열 메소드를 알아봤습니다. 다음 글에서는 '기본 DOM 조작 (1): 웹 페이지와 상호작용하기'를 살펴볼 예정입니다. JavaScript를 사용하여 웹 페이지를 조작하는 방법을 알아보는거라고 보시면 될 것 같네요. 다음 글에서 뵙겠습니다.