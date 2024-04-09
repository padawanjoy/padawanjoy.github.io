---
layout: post
title:  "Promises와 Async/Await: JavaScript의 비동기 패턴 깊이 이해하기"
date:   2024-03-16 22:33:00 +0900
author: padawanjoy
image:  '/images/posts/2024-03-16-promises-and-async-await-deep-dive-into-javascript- asynchronous-patterns/01.webp'
tags:   [javascript, js-dev-course, promise, async, await, asynchronous]
tags_color: '#db9e00'
featured: true
---
JavaScript의 비동기 프로그래밍은 사용자와의 상호작용이나 서버로부터의 요청 처리 등을 실행 스레드를 멈추지 않고 다루는 중요한 기술입니다. 이 글에서는 JavaScript에서 비동기 작업을 더욱 효율적으로 관리할 수 있도록 도와주는 Promises와 Async/Await, 이 두 가지 방식의 장점에 대해 알아보겠습니다.

## 목차
1. [Promise란 무엇인가?](#Promise란-무엇인가)
2. [Promise 사용 예제](#Promise-사용-예제)
3. [Async/Await 소개](#AsyncAwait-소개)
4. [Async/Await 사용 예제](#AsyncAwait-사용-예제)
5. [실습: 비동기 작업 연결하기](#실습-비동기-작업-연결하기)
6. [결론 및 다음 포스트 미리보기](#결론-및-다음-포스트-미리보기)

## Promise란 무엇인가?
JavaScript의 Promise는 비동기 작업이 마침내 완료되었을 때(또는 실패했을 때)의 결과를 나타내는 객체입니다. 대기(pending), 이행(fulfilled), 거부(rejected)의 세 가지 상태를 가지며, 비동기 코드를 좀 더 쉽게 다룰 수 있게 해줍니다.

## Promise 사용 예제
Promise 인스턴스를 만들기 위해 **`new Promise`** 구문을 사용할 수 있으며, 이는 비동기 작업을 감싸는 데 유용합니다:

```javascript
let dataLoading = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("데이터 로딩 성공"), 1000);
});

dataLoading.then(
  result => console.log(result), // "데이터 로딩 성공" 출력
  error => console.log(error)
);
```

## Async/Await 소개
ES2017에서 도입된 Async/Await는 Promise 위에 문법적인 단순화를 제공하며, 비동기 코드를 마치 동기 코드처럼 작성하고 동작하게 만들어 줍니다. 이는 비동기 작업의 흐름을 단순화시킵니다.

## Async/Await 사용 예제

```javascript
async function fetchUserData() {
  let response = await fetch('https://api.example.com/user');
  let data = await response.json();
  console.log(data);
}

fetchUserData();
```

## 실습: 비동기 작업 연결하기
웹 개발에서는 사용자 데이터를 가져온 뒤 그 정보를 바탕으로 사용자의 게시물을 가져오는 것 같은 여러 비동기 작업을 연결해야 할 때가 많습니다. Promises와 Async/Await를 사용해서 이러한 작업을 어떻게 처리하는지 살펴보죠.

먼저, fetch 요청 처리를 위한 **`new Promise`** 구문을 사용해서 사용자와 게시물 데이터를 조회하는 코드입니다:

```javascript
function fetchUser(userId) {
  return new Promise((resolve, reject) => {
    fetch(`https://api.example.com/users/${userId}`)
      .then(response => {
        if(response.ok) resolve(response.json());
        else reject(new Error('사용자 데이터를 가져오는 데 실패했습니다.'));
      });
  });
}

function fetchPosts(userId) {
  return new Promise((resolve, reject) => {
    fetch(`https://api.example.com/users/${userId}/posts`)
      .then(response => {
        if(response.ok) resolve(response.json());
        else reject(new Error('게시물을 가져오는 데 실패했습니다.'));
      });
  });
}

fetchUser(1)
  .then(user => {
    console.log(user);
    return fetchPosts(user.id);
  })
  .then(posts => console.log(posts))
  .catch(error => console.error(error));
```

그리고, 동일한 작업을 **`Async/Await`**를 사용해서 구현해보면:

```javascript
async function fetchUserAndPosts(userId) {
  try {
    let user = await fetch(`https://api.example.com/users/${userId}`).then(response => response.json());
    let posts = await fetch(`https://api.example.com/users/${userId}/posts`).then(response => response.json());

    console.log(user);
    console.log(posts);
  } catch (error) {
    console.error(error);
  }
}

fetchUserAndPosts(1);
```

## 결론 및 다음 포스트 미리보기
Promise와 Async/Await를 활용하는 비동기 패턴을 이용하면 복잡한 비동기 로직도 효과적으로 관리할 수 있습니다. 비동기 프로그래밍은 웹 애플리케이션의 성능을 대폭 향상시키는 강력한 방법입니다. 다음 포스트에서는 '모던 JavaScript (ES6+) 기능 탐구 (1): 새로운 문법과 향상된 기능'을 주제로, JavaScript의 최신 기능이 우리의 코드 작성 방식을 어떻게 더 효율적이고 강력하게 만들어주는지 살펴볼 예정입니다. 웹 애플리케이션을 더욱 풍부하게 만드는 데 도움이 되는 더 많은 정보를 기대해 주세요!