---
layout: post
title:  "Next.js에서 useState 같은 Hook 사용할 때 발생하는 오류 해결하기"
date:   2024-04-20 22:5:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-20-resolving-errors-with-hooks-like-usestate-in-nextjs/01.webp'
tags:   [next-js, react, hooks, error, ssr, csr, rsc, use-client, use-server]
tags_color: '#e76797'
featured: true
---
Next.js 프로젝트에서 **`useState`**와 같은 Hook을 사용하면 오류 메시지와 함께 웹 애플리케이션이 동작하지 않는 현상을 겪을 수 있습니다. 이 오류는 왜 발생하는 것인지, 그리고 어떻게 수정하면 되는지를 알아보겠습니다. 

## 목차
- [Next.js란?](#nextjs란)
- [오류 현상](#오류-현상)
- [오류 원인](#오류-원인)
- [오류 해결 방법](#오류-해결-방법)
- [마무리](#마무리)

<br>
## Next.js란?
Next.js는 React를 기반으로 하는 서버 사이드 렌더링(SSR) 프레임워크입니다. React는 HTML, Javascript와 같은 파일을 브라우저에서 렌더링하는 클라이언트 사이트 렌더링(CSR) 웹 프레임워크인데요. 이로 인해 페이지 간 전환, 컴포넌트 업데이트 등이 부드럽고 빠르다는 장점이 있지만, 초기 페이지 로딩이 느리고 SEO(Search Engine Optimization)에 불리하다는 단점이 있습니다. 이런 단점을 해결하기 위해 프레임워크들 중 하나가 바로 Next.js입니다. 클라이언트가 아닌 서버 영역에서 렌더링을 하며 CSR이 가진 단점을 극복하려는 프레임워크인 것이죠.

## 오류 현상
최근 Next.js에서 React의 상태 관리에 사용되는 **`useState`**와 같은 Hook을 사용하면 렌더링 시에 다음과 같은 오류 메시지가 발생합니다.

```html
"you're importing a component that needs useState. It only works in a Client Component but none of its parents are marked with 'use client', so they're Server Components by default"
```

## 오류 원인
이 오류는 Next.js 13 버전에서의 큰 변화와 관련이 있습니다. Next.js 13에서 React 18 버전의 기능들이 많이 도입되었는데요. React 18의 서버 컴포넌트(RSC)라는 기능도 도입이 되었습니다. 기존 React는 주로 클라이언트 사이드에서 렌더링이 되었다면, RSC를 통해 서버에서 많은 부분 렌더링을 시키는 것이죠.

이렇게 서버와 클라이언트, 두 측면에서 렌더링을 할 수 있게 됨으로써 편리한 점이 늘었으나 서버 컴포넌트와 클라이언트 컴포넌트를 구분없이 사용했을 때, 지금과 같은 오류가 발생할 수도 있게 되었죠. 서버 컴포넌트는 클라이언트 측 JavaScript를 포함하지 않고 서버에서 렌더링되므로, React의 상태 관리 Hook(**`useState`**, **`useEffect`** 등)을 사용할 수 없는 것인데요. 사실 오류라기 보다는 서버 컴포넌트에서 클라이언트 컴포넌트에서 사용해야하는 Hook을 잘 못 사용했다고 알려주는 메시지인게 맞는 표현이겠네요.

## 오류 해결 방법
Next.js 13에서 React 18의 서버 컴포넌트(RSC) 기능이 도입되었고, 서버와 클라이언트, 두 측면에서 렌더링을 할 수 있게 되었죠. 우리는 지시어를 이용해서 어디에서 렌더링을 할건지 설정할 수가 있는데요. 그 지시어는 **`use client`**와 **`use server`**라는 지시어 입니다. 

그런데 이런 지시어를 사용하지 않고 클라이언트 사이드에서 사용해야할 Hook을 사용하니 문제가 된 것이죠. 오류 메시지가 발생하는 컴포넌트, 또는 그 부모 컴포넌트에 **`use client`** 지시어를 사용해서 명시적으로 클라이언트 컴포넌트임을 설정하면 오류가 해결됩니다.

지시어는 파일 최상단에 아래 예시 코드처럼 작성하면 됩니다.

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

## 마무리
서버 및 클라이언트 컴포넌트를 Next.js에서 올바르게 구별하고 사용하는 것은 웹 애플리케이션의 성능을 최적화하는 데 중요합니다. Next.js 13, React 18 등 웹 개발을 위한 프레임워크가 발전될 수록 서버 사이드와 클라이언트 사이드의 경계도 흐려지는 것 같습니다. 처음에는 이런 점이 모호하고 필요성에 의문이 생길 수 있지만 조금만 살펴보면 성능과 개발 효율성 면에서 좋은 발전인거 같습니다.