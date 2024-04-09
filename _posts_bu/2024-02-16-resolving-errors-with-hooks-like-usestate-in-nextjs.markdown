---
layout: post
title:  "Next.js에서 useState 같은 Hook 사용할 때 발생하는 오류 해결하기: 클라이언트 컴포넌트의 올바른 이해와 사용"
date:   2024-02-16 12:03:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-16-resolving-errors-with-hooks-like-usestate-in-nextjs/01.png'
tags:   [next-js, react, hooks, error]
tags_color: '#e76797'
featured: true
---
Next.js는 서버 사이드 렌더링(SSR), 정적 사이트 생성(SSG) 같은 현대 웹 애플리케이션을 위한 다양한 기능을 제공하는 인기 있는 React 프레임워크입니다. 최근에는 서버 컴포넌트도 도입되었습니다. 하지만, Next.js에 새로운 기능과 변경사항이 도입됨에 따라, 개발자들은 그 과정에서 새로운 오류 메시지를 만나게 될 수도 있는데요. 그 중 하나는 React의 상태 관리에 사용하는 Hook을 사용할 때, 예를 들어 **`useState`**를 클라이언트 컴포넌트 내에서 사용할 때 발생하는 오류입니다.

## 오류의 원인

이런 오류 메시지를 만나는 경우가 있을겁니다. "you're importing a component that needs useState. It only works in a Client Component but none of its parents are marked with 'use client', so they're Server Components by default".

이 문제는 주로 서버 컴포넌트와 클라이언트 컴포넌트가 혼합될 때 발생합니다. 서버 컴포넌트는 클라이언트 측 JavaScript를 포함하지 않고 서버에서 렌더링되므로, React의 상태 관리 훅(**`useState`**, **`useEffect`** 등)을 사용할 수 없습니다.

## 해결책

문제의 컴포넌트 부모를 클라이언트 컴포넌트로 명시적으로 표시하는 것이 가장 간단하고 직관적인 해결책인데요. 파일 최상단에 **`use client`** 지시어를 추가하면 됩니다.

```jsx
"use client";

import React, { useState, useRef } from 'react';

const ClientComponent = () => {
  const [images, setImages] = useState([]);
  const fileInputRef = useRef(null);

  // 생략
}

export default ClientComponent;
```

### 2. 파일 명명 규칙을 사용하여 클라이언트 컴포넌트 식별하기

또 다른 방법은 파일명을 수정하는 것 입니다. Next.js는 특정 파일 이름 규칙을 사용하여 클라이언트 컴포넌트를 자동으로 식별하는 기능을 지원합니다. 예를 들어, 컴포넌트 파일 이름을 **`.client.js`**로 끝나게 함으로써 파일이 클라이언트 컴포넌트를 포함하고 있음을 명시적으로 나타낼 수 있습니다.

```jsx
// ClientComponent.client.js
import React, { useState } from 'react';

export default function ClientComponent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

### 3. 동적 임포트 활용하기

특정 컴포넌트를 클라이언트 측에서만 렌더링하려면 Next.js의 동적 임포트 기능을 활용할 수 있습니다. 이 방법을 사용하면 컴포넌트를 조건부로 클라이언트 측에서 로드하고 렌더링할 수 있습니다.

```jsx
import dynamic from 'next/dynamic';

// 동적으로 컴포넌트를 가져와 클라이언트 측에서만 렌더링합니다.
const ClientComponent = dynamic(() => import('./ClientComponent'), {
  ssr: false, // 서버 사이드 렌더링 비활성화
});

export default function Home() {
  return (
    <div>
      <ClientComponent />
    </div>
  );
}
```

## 결론

서버 및 클라이언트 컴포넌트를 Next.js에서 올바르게 구별하고 사용하는 것은 현대 웹 애플리케이션의 성능을 최적화하는 데 중요합니다. 위에서 설명한 방법을 사용하여 "useState 사용 오류"를 해결하고 Next.js 프로젝트에서 상태를 보다 효율적으로 관리할 수 있습니다.  사용자 경험을 향상시키고 애플리케이션 개발에서 서버 자원을 효율적으로 사용하는데 도움이 되는 글이었길 바랍니다 🖐️