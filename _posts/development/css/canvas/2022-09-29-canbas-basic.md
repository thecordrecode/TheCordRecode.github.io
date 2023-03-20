---
title: canvas
author: kimjeahyun
date: 2022-08-22 20:00:00 +0900
categories: [Languages for development,Canvas]
tags: [Languages for development,Canvas]
---

# Canvas API

The Canvas API provides a means for drawing graphics via JavaScript and the HTML element.

Among other things, It can be used for animation , Game Graphics, data visualization, photo manupulation , and real-time video processing

The Canvas API largely focuses on 2D graphics. The WebGL API, which also uses the canvas element, draws hardware-accelerated 2D and 3D graphics.

Basic example

This simple example draws a green rectangle onth a canvas.

> HTML

```html
<canvas id="canvas"></canvas>
```

> JavaScript

```javascript
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.fillStyle = "green";
ctx.fillRect(10, 10, 150, 100);
```