---
layout: post
title:  "Understanding Loops (1): Performing Repetitive Tasks with for Loops"
date:   2024-03-05 08:40:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-05-understanding-loops-1-performing-repetitive-tasks-with-for-loops/01.webp'
tags:   [javascript, js-dev-course, loops, for-loops]
tags_color: '#db9e00'
featured: true
---
Welcome back to our JavaScript journey! Today, we're going to delve into one of JavaScript's fundamental building blocks - 'loops'. Specifically, we will focus on **`for`** loops, understanding how they work and how to use them to perform repetitive tasks efficiently.

## Table of Contents
1. [What Are Loops?](#what-are-loops)
2. [The Basic Structure of a for Loop](#the-basic-structure-of-a-for-loop)
3. [Examples of for Loops](#examples-of-for-loops)
4. [Various Uses of for Loops](#various-uses-of-for-loops)
5. [Practice: Creating Examples with for Loops](#practice-creating-examples-with-for-loops)
6. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## What Are Loops?
Loops are programming structures that repeat a block of code as long as a specific condition is met. They increase code reusability and efficiency by enabling the same operations to be performed multiple times.

## The Basic Structure of a for Loop
The **`for`** loop is one of the most common types of loops. Its basic structure is as follows:

```javascript
for (initialization; condition; increment) {
  // Code to be executed repeatedly
}
```

- Initialization: Executed once at the start of the loop.
- Condition: Evaluated before each iteration. If true, the code block is executed.
- Increment: Executed after each iteration.

## Examples of for Loops
Let's look at a simple **`for`** loop example. A code that prints numbers from 1 to 5 can be written as:

```javascript
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

## Various Uses of for Loops
**`for`** loops can be used to traverse elements in an array or to perform a variety of tasks based on certain conditions. For example, to print all elements of an array, you can write:

```javascript
let fruits = ["Apple", "Banana", "Cherry"];
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

## Practice: Creating Examples with for Loops
Now, try writing a **`for`** loop yourself. Create a code that prints even numbers from 1 to 10:

```javascript
for (let i = 1; i <= 10; i++) {
  if (i % 2 === 0) {
    console.log(i);
  }
}
```

## Conclusion and Preview of the Next Post
In this post, we learned how to use **`for`** loops to perform repetitive tasks in JavaScript. **`for`** loops are among the most basic yet powerful tools in JavaScript. In our next post, we will cover 'Understanding Loops (2): Exploring while and do-while Loops for Condition-Based Repetition.' Stay tuned!