---
layout: post
title:  "JavaScript? ECMAScript?"
date:   2024-02-08 09:02:00 +0900
author: padawanjoy
image:  '/images/posts/2024-02-08-journey-of-javascript-from-its-inception-to-ecmascript/01.png'
tags:   [javascript, ecmascript]
tags_color: '#db9e00'
featured: true
---
자바스크립트는 웹 개발에서 없어서는 안 될 언어가 되었습니다. 그럼에도 불구하고, 자바스크립트의 기원, 그 이름이 붙여진 이유, 그리고 ECMAScript와의 관계에 대해 많은 사람들이 잘 모르는 경우가 있는데요. 그래서 자바스크립트의 역사와 그것이 어떻게 현재까지 진화해왔는지, ECMAScript와의 관계 무엇인지, 둘 사이의 차이점 까지 알아보고자 합니다.

## JavaScript의 탄생

1995년, 넷스케이프 커뮤니케이션스에서 근무하던 엔지니어 브렌던 아이크는 웹 경험을 동적으로 만들기 위한 새로운 언어를 개발했습니다. 당시 웹은 주로 정적인 정보를 공유하는 수단이었기 때문에, 이러한 개발은 큰 전환점이었습니다. 처음에는 Mocha라는 이름으로 시작했으나, 이후 LiveScript로 바뀌었고, 결국 JavaScript라는 이름이 붙여졌습니다.

## 이름의 기원: 왜 JavaScript인가?

JavaScript라는 이름은 당시 상당히 인기 있었던 Sun Microsystems의 Java 언어의 명성을 활용하기 위한 마케팅 전략의 일환으로 선택되었다고 합니다. 이런 명명 전략은 많은 사람들이 Java와 JavaScript가 밀접하게 연관되어 있다고 생각하게 만들었지만, 실제로 두 언어는 서로 매우 다른 목적과 특성을 가지고 있습니다. (관련이 없습니다 🙅‍♂️)

## ECMAScript의 등장

JavaScript의 인기가 높아짐에 따라, 크로스 브라우저 호환성 문제가 생겨나게 되었고, 이를 해결하기 위해 1997년 유럽 컴퓨터 제조업체 협회(ECMA)는 JavaScript의 표준화된 사양, 즉 ECMAScript를 도입하게 되었습니다. 이 표준화 작업은 구문, 유형, 구조 등을 통일하여 웹 개발의 일관성을 보장하기 위한 것이었습니다.

## ECMAScript와 JavaScript: 미묘한 차이

ECMAScript와 JavaScript를 동의어처럼 사용하는 경우가 있는데, 사실 둘은 다른 개념입니다. ECMAScript는 스크립팅 언어의 표준 사양을 정의하는 것이고, JavaScript는 ECMAScript 표준에 기반을 둔 구현체로, 웹 페이지와 상호 작용을 위한 웹 API들, 예를 들어 DOM(Document Object Model)과 BOM(Browser Object Model) 등을 포함합니다. 즉, JavaScript는 ECMAScript의 핵심 사양에 웹 개발을 위한 추가적인 기능들을 더한 것입니다.

ECMAScript는 핵심 언어 사양을 제공하는 반면, JavaScript는 ECMAScript와 웹 API 및 웹 페이지 생성을 위한 다른 기능들을 결합한 실제 사용되는 언어입니다. 이는 JavaScript가 ECMAScript 사양을 준수함과 동시에 더 넓은 범위의 기능을 제공한다는 것을 의미합니다.

## ECMAScript 6 소개 샘플 코드

ECMAScript 6 (ES6), 또는 ECMAScript 2015는 JavaScript에 많은 새로운 기능을 도입했습니다. 다음은 ES6의 주요 기능 중 일부를 보여주는 샘플 코드입니다.

```javascript
// let과 const로 변수 선언
let name = 'Padawan Joy';
const BIRTH_YEAR = 1990;

// 화살표 함수
const greet = (name) => {
  return `Hello, ${name}!`;
}

// 클래스 선언
class Person {
  constructor(name, yearOfBirth) {
    this.name = name;
    this.yearOfBirth = yearOfBirth;
  }

  getAge() {
    return new Date().getFullYear() - this.yearOfBirth;
  }
}

// 예제 사용
const person = new Person('Padawan Joy', 1990);
console.log(greet(person.name)); // Hello, Padawan Joy!
console.log(person.getAge()); // 현재 연도에 따라 달라집니다
```

이러한 새로운 기능들은 자바스크립트 개발자들이 더욱 효율적이고 간결한 코드를 작성할 수 있게 해주며, 프로그래밍 패턴을 더욱 현대적으로 만들어주었습니다.

## 결론

간단한 스크립팅 언어에서 시작해 웹 개발의 핵심으로 자리 잡은 자바스크립트는 그동안 많은 변화와 발전을 거쳤습니다. 자바스크립트가 계속해서 발전하면서, 우리는 앞으로 제공될 새로운 기능과 능력을 기대할 수 있습니다. 이 언어의 역사를 알고 현재의 기능을 이해하는 것은 모든 웹 개발자에게 귀중한 자산이 될 것이라고 생각합니다. 🙋‍♂️