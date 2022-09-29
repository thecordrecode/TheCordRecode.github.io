---
title: CSS 배경화면 
author: kimjeahyun
date: 2022-08-23 20:00:00 +0900
categories: [Languages for development,CSS]
tags: [Languages for development,CSS]
---

<style>
    .boxs{
        display:flex;
    }
    .box{
        width: 100px;
        height: 100px;
        background-color: lightblue;
    }
    .opacity-mid{
        opacity:0.5;
    }
    .bg-image{
        width:100px;
        height:100px;
        background-image:url("../../../../img/info.png");
    }
</style>

# CSS 배경화면 지정하기

>CSS 배경화면 색깔 지정하기.

<div class="boxs">
   <div class="box">
        
   </div>
   <div class="box opacity-mid">
      
   </div>
</div>

```css
.box{
        width: 100px;
        height: 100px;
        background-color: lightblue;
}
.box{
        width: 100px;
        height: 100px;
        background-color: lightblue;
        opacity:0.5;
}

```

# CSS 배경화면 이미지 지정하기


<div class="bg-image">
    
</div>

```css
.bg-image{
    width:100px;
    height:100px;
    background-image:url("../../../../img/info.png");
}

.bg-image{
    width:100px;
    height:100px;
    background-image:url("https://thecordrecode.github.io/img/info.png");
}
```

# 배경화면 반복 호출하기

```css
    background-repeat: repeat-y;
    background-repeat: repeat-x;
    background-repeat: no-repeat;
    background-repeat: space;
    background-repeat: round;
```

# 배경화면 기준점 정하기

```css
    background-position: center;
    background-position: bottom right;
    background-position: 50% 50%;
    background-position: 50px 100px;
```

# 배경화면 attachment

```css
    /*기본 지정값이고 스크롤모드*/
    background-attachment: scroll;
    /*고정 시킨다. 스크롤을 움직여도 안움직임*/
    background-attachment: fixed;
    /*배경이미지 요소내용과 같이 스크롤된다.*/
    background-attachment: local;
    /*기본값으로 지정시킨다..*/
    background-attachment: initial;
    /*부모의 것을 상속 받는다.*/
    background-attachment: inherit;
```