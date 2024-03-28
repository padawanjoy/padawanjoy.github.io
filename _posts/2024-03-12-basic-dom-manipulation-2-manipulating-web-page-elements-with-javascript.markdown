---
layout: post
title:  "기본 DOM 조작 (2): JavaScript로 웹 페이지 요소 조작하기"
date:   2024-03-12 16:22:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-12-basic-dom-manipulation-2-manipulating-web-page-elements-with-javascript/01.webp'
tags:   [javascript, js-dev-course, dom]
tags_color: '#db9e00'
featured: true
---
이전 글에서는 DOM을 통해 웹 페이지와 상호작용하는 기본을 소개했습니다. 이제 JavaScript로 실제 웹 페이지 요소를 조작하는 방법을 더 자세히 알아보겠습니다.

## 목차
1. [요소 스타일 변경하기](#요소-스타일-변경하기)
2. [요소 생성 및 추가하기](#요소-생성-및-추가하기)
3. [요소 제거하기](#요소-제거하기)
4. [클래스 및 속성 조작하기](#클래스-및-속성-조작하기)
5. [실습: 웹 페이지 동적으로 조작하기](#실습-웹-페이지-동적으로-조작하기)
6. [결론 및 다음 글 미리보기](#결론-및-다음-글-미리보기)

## 요소 스타일 변경하기
JavaScript로 HTML 요소의 스타일을 변경할 수 있습니다. 이는 **`style`** 속성을 사용하여 처리할 수 있습니다:

```javascript
let myElement = document.getElementById('myElement');
myElement.style.color = 'blue';
myElement.style.fontSize = '20px';
```

이 코드는 **`myElement`**의 텍스트 색상을 파란색으로 변경하고 폰트 크기를 20px로 설정합니다.

## 요소 생성 및 추가하기
새 HTML 요소를 JavaScript로 생성하고 페이지에 추가할 수도 있습니다:

```javascript
let newElement = document.createElement('p');
newElement.textContent = 'This is a new paragraph.';
document.body.appendChild(newElement);
```

이 코드는 새 **`<p>`** 요소를 생성하고 'This is a new paragraph.'로 내용을 설정한 후 페이지 끝에 추가합니다.

## 요소 제거하기
DOM에서 특정 요소를 제거하는 것도 가능합니다:

```javascript
let removeElement = document.getElementById('removeMe');
removeElement.parentNode.removeChild(removeElement);
```

이 코드는 id가 **`removeMe`**인 요소를 찾아 DOM에서 제거합니다.

## 클래스 및 속성 조작하기
요소의 클래스를 추가, 제거, 또는 변경할 수 있습니다. 또한 요소의 속성(예: id, name)을 조작할 수 있습니다:

```javascript
let myElement = document.getElementById('myElement');
myElement.className = 'newClass';  // 클래스 변경
myElement.setAttribute('name', 'newName');  // 속성 변경
```

## 실습: 웹 페이지 동적으로 조작하기
JavaScript를 사용하여 웹 페이지에 새 요소를 추가하고 스타일을 변경해 보세요. 예를 들어, 페이지에 새 **`<div>`**를 추가하고 배경색을 변경해 보세요.

```javascript
// 새로운 <div> 요소 생성
let newDiv = document.createElement('div');

// 새로운 <div> 요소에 텍스트 추가
newDiv.textContent = '이것은 새로운 div입니다!';

// 새로운 <div> 요소에 스타일 적용
newDiv.style.backgroundColor = 'lightblue';
newDiv.style.padding = '20px';
newDiv.style.marginTop = '20px';
newDiv.style.textAlign = 'center';

// 생성된 <div> 요소를 body에 추가
document.body.appendChild(newDiv);
```

## 결론 및 다음 글 미리보기
JavaScript로 웹 페이지 요소를 조작하는 방법을 배웠습니다. 다음 글인 '이벤트 처리: 웹 페이지에서 사용자와 상호작용하기'에서는 웹 페이지가 사용자 입력 및 상호작용을 어떻게 처리하는지 알아볼 것입니다. 웹 페이지를 더 상호작용적으로 만들기 위한 방법에 대해 더 알아봅시다.