---
layout: post
title:  "Ionic header의 얼룩(?) 문제 해결하기"
date:   2024-04-13 22:18:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-13-staining-issue-on-ionic-header/01.webp'
tags:   [ionic, ion-header, stain]
tags_color: '#478aff'
featured: true
---
최근 Ionic을 이용해서 모바일 앱을 개발하는 프로젝트에 참여했습니다. 그런데 페이지 이동 중 header bar에 그림자(?), 얼룩(?) 같이 어두운 명암이 생기는 문제가 있었습니다. 이 문제를 어떻게 해결했는지 공유해보려고 합니다.

## 목차
- [문제 현상](#문제-현상)
- [해결 방법](#해결-방법)
  - [방법 1. 반투명 효과 제거](#방법-1-반투명-효과-제거)
  - [방법 2. 추가 스타일 적용](#방법-2-추가-스타일-적용)
- [마무리](#마무리)

## 문제 현상
최근 Ionic의 header나 footer 컴포넌트는 약간 반투명 스타일이 기본적으로 적용되어 멋스럽게 표현이 되는데요. 이런 효과의 부작용으로 페이지 이동 시 header bar에 잠깐이지만 어두운 얼룩(?)같은게 생기는 현상이 발생할 수 있습니다. 이 현상은 **`ion-header`**를 반투명하게 만드는 **`translucent`** 속성을 적용했을 때 발생하죠.

![페이지 이동시 우상단에 생기는 그림자 모양의 얼룩]({{site.baseurl}}/images/posts/2024-04-13-staining-issue-on-ionic-header/02.webp)

![페이지 이동시 우상단에 생기는 그림자 모양의 얼룩]({{site.baseurl}}/images/posts/2024-04-13-staining-issue-on-ionic-header/03.webp)
*페이지 이동시 우상단에 생기는 그림자 모양의 얼룩*

```html
<ion-header [translucent]="true">
    <ion-toolbar>
        <ion-title>Posts</ion-title>
    </ion-toolbar>
</ion-header>
```

## 해결 방법

### 방법 1. 반투명 효과 제거
첫번째 해결 방법은, ion-header에서 translucent 속성을 제거하면 됩니다. 

```html
<ion-header [translucent]="false">
    <ion-toolbar>
        <ion-title>Posts</ion-title>
    </ion-toolbar>
</ion-header>
```

그러나 이렇게 하면 header bar에 적용한 멋진 반투명 효과가 사라지게 되겠죠. 반투명 효과를 유지하면서 얼룩 문제만 제거할 수 있는 방법은 없을까요?

### 방법 2. 추가 스타일 적용
반투명 효과를 유지하면서 얼룩 문제만 해결하는 방법이 있습니다. 바로 추가 스타일을 적용하는 것 인데요. translucent 속성을 그대로 두고, 아래와 같은 스타일을 적용하는 것입니다. 모든 페이지에 한 번에 적용하려면 global.scss에 추가하면 됩니다. 

```scss
.header-collapse-condense-inactive .header-background {
    backdrop-filter: none !important;
}
```

`backdrop-filter`는 요소의 배경 뒷면에 필터를 적용하는 CSS 속성으로, 이를 이용하여 header bar 뒷 배경을 흐리게 처리할 수 있습니다. Ionic에서는 translucent 속성값을 true로 하면, 내부적으로 `backdrop-filter`와 같은 스타일을 통해 header bar에 효과를 부여합니다. 이러한 효과로 인해 화면 전환 시 얼룩이 생기는 문제가 발생할 수 있는데요.

우리가 추가로 적용한 위의 스타일은 화면이 전환될 때에만 적용되는 `.header-collapse-condense-inactive` 클래스를 통해, `backdrop-filter` 값을 none으로 설정하게 합니다. 다시 말해, 화면이 전환될 때, `backdrop-filter` 스타일을 제거해서 얼룩이 생기지 않도록 하는 것이죠.

이렇게 하면 header bar에 반투명 효과도 적용하면서 동시에 화면 전환시 발생하는 얼룩 문제도 해결할 수 있습니다. 

![화면 전환시 얼룩 문제도 없고, 반투명 속성도 적용되어있는 모습]({{site.baseurl}}/images/posts/2024-04-13-staining-issue-on-ionic-header/04.webp)
*화면 전환시 얼룩 문제도 없고, 반투명 속성도 적용되어있는 모습*

## 마무리
Ionic과 같은 프레임워크를 사용하면 기본적으로 멋스러운 스타일의 컴포넌트들을 제공해줘서 편리한 점도 있지만, 그 컴포넌트에서 문제가 있어서 수정해야하거나 일부 디자인을 변경하고 싶을때가 있을 수 있습니다. 그럴때는 프레임워크 영역이라 수정/변경이 가능할지 난감할 수도 있는데요. 위 내용과 같이 스타일 변경만으로 간단히 해결할 수 있는 부분들이 많이 있습니다. 단, 기본 css의 속성명이 아니라 Ionic 만의 속성명을 사용하는 경우도 많으니 Ionic Docs를 확인해서 정확한 스타일 속성명으로 접근을 해야하는 것도 잊지마세요.