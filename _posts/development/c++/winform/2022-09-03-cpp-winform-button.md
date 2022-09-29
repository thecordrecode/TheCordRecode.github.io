---
title: C++-winform 로그인화면 구현
author: kimjeahyun
date: 2022-09-03 11:30:00 +0900
categories: [Languages for development,Cpp]
tags: [Languages for development,Cpp]
---

# Winforms - login windows realizing

This is login windows composes one button and two textBox 
if you success login in then appearing MessageBox of success
if you failure login in then appearing MessageBox of failure

Let's go coding of winforms

explain source code

you need two variables, one for id and the other for password

and 

you need two variables, one for temporary storing of textBox of id Text and the other for temporary storing of textBox of password Text

like under this 

and then you compare the variable of id with the variable of compareId

```cpp
		System::String^ id = "admin";
		System::String^ password = "1q2w3e4r";
		System::String^ compareID = "";
		System::String^ comparePassword = "";

		compareID = textBox1->Text;
		comparePassword = textBox2->Text;


		if (id == compareID) {
			if (password == comparePassword) {
				MessageBox::Show("로그인에 성공 하였습니다.");
			}
			else {
				MessageBox::Show("비밀번호가 틀렸습니다.");
			}
		}
		else {
			MessageBox::Show("아이디가 틀렸습니다.");
		}
```
