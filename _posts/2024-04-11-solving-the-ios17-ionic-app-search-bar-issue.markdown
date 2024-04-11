---
layout: post
title:  "Ionic 검색바의 (search) 속성이 동작하지 않는 문제 수정"
date:   2024-04-11 19:21:00 +0900
author: padawanjoy
image:  '/images/posts/2024-04-11-solving-the-ios17-ionic-app-search-bar-issue/01.webp'
tags:   [ionic, ios17, error, searchbar]
tags_color: '#3369f6'
featured: true
---
얼마전 Ionic 앱 프로젝트 관련해서 경험한 문제 현상과 해결한 방법을 공유해보려고 합니다. 같은 문제를 겪으시는 분들에게 도움이 되길 바라면서, 자세한 내용 살펴보죠.

## 목차

## 문제 현상 
저는 Native와 Hybrid 환경에서의 모바일 앱/웹 개발을 오랫동안 해오고 있습니다. 최근에 오래전 참여했던 Ionic 앱 프로젝트 운영 담당자에게 연락을 받았습니다. 앱에 문제가 생겼는데 해결이 안되고 있어서 도움을 요청하는 내용이었는데요. 공식적으로는 이미 유지보수 기간이 종료된 상태였지만 도움을 주기로 하고 현상 확인을 해봤습니다. 

이 앱은 Ionic 4 기반으로 개발되었고, Angular, Cordova, TypeScript를 사용해서 구축되었습니다. 문제는 사용자들이 자신의 기기를 iOS 17.2.1로 업데이트한 후 나타나기 시작했습니다. 사용자가 검색바에 검색어를 입력하고 키패드의 **`'검색(Search)'`** 버튼을 눌렀을 때 아무런 반응이 없는 현상이 생겼던 것인데요. 이는 이전 버전의 iOS에서는 발생하지 않던 문제였습니다.

## AS-IS 분석
검색바는 **`ion-searchbar`** 컴포넌트를 사용하여 구현했고, 컴포넌트의 **`(search)`** 속성으로 검색 버튼을 클릭했을 때 이벤트를 감지해 **`onSearch()`** 함수를 호출하도록 개발 했었습니다.

```html
<!-- ASIS 코드: search.page.html -->
<ion-searchbar #searchBar class="searchbar-style ion-no-padding" placeholder="Please enter your search term" cancelButtonIcon="close-circle" (search)="onSearch($event)"></ion-searchbar>
```

테스트를 해보니 **`onSearch()`** 함수가 호출되지 않음을 확인할 수 있었습니다. **`ion-searchbar`** 컴포넌트의 **`(search)`** 속성이 동작하지 않았던 것이죠. iOS 17.2.1 업데이트 이후 이런 처리가 작동하지 않게 변경이 된 것 같습니다. 

## TO-BE 수정 
이 문제를 해결하기 위해 **`(search)`** 속성 대신, **`(keypress)`** 속성을 사용하도록 바꾸었습니다. **`(keypress)`** 속성은 잘 호출되는걸 확인했는데요. **`(search)`** 속성은 키패드의 **`'검색(Search)'`** 버튼을 클릭했을 때만 호출되었던 반면, **`(keypress)`** 속성은 키패드의 어떤 키를 클릭해도 호출이된다는 차이가 있죠.

**`'검색(Search)'`** 버튼을 클릭했을 때에만 동작하도록 추가 처리를 해주겠습니다. 클릭하는 버튼 키에 따라서 **`keyCode`**가 다르게 전달되는데요. 'Enter' 버튼 키 (Search 키)는 **`keyCode`** 값이 13 입니다. 13일 때만 동작하도록 조건을 줘서 **`'검색(Search)'`** 버튼을 클릭했을 때만 검색 로직이 돌아가도록 하였습니다. 

```html
<!-- TOBE 코드: search.page.html -->
<ion-searchbar #searchBar class="searchbar-style ion-no-padding" placeholder="Please enter your search term" cancelButtonIcon="close-circle" (keypress)="onSearch($event)"></ion-searchbar>
```

```ts
// search.page.ts
onSearch(ev: any) {
     if (ev.keyCode == 13) {   // 검색 버튼(엔터 버튼)이 눌렸을 때
         // 검색 관련 처리 수행
     }
}
```

위와 같이 수정해서 iOS 17.2.1에서 정상적으로 검색 기능이 동작하게 되었습니다. 물론 이전 버전의 iOS에서도 잘 동작됨을 확인했습니다. 

## 마무리 
이번 경험에서처럼 OS 업그레이드와 같은 구동 환경의 변화가 잘 작동하던 기존 코드에도 영향을 줘서 예기치 않은 문제가 생길 수 있는데요. 최신 환경에서 정기적인 테스트가 필수적이며, 문제 해결에 유연한 접근 방식이 중요하다는 것을 다시 한번 느꼈습니다. 이 글이 같은 문제를 경험하는 분들에게 도움이 되기를 바랍니다! 🚀 🖖