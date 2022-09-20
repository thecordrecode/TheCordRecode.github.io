---
title: 자바스크립트 - array 각종 함수 모음
author: kimjeahyun
date: 2022-09-20 00:00:00 +0900
categories: [개발,자바스크립트]
tags: [개발,자바스크립트]
---

# Javscript Sorting Arrays

```javascript
const arrays = ["value1","value2","value3","value4"];
arrays.sort();
```

# Reversing an Array

```javascript
const arrays = ["value1","value2","value3","value4"];
arrays.sort();
arrays.reverse();
```

# Numeric Sort

```javascript
const arrays = [9,1,4,2,8,5,7,3,6];
arrays.sort((a,b)=>{return a - b})
```

# JavaScript Array forEach()

```javascript
const arrays = [45,4,8,1,25];
let txt = "";

arrays.forEach((value,index,array)=>{
    txt +=value + "<br>";
})
```

# JavaScript Array Map()

```javascript
const arrays = [45,4,8,1,25];
const arrays_2 = arrays.map((value,index,array)=>{
    return value * 2;
})
```

# JavaScript Array filter()

```javascript
const arrays = [45,4,8,1,25];
const over18 = arrays.filter((value,index,array)=>{
    return value > 18;
})
```

# JavaScript Array reduce()

```javascript
const arrays = [45,4,8,1,25];
const sum = arrays.filter((total, value, index, array)=>{
    return total + value;
})
```

# JavaScript Array every()

```javascript
const arrays = [45,4,8,1,25];
let allOver18 = arrays.every((value,index,array)=>{
    return value > 18;
})
```

# JavaScript Array some()

```javascript
const arrays = [45,4,8,1,25];
let someOver18 = arrays.some((value,index,array)=>{
    return value > 18;
})
```

# JavaScript Array IndexOf()

```javascript
const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.indexOf("Apple") + 1;
```

# JavaScript Array find()

```javascript
const numbers = [4, 9, 16, 25, 29];
let first = numbers.find((value, index, array) => {
  return value > 18;
});
```