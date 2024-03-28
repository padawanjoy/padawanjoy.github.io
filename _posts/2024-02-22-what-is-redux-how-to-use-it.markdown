---
layout: post
title:  "Redux란 무엇인가?"
date:   2024-02-22 12:43:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-22-what-is-redux-how-to-use-it/01.webp'
tags:   [redux, state, react, javascript]
tags_color: '#844eae'
featured: true
---
웹 개발 영역에서 상태 관리는 사용자 경험에 결정적인 역할을 합니다. 복잡한 애플리케이션에서 일관된 상태를 유지하며 예측 가능한 방식으로 상태를 업데이트하는 것은 개발자에게 상당한 도전입니다. Redux는 이러한 도전을 해결하기 위해 탄생했습니다. 이런 Redux에 대해서 Redux가 무엇인지, 왜 필요한지, 그리고 효과적인 사용 방법에 대해 자세히 알아보겠습니다.

## Flux와 Redux의 탄생

Flux는 Facebook에서 클라이언트 측 웹 애플리케이션을 위해 개발한 애플리케이션 아키텍처로, "단방향 데이터 흐름"이 핵심 개념입니다. 이는 애플리케이션의 상태를 예측 가능하고 이해하기 쉽게 만듭니다. 하지만 Flux 구현의 다양성과 복잡성으로 인해서 Redux가 탄생했습니다. Redux는 Flux의 아이디어를 단순화하고 유연하게 만들어 개발자 사이에서 널리 사용하게 되었죠.

## 전통적인 상태 관리의 복잡성

전통적인 상태 관리 방법은, 각 컴포넌트가 자신의 상태를 관리하고 "props"를 통해 자식 컴포넌트에 상태값을 전달합니다. 이 방식은 애플리케이션 규모가 커지고 상태를 공유해야 하는 컴포넌트가 많아지게 되면 복잡해지고 디버깅하기 어렵워집니다. Redux는 이 문제를 중앙 집중식 상태 관리를 통해 해결하고자 했습니다.

## Redux의 핵심 개념: 액션, 리듀서, 스토어

Redux를 이해하기 위해서는 액션, 리듀서, 스토어라는 세 가지 주요 개념을 알아야 합니다.

- **액션**: 상태에 어떤 변경이 필요한지 설명하는 객체로, 반드시 **`type`** 필드를 포함해야 합니다.

```javascript
{
  type: 'INCREMENT'
}
```

- **리듀서**: 현재 상태와 액션을 받아 새로운 상태를 생성하는 순수 함수입니다.

```javascript
function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
}
```

- **스토어**: 애플리케이션의 전체 상태를 보유합니다.

```javascript
const store = createStore(counterReducer);
```

추가적으로 이해하면 도움이 될 개념들은 다음과 같습니다:

- **디스패치**: 디스패치는 사용자의 상호 작용이나 발생한 이벤트에 의해 생성된 액션을 스토어로 전송하는 과정을 말합니다. 이 과정을 통해 애플리케이션의 상태가 업데이트됩니다.
- **셀렉터**: 셀렉터는 애플리케이션의 전체 상태에서 특정 부분만을 추출하는 함수입니다. 이를 통해 컴포넌트는 필요한 상태의 일부분만을 선택적으로 접근할 수 있게 되며, 이는 상태에 대한 의존성을 줄이고 코드의 재사용성을 높입니다.

## Redux 구현 예시 코드

### 1. 액션 정의하기:

```javascript
// actions.js
export const increment = () => ({
  type: 'INCREMENT' // 카운터 값을 증가시키는 액션을 정의합니다.
});
```

### 2. 리듀서 생성하기:

```javascript
// reducer.js
const initialState = { count: 0 }; // 애플리케이션의 초기 상태를 정의합니다.

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 }; // INCREMENT 액션에 대해 카운터 값을 증가시킵니다.
    default:
      return state;
  }
}

export default counterReducer;
```

### 3. 스토어 생성하고 React 컴포넌트 연결하기:

```javascript
// store.js
import { createStore } from 'redux';
import counterReducer from './reducer';

const store = createStore(counterReducer); // 리듀서를 사용하여 스토어를 생성합니다.
```

```javascript
// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import Counter from './Counter';

function App() {
  return (
    <Provider store={store}> // React 앱에 스토어를 제공합니다.
      <Counter />
    </Provider>
  );
}
```

### 4. 상태 변경 요청하기 및 상태 쿼리하기:

```javascript
// Counter 컴포넌트에서 상태를 변경하고 쿼리하는 방법
import { useSelector, useDispatch } from 'react-redux';
import { increment } from './actions';

function Counter() {
  const count = useSelector(state => state.count); // 현재 카운터 값을 쿼리합니다.
  const dispatch = useDispatch(); // 디스패치 함수를 사용 가능하게 합니다.

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => dispatch(increment())}>Increment</button> // 버튼이 클릭될 때 INCREMENT 액션을 디스패치합니다.
    </div>
  );
}
```

## 결론

Redux는 복잡한 애플리케이션에서 상태 관리를 단순화하며 개발자가 상태를 예측 가능한 방식으로 관리할 수 있도록 합니다. Redux를 적용해서, 효과적인 상태 관리를 통해 개발과 운영 측면에서 개선을 이뤄봅시다.💻