---
title: CSS Button version1
author: kimjeahyun
date: 2022-09-16 00:00:00 +0900
categories: [개발,CSS,Components]
tags: [개발,CSS,Components]
---

<style>
    .btn-1{
		width: 150px;
		height: 45px;
		border: none;
		color: white;

		background-color: black;
		border-radius: 4px;
		transition: ease-out 0.3s;
		font-size:  1rem;
		outline: none;
	}
	.btn-1:hover{
		box-shadow: inset 100px 100px 0 0 white;
		cursor: pointer;
		color: black;
	}
    .btn-2{
		width: 150px;
		height: 45px;
		color: black;
		border-radius: 4px;
		transition: ease-out 0.3s;
		font-size:  1rem;
		outline: none;
		position: relative;
		z-index: 1;

		border: 3px solid black;
	}
	.btn-2:hover{
		color: #fff;
		cursor: pointer;
	}

	.btn-2:before{
		transition: 0.5s all ease;
		position: absolute;
		top: 0;
		left: 50%;
		right: 50%;
		bottom: 0;
		opacity: 0;
		content:  "";
		background-color: black;
	}
	.btn-2:hover:before{
		transition: 0.5s all ease;
		left: 0;
		right: 0;
		opacity: 1;
		z-index: -1;
	}
</style>


<button class="btn-1">HOVER ME!</button>

# html 태그 작성하기

```html
<button class="btn-1">HOVER ME!</button>
```

# CSS 작성하기

```css
    .btn-1{
		width: 150px;
		height: 45px;
		border: none;
		color: white;

		background-color: black;
		border-radius: 4px;
		transition: ease-out 0.3s;
		font-size:  1rem;
		outline: none;
	}
	.btn-1:hover{
		box-shadow: inset 100px 100px 0 0 white;
		cursor: pointer;
		color: black;
	}
```


<button class="btn-2">HOVER ME!</button>

# html 태그 작성하기


```html
<button class="btn-2">HOVER ME!</button>
```

# CSS 작성하기

```css
    .btn-2{
		width: 150px;
		height: 45px;
		color: black;
		border-radius: 4px;
		transition: ease-out 0.3s;
		font-size:  1rem;
		outline: none;
		position: relative;
		z-index: 1;

		border: 3px solid black;
	}
	.btn-2:hover{
		color: #fff;
		cursor: pointer;
	}

	.btn-2:before{
		transition: 0.5s all ease;
		position: absolute;
		top: 0;
		left: 50%;
		right: 50%;
		bottom: 0;
		opacity: 0;
		content:  "";
		background-color: black;
	}
	.btn-2:hover:before{
		transition: 0.5s all ease;
		left: 0;
		right: 0;
		opacity: 1;
		z-index: -1;
	}
```

<style>
    .btn-3{
		width: 150px;
		height: 50px;
		position: relative;
		color: white;
		border: black solid 1px;
        background-color:black;
		z-index: 1;
	}
	.btn-3:hover{
		cursor: pointer;
	}
	.btn-3:before{
		opacity: 0;
		left: 0;
		bottom: 0;
		top: 0;
		right: 0;
		background-color: white;
		content: "";
		position: absolute;
	}
	.btn-3:hover:before{
		transition: 0.5s all ease;
		left: 50%;
		right: 50%;
		z-index: -1;
		opacity: 1;
	}
</style>

<button class="btn-3">HOVER ME</button>

# HTML 선언

```html
<button class="btn-3">HOVER ME</button>
```

# css 작성하기

```css
    .btn-3{
		width: 150px;
		height: 50px;
		position: relative;
		color: white;
		border: black solid 1px;
        background-color:black;
		z-index: 1;
	}
	.btn-3:hover{
		cursor: pointer;
	}
	.btn-3:before{
		opacity: 0;
		left: 0;
		bottom: 0;
		top: 0;
		right: 0;
		background-color: white;
		content: "";
		position: absolute;
	}
	.btn-3:hover:before{
		transition: 0.5s all ease;
		left: 50%;
		right: 50%;
		z-index: -1;
		opacity: 1;
	}
```