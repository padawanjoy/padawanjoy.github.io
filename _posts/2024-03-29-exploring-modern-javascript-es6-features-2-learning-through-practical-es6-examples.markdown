---
layout: post
title:  "모던 자바스크립트(ES6+) 기능 (2): 실용적인 ES6+ 예제로 학습하기"
date:   2024-03-29 13:25:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-29-exploring-modern-javascript-es6-features-2-learning-through-practical-es6-examples/01.webp'
tags:   [javascript, js-dev-course, es6, modern-javascript, async, await, import, export]
tags_color: '#db9e00'
featured: true
---
모던 자바스크립트, 특히 ES6 이후의 버전들은 개발에 많은 편의성과 새로운 기능들을 도입했습니다. 이번 포스트에서는 이러한 기능들을 활용해 간단한 ToDo 애플리케이션을 만드는 실습을 해보겠습니다. 간단한 실습이라도 직접 해보면 자바스크립트에 도입된 편의 기능들이 실제로 어떻게 활용될 수 있는지 더 잘 이해할 수 있을거라 생각합니다. 

## 목차
1. [클래스와 상속](#클래스와-상속)
2. [프로미스와 비동기 처리](#프로미스와-비동기-처리)
3. [모듈](#모듈)
4. [스프레드 연산자와 나머지 매개변수](#스프레드-연산자와-나머지-매개변수)
5. [실습: 간단한 ToDo 애플리케이션 만들기](#실습-간단한-todo-애플리케이션-만들기)
6. [마치며](#마치며)

## 클래스와 상속
ES6에서는 전통적인 프로토타입 기반 상속 대신, 클래스 기반의 객체 지향 프로그래밍을 지원하기 위한 **`class`** 키워드를 도입했습니다. 이를 통해 클래스를 선언하고 상속하는 것이 훨씬 쉬워졌습니다.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

let dog = new Dog('Rex');
dog.speak(); // Rex barks.
```

## 프로미스와 비동기 처리
프로미스는 비동기 작업을 쉽게 처리할 수 있게 해주는 객체입니다. **`async`**와 **`await`**는 프로미스를 사용하여 비동기 코드를 동기식으로 작성할 수 있게 해주는 문법적 특성입니다.

```javascript
function fetchUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve({ id: id, name: "홍길동" }), 1000);
  });
}

async function getUser() {
  let user = await fetchUser(1);
  console.log(user.name); // 홍길동
}

getUser();
```

## 모듈
ES6 모듈은 자바스크립트 코드를 여러 파일로 분리하고 재사용할 수 있게 해줍니다. **`import`**와 **`export`** 문을 사용하여 모듈을 가져오거나 내보낼 수 있습니다.

```javascript
// message.js
export function showMessage(msg) {
  console.log(msg);
}

// app.js
import { showMessage } from './message.js';

showMessage('Hello, ES6 Modules!');
```

## 스프레드 연산자와 나머지 매개변수
스프레드 연산자(**``...``**)는 배열이나 객체의 속성을 확장할 때 사용됩니다. 나머지 매개변수는 함수가 받을 수 있는 임의의 수의 인수를 배열로 변환합니다.

```javascript
let parts = ['shoulders', 'knees'];
let body = ['head', ...parts, 'toes'];

console.log(body); // ["head", "shoulders", "knees", "toes"]

function sum(...numbers) {
  return numbers.reduce((prev, curr) => prev + curr, 0);
}

console.log(sum(1, 2, 3)); // 6
```

## 실습: 간단한 ToDo 애플리케이션 만들기
모던 자바스크립트 기능을 활용하여 간단한 ToDo 애플리케이션을 만들어 보겠습니다. 여기서는 클래스, 프로미스, 모듈 등을 사용하여 애플리케이션을 구성해볼 것입니다.

### 1. ToDo 클래스 만들기
먼저 ToDo 항목을 관리할 클래스를 만듭니다.

```javascript
class ToDo {
  constructor() {
    this.tasks = [];
  }

  addTask(task) {
    this.tasks.push(task);
    console.log(`Added task: "${task}"`);
  }

  listTasks() {
    if (this.tasks.length > 0) {
      console.log("Tasks:");
      this.tasks.forEach((task, index) => {
        console.log(`${index + 1}: ${task}`);
      });
    } else {
      console.log("No tasks to show.");
    }
  }
}
```

### 2. ToDo 애플리케이션에 비동기 처리 추가하기
다음으로, 비동기적으로 일정 시간 후에 할 일 목록을 출력하는 기능을 추가해보겠습니다.

```javascript
class ToDo {
  constructor() {
    this.tasks = [];
  }

  addTask(task) {
    this.tasks.push(task);
    console.log(`Added task: "${task}"`);
  }

  listTasks() {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(this.tasks);
      }, 1000);
    });
  }
}

const myToDo = new ToDo();
myToDo.addTask("Learn JavaScript");
myToDo.addTask("Learn ES6+");
myToDo.listTasks().then((tasks) => {
  if (tasks.length > 0) {
    console.log("Tasks:");
    tasks.forEach((task, index) => {
      console.log(`${index + 1}: ${task}`);
    });
  } else {
    console.log("No tasks to show.");
  }
});
```

### 3. 모듈로 코드 분리하기
가능하다면, ToDo 클래스를 별도의 모듈 파일로 분리하고, 메인 애플리케이션 파일에서 이를 불러와 사용합니다. (웹 환경에서 모듈을 사용하기 위해서는 웹팩 같은 번들러 또는 ES 모듈을 지원하는 서버 환경이 필요합니다.)

- **`todo.js`**:

```javascript
export class ToDo {
  // ToDo 클래스 코드
}
```

- **`app.js`**:

```javascript
import { ToDo } from './todo.js';

const myToDo = new ToDo();
// 나머지 코드
```

## 마치며
이번 포스트를 통해 모던 자바스크립트의 주요 기능들을 실제 예제를 통해 살펴보았습니다. 다음 포스트에서는 '자바스크립트 디버깅 기초: 버그를 찾아내고 해결하는 전략'에 대해 다룰 예정입니다. 코드 작성만큼 중요한 것이 디버깅이죠. 디버깅은 더 견고한 코드를 작성할 수 있는
중요한 도구이니 기대해 주세요!