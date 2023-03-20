---
title: Python - Variables
author: kimjeahyun
date: 2023-03-08 12:00:00 +0900
categories: [Languages for development,Python]
tags: [Languages for development,Python]
---


# Introduce 

Hi I'm Thecordrecode 

Today We're gonna study about Variables on Python 3

It is always to study new things everywhere 

Let's go Variable 


# What is variable? and what does it do?

Variables are containers for storing data values.

# Why we should store to variables

There is no the reason to store to variables in my head
But There are a few useful parts that you store to variable

The first that I think is You don't need to write the data 
If you have stored the value to Variables
You don't need to remember the data When you write the value again
You just write name that is stored data 

The second that I think is You can reuse the data and calculate 

All right.!!! Let's go to get the experience of Variable Example 

# How to declare the variable in python 3

> Key point

Unlike other languages like Java , C++ , C# 
You don't have to write the type at Variable 

```python

x = 5
y = "Hello Python world"

```

Yes , it is so easy to declare the Variable in python 3

# You can do casting 

```python
x = str(3) # This is now a String type.
y = int(3) # This is now a Int type
z = float(3) # Yes so easy it is float type.s
```

# When I want to get the type from Variable how Can I do 

Yes it is so easy to get the type from Variable 
You just use the function that is type() 

Under the code, you can see How to use type() function

```python

x = 5
y = "Hello Python world"

print(type(x))
print(type(y))

```

# Python Variables - Assign Multiple Values

Many Values to Multiple Variables

Python allows you to assign values to multiple variables in one line:

```python
x,y,z = "Oranges", "Banana", "Cherry"
print(x)
print(y)
print(z)
```

# One Value to Multiple Variables

And you can assign the same value to multiple variables in one lines:

```python
x = y = z = "Orange"
print(x)
print(y)
print(z)
```

# Unpack a Collection

If you have a collection of values in a list, tuple etc. Python allows you to extract the values into variables. This is called unpacking.

```python
fruits = ["apple","banana","cheery"]
x , y, z = fruits
print(x)
print(y)
print(z)
```

# Global Variables 

Variables that are created outside of a function (as in all of the examples above) are known as global variables.

Global variables can be used by everyone, both inside of functions and outside.

```python
x = "awesome"
def myfunc():
    print("Python is " + x)

myfunc()
```

if you create a variable with the same name inside a function, this variable will be local, and can only be used inside the function. The global variables with the same name will remain as it was, global and with the original value.

```python
x = "awesome"

def myfunc():
    x = "fantastic"
    print("Python is " + x)

myfunc()

print("Python is " + x)
```

# The global keyword
Normally, when you create a variable inside a function, that variable is local, and can only be used inside that function.

To create a global variable inside a function, you can use the global keyword.

```python
def myfunc():
    global x
    x = "fantastic"

myfunc()

print("Python is "+ x)

```

Thank you for your efforts.

See you again next course!!
