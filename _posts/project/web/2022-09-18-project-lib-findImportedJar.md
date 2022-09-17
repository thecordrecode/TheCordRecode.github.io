---
title: 홈쇼핑 페이지 만들기 레이아웃 잡기
author: kimjeahyun
date: 2022-09-18 00:00:00 +0900
categories: [프로젝트,라이브러리]
tags: [프로젝트,라이브러리]
---

CSS 소스

```css
	*{
		box-sizing: border-box;
		padding: 0;
		margin: 0;
		border: 1px solid black;
		font-family: sans-serif;
		font-size: 1.25rem;
		font-weight: 900;
	}
	.panel{
		width: 100%;
		height: 100%;
	}
	.container{
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
	}
	.container > .container-content{
		flex: 0 0 1081px;
	}
	.row{
		flex-direction: row;
	}
	.column{
		flex-direction: column;
	}
	.header{
		flex: 0 0 186px;
	}
	.header > * > .header-top{
		flex: 0 0 123px;
	}
	.header > * > .header-menu-wrap{
		flex: 1 0 0 ;
	}
	.content{
		flex: 1 0 0;
	}
	.footer{
		flex: 0 0 183px;
	}
	.footer > * > .link-area{
		flex: 0 0 52px;
	}
	.footer > * > .footer-contents{
		flex: 1 0 0;
	}
	.contents{
		height: 1000px;
	}
```

html 소스

```html
	<div class="panel">
		<div class="container column">
			<div class="header">
				<div class="container column">
					<div class="header-top">
						<div class="container">
							<div class="container-content">
								header-top
							</div>
						</div>
					</div>
					<div class="header-menu-wrap">
						<div class="container">
							<div class="container-content">
								header-menu-wrap
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="content">
				<div class="contents">
					<div class="container">
						<div class="container-content">
							contents
						</div>
					</div>
				</div>
			</div>
			<div class="footer">
				<div class="container column">
					<div class="link-area">
						<div class="container">
							<div class="container-content">
								link-area
							</div>
						</div>
					</div>
					<div class="footer-contents">
						<div class="container">
							<div class="container-content">
								footer-contents
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
```