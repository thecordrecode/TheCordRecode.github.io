---
title: CSS-width-height
author: kimjeahyun
date: 2022-09-14 00:00:00 +0900
categories: [개발,CSS,CSS기초]
tags: [개발,CSS,CSS기초]
---

<style type="text/css">
	.width-height-ex1{
		width:100%;
		height:100px;
		border: 1px solid black;
	}
	.width-height-ex2{
		max-width:500px;
		height:100px;
		border: 1px solid black;
	}
</style>

# width , height 속성값 지정하기

width , height 속성 값은 태그의 너비와 높이를 셋팅해주는 속성 값이다.
너비와 높이를 설정하는 방법은 총 5가지가 존재하는데

        1.auto 
			auto 값은 기본 값이다. 브라우저에서 자동적으로 높이와 너비를 계산해준다.
		2.length
			개발자가 직접 너비를 지정하는 것이다. px,cm,... 다양한 값으로 지정할 수 있다.
		3.percent 
			퍼센트 값으로 값을 지정하는 것이다.
		4.initial 
			너비와 높이 값을 기본 값으로 설정한다.
		5.inherit
			부모의 너비와 높이 값을 가져와 지정한다.


<div class="width-height-ex1">
	이 태그는 100px 의 높이와 100% 의 너비값을 가지고 있다.
</div>

```html
<style type="text/css">
	.width-height-ex1{
		width:100%;
		height:100px;
		border: 1px solid black;
	}
</style>
<div class="width-height-ex1">
	이 태그는 100px 의 높이와 100% 의 너비값을 가지고 있다.
</div>
```

# max-width

		max-width 태그의 최대 너비값을 지정해주는 속성갑이다.
		max-width 또한 width 설정과 같이 지정하는 방식이 같다.

		max-width 값을 사용할때는 브라우저창이 작아질때 자동적으로 너비값을 맞춰준다.
		만약 최대값을 넘어갈경우는 최대값만 유지시킨다.

```html
<style type="text/css">
	.width-height-ex2{
		max-width:500px;
		height:100px;
		border: 1px solid black;
	}
</style>
<div class="width-height-ex2">
	이 태그 값은 너비가 500이상을 절때 넘을 수 없다.
</div>
```