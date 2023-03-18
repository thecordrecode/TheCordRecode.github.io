---
title: CSS 색깔로 버튼 만들어보기
author: kimjeahyun
date: 2022-08-23 01:00:00 +0900
categories: [Languages for development,CSS]
tags: [Languages for development,CSS]
---

<style>
    *{
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        -o-user-select: none;
        user-select: none;
    }
    .btn-color-v1{
        width:100px;
        height:50px;
        text-align: center;
        line-height: 50px;
        font-size: 18px;
        font-weight: 900;
        cursor:pointer;
    }
    .btn-color-v1:hover{
        opacity:0.6;
    }
    .bg-color-tomato{
        background-color:tomato;
    }
    .bg-color-orange{
        background-color:Orange;
    }
    .bg-color-DodgerBlue{
        background-color:DodgerBlue;
    }
    .bg-color-MediumSeaGreen{
        background-color:MediumSeaGreen;
    }
    .bg-color-Gray{
        background-color:Gray;
    }
    .bg-color-SlateBlue{
        background-color:SlateBlue;
    }
    .bg-color-Violet{
        background-color:Violet;
    }
    .display{
        display:flex;
    }
</style>


# CSS 색깔을 이용하여 버튼 만들어보기


>색깔을 이용하여 버튼 생성해보기

<br>

<div class="display">
    <div class="btn-color-v1 bg-color-tomato">
        button
    </div>
    <div class="btn-color-v1 bg-color-orange">
        button
    </div>
    <div class="btn-color-v1 bg-color-DodgerBlue">
        button
    </div>
    <div class="btn-color-v1 bg-color-MediumSeaGreen">
        button
    </div>
    <div class="btn-color-v1 bg-color-Gray">
        button
    </div>
    <div class="btn-color-v1 bg-color-SlateBlue">
        button
    </div>
    <div class="btn-color-v1 bg-color-Violet">
        button
    </div>
</div>

<br>

>소스

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    *{
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        -o-user-select: none;
        user-select: none;
    }
    .btn-color-v1{
        width:100px;
        height:50px;
        text-align: center;
        line-height: 50px;
        font-size: 18px;
        font-weight: 900;
        cursor:pointer;
    }
    .btn-color-v1:hover{
        opacity:0.6;
    }
    .bg-color-tomato{
        background-color:tomato;
    }
    .bg-color-orange{
        background-color:Orange;
    }
</style>
<body>    
    <div class="btn-color-v1 bg-color-tomato">
        button
    </div>
    <div class="btn-color-v1 bg-color-orange">
        button
    </div>
</body>
</html>
```
