---
title: CSS Button version2
author: kimjeahyun
date: 2022-09-16 00:00:00 +0900
categories: [Languages for development,CSS]
tags: [Languages for development,CSS]
---

<style type="text/css">
	.btn-container{
		background-color: #aa24fc;
		width:500px;
		height:150px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.btn{
		background-color: #aa24fc;
		border: none;
		outline: none;
		font-family: sans-serif;
		position: relative;
		width: 300px;
		height: 50px;
		font-size: 1.25rem;
		letter-spacing: 0.5px;
		color: white;
		cursor: pointer;
		transition: 0.5s;
		z-index: 1;
	}
	.btn:before, .btn:after{
		content: '';
		bottom: 0px;
		width: 2px;
		position: absolute;
		height: 0%;
		background-color: white;
		transition: 0.5s;
	}
	.btn:before{
		left: 0;
	}
	.btn:after{
		right: 0;
	}
	.jh-span{
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 0%;
		background-color: white;
		z-index: -1;
		transition: 0.5s;
	}
	.btn:hover > .jh-span{
		height: 100%;
		transition-delay: 0.5s;
	}
	.btn:hover:before,.btn:hover:after{
		height: 100%;
	}
	.btn:hover{
		color: #aa24fc;
		letter-spacing: 2px;
		font-size: 1.35rem;
	}
</style>


# html 작성하기

```html
	<div class="btn-container">
		<button class="btn">
			BUTTON
			<span></span>
		</button>
	</div>
```

# 스타일 작성하기

```css

	*{
		margin: 0;
		padding: 0;
		background-color: #aa24fc;
		border: none;
		outline: none;
		font-family: sans-serif;
	}
	.btn-container{
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.btn{
		position: relative;
		width: 300px;
		height: 50px;
		font-size: 1.25rem;
		letter-spacing: 0.5px;
		color: white;
		cursor: pointer;
		transition: 0.5s;
		z-index: 1;
	}
	.btn:before, .btn:after{
		content: '';
		bottom: 0px;
		width: 2px;
		position: absolute;
		height: 0%;
		background-color: white;
		transition: 0.5s;
	}
	.btn:before{
		left: 0;
	}
	.btn:after{
		right: 0;
	}
	span{
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 0%;
		background-color: white;
		z-index: -1;
		transition: 0.5s;
	}
	.btn:hover > span{
		height: 100%;
		transition-delay: 0.5s;
	}
	.btn:hover:before,.btn:hover:after{
		height: 100%;
	}
	.btn:hover{
		color: #aa24fc;
		letter-spacing: 2px;
		font-size: 1.35rem;
	}
```

<div class="btn-container">
	<button class="btn">
		BUTTON
		<span class="jh-span"></span>
	</button>
</div>
