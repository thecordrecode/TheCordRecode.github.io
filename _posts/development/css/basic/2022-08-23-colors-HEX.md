---
title: CSS 색깔 HEX를 지정하기
author: kimjeahyun
date: 2022-08-23 01:00:00 +0900
categories: [개발,CSS,CSS기초]
tags: [개발,CSS언어,CSS기초]
---

<style>
    .btn-color-v1{
        width:100px;
        height:50px;
        text-align: center;
        line-height: 50px;
        background-color: rgba(165, 62, 11,1);
        font-size: 18px;
        font-weight: 900;
        cursor:pointer;
    }
    .btn-color-v1:hover{
        background-color: rgba(165, 62, 11,0.6);
    }
</style>


# CSS 색깔 HEX를 이용하여 지정하기

Css는 이미 지정된 색깔 이름 또는 RGB,HEX,HSL,HSLA,RGBA를 사용하여 값을 지정 할 수 있다.

이번시간은 HEX 사용하여 색깔을 지정해보겠다.
HEX는 총 6자리 알파벳과 숫자를 조합해서 색을 지정한다.


> 예제 배경화면에 색깔 지정하기

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
    /* 여기는 주석처리 공간입니다. 영향을 받지 않습니다.*/
    .box{
        width:100px;
        height:50px;
    }

</style>
<body>
    <div class="box" style="background-color: #363636;">
        #363636
    </div>
    <div class="box" style="background-color: #36abcc;">
        #36abcc
    </div>
</body>
</html>

```

> 글자에 색깔 지정하기

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
    /* 여기는 주석처리 공간입니다. 영향을 받지 않습니다.*/
    .box{
        width:100px;
        height:50px;
    }

</style>
<body>
    <div class="box" style="color: #363636;">
        #363636
    </div>
    <div class="box" style="color: #36abcc;">
        #36abcc
    </div>
</body>
</html>

```

> 테두리 색깔 지정하기.

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
    /* 여기는 주석처리 공간입니다. 영향을 받지 않습니다.*/
    .box{
        width:100px;
        height:50px;
        border: solid 1px black;
    }

</style>
<body>
    <div class="box" style="border-color: #363636;">
        #363636
    </div>
    <div class="box" style="border-color: #36abcc;">
        #36abcc
    </div>
</body>
</html>
```

>색깔을 이용하여 버튼 생성해보기

</br>

<div class="btn-color-v1">
    button
</div>

</br>

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
    .btn-color-v1{
        width:100px;
        height:50px;
        text-align: center;
        line-height: 50px;
        background-color: rgba(165, 62, 11,1);
        font-size: 18px;
        font-weight: 900;
        cursor:pointer;
    }
    .btn-color-v1:hover{
        background-color: rgba(165, 62, 11,0.6);
    }
</style>
<body>    
    <div class="btn-color">
        button
    </div>
</body>
</html>
```