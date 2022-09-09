---
title: 자바스크립트 - 소개
author: kimjeahyun
date: 2022-09-09 10:00:00 +0900
categories: [개발,자바스크립트]
tags: [개발,자바스크립트]
---

# 자바스크립트

자바스크립트 (JS)는 인터프리터 또는 just-in-time 컴파일 프로그래밍 언어로 일급 함수를 지원한다.

>일급 함수란  함수를 다른 함수에 인수로 제공하거나, 함수가 함수를 반환할 수 있으며, 변수에 할당이 가능한것

자바스크립트는 웹 페이지를 위한 언어로 알려져있지만 꼭 웹페이지에만 사용되는 것은 아니다. Apache couchDB, Adobe Acrobat, Node.js 등 다양한 곳에서 사용된다.

자바스크립트는 다음과 같은 특징을 가지고 있다.
-   다중 패러다임
-   단일 스레드
-   객체지향형
-   함수형

> 자바스크립트를 통하여 무엇을 할 수 있을까?


# 자바스크립트는 HTML 내용을 변경 할 수 있다.

소스코드

```javascript
<div id="TEST_20220909">
    누르면 값이 변경됩니다.
</div>


<script>

    var divObject = document.getElementById("TEST_20220909");

    divObject.addEventListener("click",()=>{
        divObject.innerHTML = "Changed";
    });

    
</script>
```

> 구현

<div id="TEST_20220909">
    누르면 값이 변경됩니다.
</div>


<script>

    var divObject = document.getElementById("TEST_20220909");

    divObject.addEventListener("click",()=>{
        divObject.innerHTML = "Changed";
    });

    
</script>

# 자바스크립트는 스타일 및 속성값을 변경 할 수 있다.

> 구현

<div id="TEST2_20220909">
    누르면 색깔이 변경됩니다.
</div>

<script>

    var divObject2 = document.getElementById("TEST2_20220909");

    divObject2.addEventListener("click",()=>{
        divObject.style.fontColor = 'red';
    });

    
</script>

소스코드


```javascript

<div id="TEST2_20220909">
    누르면 색깔이 변경됩니다.
</div>

<script>

    var divObject2 = document.getElementById("TEST2_20220909");

    divObject2.addEventListener("click",()=>{
        divObject.style.color = 'red';
    });

    
</script>

```

이외에도 자바스크립트를 통하여 다양한 기능을 구현할수 있다.