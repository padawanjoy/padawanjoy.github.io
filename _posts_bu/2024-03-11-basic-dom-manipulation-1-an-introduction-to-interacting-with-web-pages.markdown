---
layout: post
title:  "기본 DOM 조작 (1): 웹 페이지와 상호작용하기"
date:   2024-03-11 13:24:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-11-basic-dom-manipulation-1-an-introduction-to-interacting-with-web-pages/01.webp'
tags:   [javascript, js-dev-course, dom]
tags_color: '#db9e00'
featured: true
---
JavaScript를 이용하면 웹 페이지와 상호작용을 할 수 있습니다. 이 글에서는 DOM(Document Object Model)의 기본 개념과 이를 통해 웹 페이지와 어떻게 상호작용하지, 그 방법을 살펴보려 합니다.

## 목차
1. [DOM이란 무엇인가?](#dom이란-무엇인가)
2. [DOM 트리 구조](#dom-트리-구조)
3. [요소 선택하기](#요소-선택하기)
4. [요소 속성 및 내용 조작하기](#요소-속성-및-내용-조작하기)
5. [실습: 간단한 DOM 조작](#실습-간단한-dom-조작)
6. [결론 및 다음 글 미리보기](#결론-및-다음-글-미리보기)

## DOM이란 무엇인가?
DOM은 웹 페이지의 구조를 모델로 나타내어 JavaScript가 페이지의 내용, 구조, 스타일을 조작할 수 있게 합니다. 웹 페이지가 브라우저에 로드될 때, HTML을 파싱하고 DOM 트리를 생성합니다.

## DOM 트리 구조
DOM은 문서의 계층 구조를 나타냅니다. 모든 요소, 속성, 텍스트는 노드입니다. 예를 들어, DOM 트리에서 **`<body>`** 태그는 부모 노드가 되고, 그 안의 **`<p>`** 태그는 자식 노드가 됩니다.

## 요소 선택하기
DOM 조작의 첫 단계는 조작하고자 하는 HTML 요소를 선택하는 것입니다. JavaScript는 **`document.getElementById()`**, **`document.getElementsByClassName()`**, **`document.getElementsByTagName()`** 등의 메소드를 제공합니다:

```javascript
let elementById = document.getElementById('example');
let elementsByClassName = document.getElementsByClassName('example-class');
let elementsByTagName = document.getElementsByTagName('p');
```

## 요소 속성 및 내용 조작하기
요소를 선택한 후에는 JavaScript를 사용하여 속성이나 내용을 변경할 수 있습니다. 예를 들어, 요소의 내용을 변경하려면 **`textContent`** 또는 **`innerHTML`** 속성을 사용할 수 있습니다:

```javascript
let myElement = document.getElementById('myElement');
myElement.textContent = "New content";
// or
myElement.innerHTML = "<strong>New content</strong>";
```

## 실습: 간단한 DOM 조작
간단한 웹 페이지에서 요소를 선택하고 내용을 변경하는 것을 연습해 봅시다:

```html
<div id="demo">Change this content.</div>
```

```javascript
let demoElement = document.getElementById('demo');
demoElement.textContent = "DOM 조작을 통해 변경됨!";
```

## 결론 및 다음 글 미리보기
DOM의 기본과 웹 페이지 요소를 선택하고 조작하는 방법을 배웠습니다. 이 지식은 웹 페이지를 동적으로 만드는 데 아주 중요한 내용입니다. 다음 글에서는 '기본 DOM 조작 (2): JavaScript로 웹 페이지 요소 조작하기'를 탐구할 예정입니다. 계속 주목해 주세요!