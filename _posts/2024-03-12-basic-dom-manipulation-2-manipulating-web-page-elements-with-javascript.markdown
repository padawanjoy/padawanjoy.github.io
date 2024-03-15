---
layout: post
title:  "Basic DOM Manipulation (2): Manipulating Web Page Elements with JavaScript"
date:   2024-03-12 16:22:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-12-basic-dom-manipulation-2-manipulating-web-page-elements-with-javascript/01.webp'
tags:   [javascript, js-dev-course, dom]
tags_color: '#db9e00'
featured: true
---
In our previous post, we introduced the basics of interacting with web pages through the DOM. Now, we'll delve deeper into how to actually manipulate web page elements using JavaScript.

## Table of Contents
1. [Changing Element Styles](#changing-element-styles)
2. [Creating and Adding Elements](#creating-and-adding-elements)
3. [Removing Elements](#removing-elements)
4. [Manipulating Classes and Attributes](#manipulating-classes-and-attributes)
5. [Practice: Dynamically Manipulating a Web Page](#practice-dynamically-manipulating-a-web-page)
6. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## Changing Element Styles
With JavaScript, you can change the style of HTML elements. This can be achieved using the **`style`** property:

```javascript
let myElement = document.getElementById('myElement');
myElement.style.color = 'blue';
myElement.style.fontSize = '20px';
```

This code changes the text color of **`myElement`** to blue and sets its font size to 20px.

## Creating and Adding Elements
You can also create new HTML elements and add them to the page with JavaScript:

```javascript
let newElement = document.createElement('p');
newElement.textContent = 'This is a new paragraph.';
document.body.appendChild(newElement);
```

This code creates a new **`<p>`** element, sets its content to 'This is a new paragraph.', and then adds it to the end of the page.

## Removing Elements
It's also possible to remove specific elements from the DOM:

```javascript
let removeElement = document.getElementById('removeMe');
removeElement.parentNode.removeChild(removeElement);
```

This code finds the element with the id **`removeMe`** and removes it from the DOM.

## Manipulating Classes and Attributes
You can add, remove, or change an element's classes. Additionally, you can manipulate the attributes of an element (e.g., id, name):

```javascript
let myElement = document.getElementById('myElement');
myElement.className = 'newClass';  // Change class
myElement.setAttribute('name', 'newName');  // Change attribute
```

## Practice: Dynamically Manipulating a Web Page
Now it's your turn. Use JavaScript to add a new element to the web page and change its style. For instance, add a new **`<div>`** to the page and change its background color.

## Conclusion and Preview of the Next Post
Today, we learned about using JavaScript to manipulate web page elements. In our next post, 'Handling Events: Responding to User Actions on Web Pages', we will explore how web pages handle user inputs and interactions. Stay tuned for more insights into making your web pages more interactive.