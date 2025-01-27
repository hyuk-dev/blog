---
title: 'Virtual DOM 정리노트'
date: 2024-12-22T22:53:39+09:00
tags: ["javaScript"]
author: "Lee"
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: true
disableHLJS: false # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: false
ShowRssButtonInSectionTermList: true
UseHugoToc: false
---

# Virtual DOM 이란?
UI의 가상적 표현을 메모리에 저장하고, ReactDOM 같은 라이브러리에 의해 실제 DOM과 동기화하는 프로그래밍 개념으로, 이러한 일련의 과정을 `재조정` 이라고 합니다.
이 접근방식이 React의 선언적 API를 가능하게 합니다. React에게 원하는 UI의 상태를 알려주면 DOM이 그 상태와 일치하게 됩니다.
<br />
<br />
# React가 Virtual DOM 사용하는 법
기존에 javaScript에서 어떤 식으로 DOM 조작을 했을까요?

```javascript
document.querySelector('.example').style.backgroundColor = 'red';
```

위 코드를 보면 `example` 이라는 클래스의 스타일 값만 변경해주는 것 처럼 보이지만,
실제로 DOM에서는 `example` 클래스에 해당하는 엘리먼트와 자식 엘리먼트들을 삭제하고 `background-color = 'red'` 가 적용 된 새로운 엘리먼트로 대체된 후에 다시 새로 렌더링하여 브라우저에 그려지게 됩니다.


리액트는 Virtual DOM을 아주 잘 활용하는데, 변경된 엘리먼트와 자식 엘리먼트만 리렌더링하여 메모리 효율을 높입니다.
<br />
<br />
# 가상 DOM (Virutal DOM) 작동 단계별 프로세스
1. 초기 렌더링: 앱이 시작되고 전체 UI가 가상 DOM으로 표현됩니다. React 요소가 생성되어 가상 구조로 렌더링됩니다.

2. 상태 및 속성 변경: 앱에서 상태 및 속성이 변경되면 React는 가상 DOM에서 영향을 받는 구성 요소를 다시 렌더링합니다. 실제 DOM에는 바로 영향이 가지 않습니다.

3. Diff 알고리즘으로 비교: 현재 버전의 가상DOM과 이전 버전 가상DOM을 비교하여 버전 간의 차이점을 식별합니다.

4. 조정 프로세스: 식별된 차이점을 기반으로 React는 실제 DOM을 업데이트 하는 가장 효율적인 방식으로 업데이트 해야하는 실제 DOM 부분만 변경됩니다. 그래서 성능적 이익을 챙길 수 있습니다.

5. 실제 DOM 업데이트: 마지막으로 실제 DOM에 필요한 변경 사항을 적용합니다.
<br />
<br />
# 웹 개발에서 가상 DOM을 사용하는 이유

1. 단순화된 개발: 가상 DOM을 사용하면 추상화가 더 잘됩니다.

2. 향상된 성능: 실제 DOM을 직접 조작하는 것보다 성능상의 개선을 얻을 수 있습니다.

3. 향상된 사용자 경험: UI 업데이트가 매끄럽고 더 나은 UX에 기여합니다.

4. 크로스 플랫폼 개발: React Native도 비슷한 접근 방식을 이용하고 웹 및 모바일 플랫폼에서 코드를 재사용하여 개발 시간을 단축할 수 있습니다.