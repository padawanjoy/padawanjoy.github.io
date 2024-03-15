---
layout: post
title:  "Basic DOM Manipulation (1): An Introduction to Interacting with Web Pages"
date:   2024-03-11 13:24:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-11-basic-dom-manipulation-1-an-introduction-to-interacting-with-web-pages/01.webp'
tags:   [javascript, js-dev-course, dom]
tags_color: '#db9e00'
featured: true
---
In our JavaScript learning journey, interacting with web pages is a crucial part. In this post, we will introduce the basic concepts of DOM (Document Object Model) and how it enables interaction with web pages.

## Table of Contents
1. [What is the DOM?](#what-is-the-dom)
2. [DOM Tree Structure](#dom-tree-structure)
3. [Selecting Elements](#selecting-elements)
4. [Manipulating Element Attributes and Content](#manipulating-element-attributes-and-content)
5. [Practice: Simple DOM Manipulation](#practice-simple-dom-manipulation)
6. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## What is the DOM?
The DOM represents the structure of web pages as a model, allowing JavaScript to manipulate the page's content, structure, and styles. When a web page is loaded in the browser, it parses the HTML and creates the DOM tree.

## DOM Tree Structure
The DOM represents the hierarchical structure of documents; all elements, attributes, and text are nodes. For example, in the DOM tree, the **`<body>`** tag would be a parent node, and a **`<p>`** tag inside it would be a child node.

## Selecting Elements
The first step in DOM manipulation is selecting the HTML element you want to manipulate. JavaScript provides methods like **`document.getElementById()`**, **`document.getElementsByClassName()`**, and **`document.getElementsByTagName()`**:

```javascript
let elementById = document.getElementById('example');
let elementsByClassName = document.getElementsByClassName('example-class');
let elementsByTagName = document.getElementsByTagName('p');
```

## Manipulating Element Attributes and Content
Once you've selected an element, you can use JavaScript to change its attributes or content. For instance, to change the content of an element, you can use the **`textContent`** or **`innerHTML`** properties:

```javascript
let myElement = document.getElementById('myElement');
myElement.textContent = "New content";
// or
myElement.innerHTML = "<strong>New content</strong>";
```

## Practice: Simple DOM Manipulation
Let’s practice by selecting an element from a simple web page and changing its content:

```html
<div id="demo">Change this content.</div>
```

```javascript
let demoElement = document.getElementById('demo');
demoElement.textContent = "Changed through DOM manipulation!";
```

## Conclusion and Preview of the Next Post
Today, we learned the basics of the DOM and how to select and manipulate web page elements. This knowledge is essential for making web pages dynamic. In the next post, 'Basic DOM Manipulation (2): Manipulating Web Page Elements with JavaScript', we will explore how to make web pages more dynamic using JavaScript. Stay tuned!