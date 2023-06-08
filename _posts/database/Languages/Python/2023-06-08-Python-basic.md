---
title: Basic Python
author: thecordrecode
date: 2023-06-08 10:00:00 +0900
categories: [LANGUAGES,PYTHON]
tags: [LANGUAGES,PYTHON]
---


# You can get various abilities in Python, including variables data types loops conditions and classes.

Hi ,nice to meet you again! I am thecoderecode. I assume you have already learned about what Python is and what applications you can build with it.

In this chapter, we will focus on the basics of Python, including variables , lists, tuples, sets, dictionaries, conditions, loops and classes.

Now , Let's delve into the fundamentals of Python 

Step 1 Create a file named "main.py" in Your project.

```python
import basic

if __name__ == "__main__":
    basic.process()
```

In the code above, you can learn about modules. The line "import basic" imports the basic module, and you can call functions from the basic module.

Now let's move on to Step2 Create a second file named "basic.py in your project. The following code examples will cover topics such as variables, data types etc... 


```python
# This is called variable in Languages of programs
# In python Variable is declared like under the exam code
# You don't need to declare Data type of variable
variable_number = 10

# What is There variables in Python

# List
# List are used to store multiple items in a single variable
myList = [1,2,3,4,5]
myListCharacter = ["Apple","Banana","Cherry"]

# Tuple
# The tuple is a collection which is ordered and unchangeable.
myTuple = (1,2,3,4,5)
myTupleCharacter = ("Apple","Banana","Cherry")

# Set
# Set is a collection which is unordered, unchageable, and unindexed.
mySet = {1,2,3,4,5}
mySetCharacter = {"Apple","Banana","Cherry"}

# Dictionary
# A dictionary is a collection which is ordered, changeable and do not allow duplicates.
myDict = {
    "brand":"Ford",
    "model":"Mustang",
    "year":1964
}

def exceptionThrowFunction():
    x = 1
    if x < 0 :
        raise ValueError

class Person:
    certifications = ["License-1","License-2","License-3","License-4","License-5"]
    def __init__(self,fname,lname):
        self.fname = fname
        self.lname = lname

    def printname(self):
        print(self.fname, self.lname)

    def showMyLicenses(self):
        CertificationIter = iter(self.certifications)

        isok = True
        while isok:
            value = next(CertificationIter)
            if value == None:
                isok = False
                continue
            print(value)



class StrongMan(Person):
    def ListStrongThings(self,fname,lname):
        Person.__init__(self,fname,lname)
        print("I can Lift heavy things")

# This is function that is a block of code which only runs when it is called.
def process():
    try:
        print("# Class Example")
        person1 = StrongMan("kim","jaehyeun")
        person1.printname()
        print("## iter Example and Exception")
        person1.showMyLicenses()
    except:
        print("# Error:An Exception Error Occured")
    else:
        print("# Info:Process is sucessfully")



```


if you execute file "main.py" You'll see next command lines 
```bash
# Class Example
kim jaehyeun
## iter Example and Exception
License-1
License-2
License-3
License-4
License-5
# Error:An Exception Error Occured
```

Congratulation You finished to learn basic skill of python 
