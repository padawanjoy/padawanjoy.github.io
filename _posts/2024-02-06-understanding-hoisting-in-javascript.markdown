---
layout: post
title:  Understanding Hoisting in JavaScript
date:   2024-02-06 13:13:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-06-understanding-hoisting-in-javascript/01.png'
tags:   [javascript, hoisting]
# tags_color: '#6b96df'
featured: true
---
Hoisting is one of those concepts in JavaScript that can cause quite a bit of confusion. But fear not! In this blog post, we will break down the concept of hoisting in a step-by-step manner that's easy for beginners to understand. We'll also include example codes to illustrate how it works in practice.

## What is Hoisting?

Hoisting in JavaScript refers to the behavior where variable and function declarations are moved to the top of their containing scope before code execution. This means that declarations are stored in memory during the compile phase, allowing us to use variables and functions before they are actually declared in the code.

### Variable Hoisting

In JavaScript, you can declare variables using **`var`**, **`let`**, or **`const`**. Variables declared with **`var`** are initialized with undefined when hoisted, but variables declared with **`let`** and **`const`** are not initialized during hoisting.

```javascript
console.log(x); // undefined
var x = 5;
console.log(x); // 5

console.log(y); // ReferenceError: y is not defined
let y = 10;
```

In the example above, the **`var`**-declared variable **`x`** can be used due to hoisting, but its initial value is **`undefined`**. However, the **`let`**-declared variable **`y`** is hoisted but not initialized, so trying to access it before its declaration results in an error.

### Function Hoisting

Function declarations are hoisted, allowing them to be called before they are defined in the code. However, function expressions are not hoisted.

```javascript
foo(); // "Hello, world!"
function foo() {
    console.log("Hello, world!");
}

bar(); // TypeError: bar is not a function
var bar = function() {
    console.log("Hello, world!");
};
```

The function **`foo`** is defined using a declaration, so it can be called before its point in the code. However, **`bar`** is defined using a function expression assigned to a variable, so it is not hoisted.

## Why Hoisting Matters

Understanding hoisting is crucial for predicting the order of code execution and preventing bugs. It is especially important to understand the differences between **`var`**, **`let`**, and **`const`** and to use them appropriately.
<!-- (Please refer to [this post](https://padawanjoy.com/blog/declaring-variables-in-javascript-var-vs-let-const) to understand the differences between **`var`**, **`let`**, and **`const`**.) -->

## Writing Good Code

To avoid confusion caused by hoisting, here are some recommendations:

- Use **`let`** or **`const`** instead of **`var`** whenever possible.
- Declare variables and functions before using them.
- For readability and maintainability, it's good practice to place function declarations at the top of your code.

## Conclusion

Hoisting is a fundamental concept in JavaScript that you must understand when writing and debugging your code. I hope this post has clarified what hoisting is and how it works, and that you'll be able to write more robust and error-free JavaScript code with this knowledge.

Always keep in mind how hoisting affects your code. By understanding these basic concepts, you'll be able to delve deeper into the intricacies of JavaScript. Happy coding!