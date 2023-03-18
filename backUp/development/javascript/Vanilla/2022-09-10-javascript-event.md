---
title: 자바스크립트 - 이벤트
author: kimjeahyun
date: 2022-09-10 14:00:00 +0900
categories: [Languages for development,JavaScript]
tags: [Languages for development,JavaScript]
---

# 자바스크립트 이벤트

HTML 공통 이벤트

|Event|Description|
|----|------------|
|onchange|요소가 변경될때|
|onclick|유저가 요소를 클릭할때|
|onmouseover|요소에 마우스를 올릴때|
|onmouseout|마우스가 나갈때|
|onkeydown|키를 누를때|
|onload|브라우저가 로딩이 끝날떄|

이벤트를 사용하여 다양한 입력과 액션을 취할 수 있다.

이벤트를 입력하는 방법

```javascript

//HTML 태그에 바로 삽입하기

<element event="javaScript">

//자바스크립트를 통해 삽입하기

document.getlementById("ID").addEventListener("event",function);

```

