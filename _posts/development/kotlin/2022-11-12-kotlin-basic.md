---
title: Kotlin Introduction
author: kimjeahyun
date: 2022-11-12 00:00:00 +0900
categories: [Languages for development,Kotlin]
tags: [Languages for development,Kotlin]
---


# What is Kotlin? 

Kotlin is a modern, trending programming language that was released in 2016 by JerBrains.

It has become very popular since it is compatible with java
, which means that Java code can be used in kotlin programs.

Kotlin is used for:
-   Mobile applications 
-   Web development
-   Server side Applications
-   Data science
-   And much, much more!

# Why Use Kotlin?

-   Kotlin is fully compatible with Java
-   Kotlin works on different platforms ( windows, Mac, Linux , Raspberry pi, etc.)
-   Kotlin is concise and safe
-   Kotlin is easy to learn , expecially If you already know Java
-   Kotlin is free to use
-   Big Community/support


# Kotlin Syntax

In the previous chapter, we created a kotlin file called Main.kt, and we used the following code to print hello world to the screen:

```kotlin
fun main()
{
    println("Hello World")
}
```

-   The func keyword is used to declare a function. A function is a block of code designed to perform a particular task. In the example above, it declares the main() function

-   The main() function is something you will see in every kotlin program. This function is used to execute code. Any code inside the main() function's curly brackets {} will be executed.

-   For example, the println() function is inside the main() function, meaning that this will be executed. The println() function is used to output/print text, and in our example it will output hello world.


# kotlin Comments

Comments can be used to explain Kotlin code, and to make it more readable. It can also be used to prevent execution when testing alternative code.

# Single-line comments

Single-line comments starts with two forward slashes //
any text between // and the end of the line is ignored by kotlin
This example uses a single-line comment before a line of code:

```kotlin
//This is a comment
println("Hello world")
```

# Muti-line comments

Multi-line comments start with /* and ends with */

```kotlin
/* this is multiple comments */
```

# Kotlin Variables

Variables are containers for storing data values.
To Create a variable, use var or val, and assign a value to it with the equal sign = 

Syntax

```kotlin
var variableName = value
val variableName = value
```

Example 

```kotlin
var name = "kim jae hyeong"
val birthyear = 1995

println(name)
println(birthyear)
```

# Variable Type

unlike many other programming languages, variables in kotlin do not need to be declared with a specified type 

To create a variable in kotlin that should store text and another that should store a number, look at the following example.


When you create a variable with val keyword, you cannot be changed value 

```kotlin
/*
* Date : 2022-11-12
* Author : Kim Jae Hyeon
* Content : This is main Function which is executing Output text of Hello word!
* */
fun main() {

    var userName:String = "kim jae hyeong"
    var age:Int = 28

    println("My name is $userName , My age is $age")

}

```


```kotlin

/*
* Date : 2022-11-12
* Author : kim jae hyeong
* content : This is function for studying about data Type
* */
fun exampleDataType(){

    var myNum:Int = 5
    var myDoubleNum:Double = 5.99
    var myLetter:Char = 'A'
    var myBoolean:Boolean = true
    var myText:String = "Hello"

}


```

# Kotlin Strings

Kotlin Strings

Strings are used for storing text.

A String contains a collection of characters surrounded  by double quotes


# String length 

```kotlin
var txt = "Kotlin is easy to learn and so funny "
println("length of txt is "+txt.length)
```

# String Functions

There are many strings functions available, for example toUpperCase() and toLowerCase()

```kotlin
fun stringUpperAndLowerExample(txt:String){
    println("original Txt: $txt")
    println("upper: "+txt.uppercase())
    println("loower: "+txt.lowercase())
}
```

# Comparing Strings

```kotlin

fun comparingFunc(txt:String,txt_2:String): Boolean{
    if(txt.compareTo(txt_2) == 0)
        return true
    else
        return false
}

```
# Finding a String in a String

```kotlin
fun FindingString(txt:String){
    var txt1 = "Please locate where occurs!"
    println(txt1.indexOf(txt))
}
```

# Kotlin if 

```kotlin
if(condition1){
    // block of code to be executed if conditional is true
}
else if(condition2){

}
else{

}
```

# Kotlin When 

instead of writing many if...else expressions, you can use the when expression , which is much easier to read.

it is used to select one of many code blocks to be executed:

```kotlin
fun findDay(number:Int):String{
    var result = when (number){
        1 -> "Monday"
        2 -> "Tuesday"
        3 -> "Wednesday"
        else -> "Invalid Day"
    }
    return result
}
```

# Kotlin While Loop

Loops

Loops can execute a block of code as long as a specified condition is reached.

Loops are handy becauses they save time, reduce errors, and they make code more readable.


# Kotlin while Loop

```kotlin
while(condition){
    //code block to a be executed
}
```

# Kotlin break and continue

Kotlin Break

The break statement is used to jump out of a loop.

Kotlin continue

The continue statement breaks one iteration, if a specified condition occurs, and continues with the next iteration in the loop.

# Kottlin array

```kotlin
var cars = arrayOf("good","good job")
```

# kotlin For Loop

Kotlin For Loop

Often when you work with arrays , you need to loop through all of the elements.

To loop through array elements, use the for loop together with the in operator:

```kotlin
var cars = arrayOf("Volvo","BMW","Ford","MazDa")
for(x in cars)
    println(x)
```

# Kotlin Classes and Objects

Kotlin Classes / Objects

Everything in kotlin is associated with classes and objects , along with its properties and functions. For example : in real life, a car is an object. The car has properties, such as brand, weight and color, and functions, such as drive and brake.

```kotlin
class Car{
    var brand = ""
    var model = ""
    var year = 0
}
fun main() {

    var c1 = Car()
    c1.brand = "Ford"
    c1.model = "Mustang"
    c1.year = 1969

    println(c1.brand)
    println(c1.model)
    println(c1.year)
}
```


```kotlin
class Car(var brand: String,var model: String, var year:Int){
}
fun main() {

    var c1 = Car("Ford","Mustang",1969)

    println(c1.brand)
    println(c1.model)
    println(c1.year)
}
```