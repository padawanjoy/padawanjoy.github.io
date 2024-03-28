---
layout: post
title:  "iOS 17 이상에서 발생하는 Ionic 앱 검색창 문제 해결"
date:   2024-01-31 10:20:00 +0900
author: padawanjoy
image:  '/images/posts/2024-01-31-solving-the-ios17-ionic-app-search-bar-issue/01.png'
tags:   [ionic, ios17, error, searchbar]
# tags_color: '#6b96df'
featured: true
---
iOS 17 업데이트 후 Ionic 앱에서 발생한 검색창 문제에 대해 해결했던 경험을 공유하고자 합니다. 제 경험이 여러분의 개발에 도움이 되기를 바라면서, 자세한 내용 살펴보죠.

우선, 저는 다양한 환경에서 모바일 및 웹 개발을 해오고 있으며, iOS & Android Native와 Hybrid 개발에 꽤 오랫동안 참여하고 있습니다. 최근에, 오래전 참여했던 Ionic 앱 프로젝트로부터 유지보수 요청을 받았습니다. 공식적인 유지보수 기간이 종료된 상태였음에도 불구하고, 도움을 주기로 했는데요.

해당 앱은 Ionic 4를 기반으로 개발되었었고, Angular, Cordova, TypeScript를 사용하여 구축되었습니다. 문제는 사용자들이 자신의 기기를 iOS 17.2.1로 업데이트한 후 나타나기 시작했습니다. 사용자가 검색창에 검색어를 입력하고 키패드의 '검색' 버튼을 눌렀을 때 아무런 반응이 없는 현상이 생겼던 것인데요. 이는 이전 버전의 iOS에서는 발생하지 않던 문제였습니다.

검색창은 **`ion-searchbar`** 컴포넌트를 사용하여 구현되었고, 컴포넌트의 **`(search)`** 속성으로 검색 버튼을 클릭했을 때 이벤트를 감지해 **`onSearch()`** 함수를 호출하도록 개발 했었습니다. 그러나 iOS 17.2.1 업데이트 이후 이런 처리가 작동하지 않게 되었습니다.

```html
<!-- ASIS 코드: search.page.html -->
<ion-searchbar #searchBar class="searchbar-style ion-no-padding" placeholder="Please enter your search term" cancelButtonIcon="close-circle" (search)="onSearch($event)"></ion-searchbar>
```

이 문제를 해결하기 위해 **`(keypress)`** 속성을 사용하도록 바꾸고 **`onSearch()`** 함수 로직을 수정하여 'Enter' (또는 검색) 키가 클리되었는지 확인하게 위해 **`keyCode`**를 체크하도록 했습니다. 다음은 수정한 코드입니다:

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

위와 같이 수정해서 iOS 17.2.1에서도 정상적으로 동작하게 했고, 이전 버전의 iOS에서도 잘 동작됨을 확인했습니다.

이번 경험에서처럼 구동 환경의 변화가 기존 코드의 작동 방식에 예기치 않은 영향을 미칠 수 있는데요. 최신 환경에서 정기적인 테스트가 필수적이며, 문제 해결에 유연한 접근 방식이 중요하다는 것을 다시 한번 알 수 있었습니다.

이 글이 여러분의 앱 개발에 도움이 되기를 바랍니다! 🚀 🖖