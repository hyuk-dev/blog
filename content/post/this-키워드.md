---
title: "this 키워드에 대해 알아봅시다."
date: 2024-12-20T20:04:46+09:00
# weight: 1
# aliases: ["/first"]
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
UseHugoToc: true
---

(이 포스팅은 javascript 기준으로 작성되었습니다.)

# this 키워드란?

this 키워드는 현재 내가 속해있는 객체를 가리킵니다.

```javascript
const hello = {
    name : "이름",
    world : function(){ return this.name}
}
console.log(hello.world());

// 출력값 : 이름
```
<br/>

# 윈도우에서 this
```javascript
function test(){
    return this;
}

console.log(window === test());
// true
```
위 코드를 브라우저에서 실행해보면, true가 출력됩니다.

<br />

# 메소드 내부함수에서 this
```javascript
const test = {
    hello: function() {
        console.log(this); // test

        function hi() console.log(this); // window
    }

}
```
메소드의 내부함수에서 this를 출력해보면 window가 나옵니다.

<br />

# 콜백함수에서 this
```javascript
    function cb(){
        console.log(this);
    }
    function test(callback){
        callback();
    }
    test(cb); // window 출력
```
콜백함수 내에서 this를 출력해도 window가 나옵니다.

<br/>

# this를 선언한 적 없는데?
자바스크립트에서 함수는 arguments Object와 this를 묵시적으로 전달받습니다.