---
layout: post
title:  "What is Redux? - How to Use It?"
date:   2024-02-22 12:43:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-22-what-is-redux-how-to-use-it/01.webp'
tags:   [redux, state, react, javascript]
# tags_color: '#e76797'
featured: true
---
In the realm of web development, state management plays a crucial role in determining the user experience. Maintaining a consistent state and updating it in a predictable manner across complex applications can pose a significant challenge to developers. Redux was created to address these issues. This article will thoroughly explain what Redux is, why it's necessary, and how to use it effectively.

## The Birth of Flux and Redux

Flux is an application architecture developed by Facebook for client-side web applications. Its core concept is "unidirectional data flow," making the application's state more predictable and easier to understand. However, due to the variety and complexity of Flux implementations, Redux was developed to simplify and make the ideas behind Flux more flexible, gaining widespread adoption among developers.

## The Complexity of Traditional State Management

In traditional state management, each component manages its own state and passes it to child components via "props". This approach works well for simple applications but becomes increasingly complicated and difficult to debug as the application grows and more components need to share state. Redux solves this problem through centralized state management.

## Core Concepts of Redux: Actions, Reducers, and Store

To understand Redux, it's essential to grasp three main concepts: actions, reducers, and the store.

- **Actions**: Actions are objects that describe what change is needed in the state. They must include a **`type`** field, indicating the action's type. It's akin to writing an order slip in a restaurant, specifying exactly what you want.
- **Reducers**: Reducers are pure functions that take the current state and an action to produce a new state. They decide how to update the state based on the action's type, similar to a chef preparing your order based on the order slip.
- **Store**: The store holds the entire state of the application, similar to a kitchen where prepared food and beverages are stored.

Additionally, understanding the following concepts will be helpful:

- **Dispatch**: Dispatching is the process of sending an action to the store. When a user interaction or event occurs, an action is created and dispatched to the store to update the state, much like handing over an order slip to the kitchen.
- **Selectors**: Selectors are functions used to query the store's state. They allow components to selectively pick parts of the state they need, reducing dependency on the state and increasing reusability, akin to choosing your meal from a menu.

## Implementing Redux with Example Code

### 1. Defining Actions:

```javascript
// actions.js
export const increment = () => ({
  type: 'INCREMENT' // Defines an action to increase the counter value.
});
```

### 2. Creating Reducers:

```javascript
// reducer.js
const initialState = { count: 0 }; // Defines the application's initial state, like a menu at the start of the day.

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }; // Increments the counter value for the INCREMENT action.
    default:
      return state;
  }
}

export default counterReducer;
```

### 3. Creating the Store and Connecting React Components:

```javascript
// store.js
import { createStore } from 'redux';
import counterReducer from './reducer';

const store = createStore(counterReducer); // Creates the store using the reducer, readying the kitchen for customers.
```

```javascript
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import Counter from './Counter';

function App() {
  return (
    <Provider store={store}> // Provides the store to the React app, similar to offering a menu to customers.
      <Counter />
    </Provider>
  );
}
```

### 4. Requesting State Changes and Querying State:

```javascript
// Demonstrating how to change and query state in the Counter component
import { useSelector, useDispatch } from 'react-redux';
import { increment } from './actions';

function Counter() {
  const count = useSelector(state => state.count); // Queries the current counter value, like selecting food from a menu.
  const dispatch = useDispatch(); // Makes the dispatch function available.

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => dispatch(increment())}>Increment</button> // Dispatches the INCREMENT action when the button is clicked, similar to placing an order.
    </div>
  );
}
```

## Conclusion

Redux simplifies state management in complex applications, enabling developers to manage state in a predictable manner. Through this guide, you've learned the fundamental concepts and usage of Redux. Applying Redux allows for more effective state management, easing debugging and maintenance.