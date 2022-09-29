---
title: 자바스크립트 - 비동기
author: kimjeahyun
date: 2022-09-11 00:00:00 +0900
categories: [Languages for development,JavaScript]
tags: [Languages for development,JavaScript]
---


# 자바스크립트 콜백

콜백은 함수의 매개변수를 통해 전달이 가능하며 함수 내에서 다른 함수를 호출하는 것을 의미한다.


다음 예제를 통해 알수 있듯이 operator라는 매개변수 를 이용하여 함수를 넘길 수 있다.

```javascript

<div id ="output">
		
</div>

<script>
	function plus(number,number2){
		return number+number2;
	}

	function calc(number, number2,operator){
		return operator(number,number2);
	}


	document.getElementById("output").innerHTML = calc(5,5,plus);

</script>

```

# 자바스크립트 Promise

프로마이즈는 코드가 실행되고 무조건 대기한후 해당 코드가 성공하면 실행할수 있게 해주는 키워드이다.

```javascript

<div id ="output">
		
	</div>

	<script>

		var pro = new Promise((sucess,fail)=>{
				
				setTimeout(()=>{
					sucess();
				},2000);

		});

		pro.then((sucess)=>{
			alert("TEST");
		},(fail)=>{

		})
		

	</script>

```


