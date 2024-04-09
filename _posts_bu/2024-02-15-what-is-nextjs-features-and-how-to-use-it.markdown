---
layout: post
title:  "Next.js란? - 기능 및 사용 방법"
date:   2024-02-15 10:56:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-15-what-is-nextjs-features-and-how-to-use-it/01.png'
tags:   [next-js, react]
tags_color: '#e76797'
featured: true
---
Next.js는 현대 웹 개발에 있어 필수적인 프레임워크로 자리매김했습니다. 이 프레임워크는 서버 사이드 렌더링(SSR), 정적 사이트 생성(SSG), API 라우트 등의 고급 기능을 제공하여 React 기반 애플리케이션 구축을 간편하고 빠르며 효율적으로 만들어줍니다. Next.js의 개요, 장점, React와의 관계, 사용 방법, 그리고 최신 버전에 대해서 한번 알아보겠습니다.

## Next.js 소개

Next.js는 SSR, SSG, API 라우트와 같은 고급 웹 개발 기능을 쉽게 구현할 수 있는 React 프레임워크입니다. 이는 성능 최적화 및 SEO 친화적 페이지 생성을 용이하게 하며, 웹 애플리케이션 개발 과정을 단순화시킵니다.

## Next.js의 장점

1. **자동 서버 사이드 렌더링(SSR):** 페이지를 더 빠르게 제공하여 SEO(검색 엔진 최적화)에 유리합니다.
2. **정적 사이트 생성(SSG):** 빌드 시에 사이트를 구축하여 빠른 로딩 시간과 효율적인 캐싱을 제공합니다.
3. **파일 기반 라우팅:** `pages` 디렉토리의 파일 구조를 기반으로 자동 라우트 설정을 제공합니다.
4. **API 라우트:** 동일 프로젝트 내에서 백엔드 로직을 위한 API 엔드포인트를 쉽게 생성할 수 있습니다.
5. **풍부한 플러그인 생태계 및 커뮤니티 지원:** 다양한 기능을 손쉽게 추가할 수 있으며, 활발한 커뮤니티의 지원을 받을 수 있습니다.

## React와의 관계

Next.js는 React 위에 구축되었습니다. 즉, Next.js를 사용하기 위해서는 React에 대한 기본적인 이해가 필요합니다. React의 컴포넌트 기반 개발 방식을 유지하면서 추가 기능과 최적화를 제공합니다. React로 만든 컴포넌트를 Next.js 프레임워크 안에서 사용할 수 있으며, Next.js는 이 컴포넌트들을 서버 사이드에서 렌더링하거나 정적 사이트로 생성하는 데 도움을 줍니다.

## 사용 방법

### 프로젝트 생성

새로운 Next.js 프로젝트를 시작하는 것은 매우 간단합니다. 다음 명령어를 통해 새로운 Next.js 애플리케이션을 생성할 수 있습니다:

```bash
npx create-next-app@latest 프로젝트-이름
```

이 과정에서 **`src`** 폴더 생성 여부를 선택할 수 있으며, **`src`** 폴더를 사용하면 **`src/pages`**, **`src/components`** 등으로 프로젝트를 더 모듈화할 수 있습니다.

### 페이지 생성 및 라우팅

- **pages/index.js 구조를 사용할 때:** 이 파일은 웹사이트의 홈페이지를 나타냅니다. 예를 들어, 다음과 같이 작성할 수 있습니다:

```jsx
function HomePage() {
  return <div>Welcome to Next.js!</div>;
}

export default HomePage;
```

- **src/app/page.js & layout.js 구조를 사용할 때:** 최신 버전에서 **`src`** 폴더 선택 시, 페이지와 레이아웃을 관리하는 방법이 조금 변경됩니다. **`page.js`** 파일은 각 페이지의 주요 컴포넌트로, **`layout.js`**는 페이지의 공통 레이아웃을 정의하는 데 사용됩니다.

### 클라이언트 컴포넌트와 서버 컴포넌트

Next.js 최신 버전에서는 클라이언트 컴포넌트와 서버 컴포넌트 사이의 구분이 더욱 명확해졌습니다. **`useState`**와 같은 React 훅은 클라이언트 컴포넌트 내에서만 사용해야 하며, 서버 컴포넌트에서 사용 시 경고 메시지가 나타납니다.

```
You're importing a component that needs useState. It only works in a Client Component but none of its parents are marked with "use client", so they're Server Components by default.
```

이는 특정 컴포넌트를 클라이언트 측에서만 렌더링되도록 명시적으로 표시해야 함을 의미합니다. [이 주제에 대한 자세한 논의는 별도의 글에서 다룰 예정입니다.](https://padawanjoy.com/blog/resolving-errors-with-hooks-like-usestate-in-nextjs).

## 결론

Next.js는 React 기반의 웹 애플리케이션 개발에 있어 강력한 도구입니다. 서버 사이드 렌더링, 정적 사이트 생성, 자동 라우팅 등의 기능을 제공하여 개발자가 보다 쉽고 빠르게 고품질의 웹사이트를 구축할 수 있도록 돕습니다. Next.js를 활용하면 사용자 경험을 향상시키고, SEO를 최적화하며, 개발 과정을 간소화할 수 있습니다.