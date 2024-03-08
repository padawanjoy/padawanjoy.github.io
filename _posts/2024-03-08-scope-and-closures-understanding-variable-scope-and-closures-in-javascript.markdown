---
layout: post
title:  "Scope and Closures: Understanding Variable Scope and Closures in JavaScript"
date:   2024-03-08 09:36:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-08-scope-and-closures-understanding-variable-scope-and-closures-in-javascript/01.webp'
tags:   [javascript, js-dev-course, scope, closures]
tags_color: '#db9e00'
featured: true
---
Welcome to an integral part of our JavaScript learning journey: 'Scope and Closures'. These concepts are pivotal in understanding how JavaScript operates under the hood. Today's post will delve deep into these subjects and shed light on how they influence the behavior of variables in JavaScript.

## Table of Contents
1. [What is Scope?](#what-is-scope)
2. [Global vs. Local Scope](#global-vs-local-scope)
3. [What are Closures?](#what-are-closures)
4. [Examples of Closures](#examples-of-closures)
5. [Practice: Protecting Private Information with Closures](#practice-protecting-private-information-with-closures)
6. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## What is Scope?
Scope refers to the accessibility of variables in different parts of your code. In JavaScript, there are 'global scopes' where variables are accessible from anywhere in the code, and 'local scopes' where variables can only be accessed within a specific function.

## Global vs. Local Scope
Variables declared in the global scope are accessible from any part of the code. However, variables declared in a local scope, such as within a function, are only accessible within that function. For example:

```javascript
let globalVar = "This is a global variable";

function myFunction() {
  let localVar = "This is a local variable";
  console.log(globalVar); // Accessible
  console.log(localVar);  // Also accessible
}

myFunction();
console.log(localVar);  // Error: localVar is not defined outside of myFunction
```

## What are Closures?
A closure is a feature where an inner function has access to the outer (enclosing) function’s variables. This allows for the inner function to remember the environment in which it was created, even after the outer function has completed execution.

## Examples of Closures
Closures are commonly used for data encapsulation and creating private variables. Here’s an example:

```javascript
function makeCounter() {
  let count = 0;
  return function() {
    return count++;
  };
}

let counter = makeCounter();
console.log(counter());  // Outputs 0
console.log(counter());  // Outputs 1
```

## Practice: Protecting Private Information with Closures
Let's practice using closures by writing code that protects private information using closures:

```javascript
function createPerson(name) {
  return {
    getName: function() {
      return name;
    }
  };
}

let person = createPerson("John");
console.log(person.getName());  // Outputs "John"
```

## Conclusion and Preview of the Next Post
In this post, we covered the crucial concepts of scope and closures in JavaScript. Although these topics can be challenging to grasp, they are essential for understanding how JavaScript works. In our next post, we will explore 'Basic Objects: Structuring Data with Objects in JavaScript.' Stay tuned and keep learning with us!