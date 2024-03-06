---
layout: post
title:  "Understanding Loops (2): Exploring while and do-while Loops for Condition-Based Repetition"
date:   2024-03-06 11:03:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-06-understanding-loops-2-exploring-while-and-do-while-loops-for-condition-based-repetition/01.webp'
tags:   [javascript, js-dev-course, loops, while, do-while]
tags_color: '#db9e00'
featured: true
---
Continuing our JavaScript journey, today we will learn about 'while' and 'do-while' loops. These two types of loops repeat a block of code based on a specific condition, making them incredibly useful for performing various repetitive tasks within a program.

## Table of Contents
1. [Basic Structure of a while Loop](#basic-structure-of-a-while-loop)
2. [Basic Structure of a do-while Loop](#basic-structure-of-a-do-while-loop)
3. [while vs do-while](#while-vs-do-while)
4. [Practice: Using while and do-while Loops](#practice-using-while-and-do-while-loops)
5. [Conclusion and Preview of the Next Post](#conclusion-and-preview-of-the-next-post)

## Basic Structure of a while Loop
The **`while`** loop continues to execute a block of code as long as a specified condition is true. Its structure is as follows:

```javascript
while (condition) {
  // Code to be executed as long as the condition is true
}
```

For example, a while loop that prints numbers from 1 to 5 can be written as:

```javascript
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

## Basic Structure of a do-while Loop
The **`do-while`** loop executes a block of code once, and then repeats the execution as long as a specified condition remains true. The structure is as follows:

```javascript
do {
  // Code block to be executed
} while (condition);
```

This structure is particularly useful when you want to execute the code block at least once before checking the condition. For example:

```javascript
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
```

## while vs do-while
The main difference between **`while`** and **`do-while`** loops is that **`do-while`** loop guarantees that the code block is executed at least once, even if the condition is false from the start.

## Practice: Using while and do-while Loops
Now, it's your turn to try out the loops. Write a program using **`while`** or **`do-while`** loops that keeps asking the user "Continue? (yes/no)" until the answer is 'yes'. You can use the JavaScript **`prompt`**() function:

```javascript
let answer;
do {
  answer = prompt("Continue? (yes/no)");
} while (answer !== "yes");
```

## Conclusion and Preview of the Next Post
Today, we covered 'while' and 'do-while' loops for conditional repetition in JavaScript. In our next post, we will dive into 'The Basics of Functions: Defining and Calling Functions in JavaScript'. Functions play a critical role in JavaScript, so make sure to follow along!