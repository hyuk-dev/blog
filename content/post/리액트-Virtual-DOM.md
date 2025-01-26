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

# React가 Virtual DOM 사용하는 법
기존에 javaScript에서 어떤 식으로 DOM 조작을 했을까요?

```javascript
document.querySelector('.example').style.backgroundColor = 'red';
```

위 코드를 보면 `example` 이라는 클래스의 스타일 값만 변경해주는 것 처럼 보이지만,
실제로 DOM에서는 `example` 클래스에 해당하는 엘리먼트와 자식 엘리먼트들을 삭제하고 `background-color = 'red'` 가 적용 된 새로운 엘리먼트로 대체된 후에 다시 새로 렌더링하여 브라우저에 그려지게 됩니다.


리액트는 Virtual DOM을 아주 잘 활용하는데, 변경된 엘리먼트와 자식 엘리먼트만 리렌더링하여 메모리 효율을 높입니다.

1. Change of State
2. Diffing
3. Re-render Virtual DOM

