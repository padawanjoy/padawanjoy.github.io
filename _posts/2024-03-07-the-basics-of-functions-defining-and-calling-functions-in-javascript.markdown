---
layout: post
title:  "The Basics of Functions: Defining and Calling Functions in JavaScript"
date:   2024-03-07 10:48:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-07-the-basics-of-functions-defining-and-calling-functions-in-javascript/01.webp'
tags:   [javascript, js-dev-course, function]
tags_color: '#db9e00'
featured: true
---
Welcome to an essential part of our JavaScript journey: 'Functions'. Functions are a fundamental component in JavaScript, enabling code reuse and making programs more systematic. In this post, we'll explore the basic concepts of functions, how to define them, and how to call them.

## Table of Contents
1. [What is a Function?](#what-is-a-function)
2. [Defining Functions](#defining-functions)
3. [Calling Functions](#calling-functions)
4. [Parameters and Arguments](#parameters-and-arguments)
5. [Practice: Creating a Simple Function](#practice-creating-a-simple-function)
6. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## What is a Function?
A function is a bundle of code designated to perform a specific task. Once written, it can be reused multiple times, reducing code duplication.

## Defining Functions
There are several ways to define a function in JavaScript, but the most basic form looks like this:

```javascript
function sayHello() {
  console.log("Hello!");
}
```

In this code, **`sayHello`** is the name of the function, and the code inside the curly braces is executed when the function is called.

## Calling Functions
After defining a function, you can call it by adding **`()`** to its name. For example:

```javascript
sayHello();  // Outputs "Hello!"
```

## Parameters and Arguments
Functions can accept input values through parameters, increasing the function's flexibility:

```javascript
function sayHello(name) {
  console.log("Hello, " + name + "!");
}

sayHello("John");  // Outputs "Hello, John!"
```

## Practice: Creating a Simple Function
Now, it's your turn to create a function. Write one that takes two numbers and returns their sum:

```javascript
function add(num1, num2) {
  return num1 + num2;
}

console.log(add(5, 3));  // Outputs 8
```

## Conclusion and Preview of the Next Post
Today, we learned about defining and calling functions in JavaScript. Understanding functions is crucial since they play a significant role in programming. In our next post, we will delve into 'Scope and Closures: Understanding JavaScript's Variable Scope and Closures.' Make sure to grasp the basics before moving on to more advanced topics. Stay tuned!