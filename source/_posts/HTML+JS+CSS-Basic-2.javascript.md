---
title: HTML+JS+CSS Basic-2.javascript
date: 2023-10-3 21:06:08
categories:
  - Study Tutorials
tags:
  - CSS
  - HTML
  - JS
description: This article serves as a dictionary for my own work and study, so readers are welcome to bookmark and use it. The author is a back-end development front-end dabbling is not deep, so the article focuses on the breadth and practicality, the principle and performance will not be too much in-depth.
cover: https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310032010660.jpg
---

![](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310032010660.jpg)

## 2. javascript

javascript as a scripting language, syntax and Java there are similarities. For example, comments use double slashes (//), and semicolons (;) as the end of expressions...

### 2.1 Common types

Common types are: String, Number, Boolean, Array, Object.

#### 2.1.1 String

Strings can be wrapped in single or double quotes, and strings can be spliced using the plus sign (+).

It is created as follows:

```js
var str1 = "str1";
var str2 = 'str1';
var str3 = new String("str1");
var str4 = "s"+"tr"+new String("4");

```

Common APIs：

```js
// Determines if a string starts with str, returns true or false.
string.startsWith(str)

// Determines if a string starts with str, returns true or false.
string.endsWith(str)

// Returns the contents of the string len from start+1.
string.substr(start,len)

// Replace string content method: replace str1 with str2
string.replace(str1, str2)

```

Other than that, it is basically the same as java usage.

#### 2.1.2 Number

Can represent either integers or decimals; too large or too small a value can be expressed in scientific notation.

```js
var y=123e5;      // 12300000
var z=123e-5;     // 0.00123

```

The Number type has a more specific object NAN, which represents non-numeric values.

```js
typeof NaN; // "number"

```

A NaN object is not equal to any object, including itself:

```js
NaN == NaN //false

```

You can use the js built-in function isNaN() to determine this:

```js
var nan = NaN;
isNaN(nan); // true
Number.isNaN(NaN); // true

```

When a string can not be converted to a number, return NaN means parsing failure; undefined and NaN arithmetic operations will return NaN; invalid parameters of mathematical functions, such as the square root of a negative number, the logarithm of a negative number, will return NaN; there is an infinity in js, infinity multiplied by 0 will return NaN:

```js
var result = 1/0; //Infinity
var resultN = -1/0; //-Infinity
isNaN(result * 0); // true

```

#### 2.1.3 Boolean

has only two values: true and false; note that it is case sensitive.

#### 2.1.4 Arrays

Arrays in js do not require the same type of elements, but try to keep the element types consistent for easy maintenance.

The way to create an array is as follows:

```js
var test_arr = ["a", 1, null];
var cars=new Array("ET7","ES8","EC6");

```

Common APIs：

```js
//1.Taking and assigning values using subscripts
cars[0]="Saab";
//2.Add, delete last element
list.push("banana");
list.pop();
//3.Adding, deleting the first element
scores.shift();
scores.unshift(76);

```

Other than that, it is basically the same as java usage.

#### 2.1.5 Types of objects

```js
var car = {
    name:"EC6", 
    a:4.5, 
    color:"blue"
};
// There are two ways to get objects
car.name;
car["name"];

```

#### 2.1.6 typeof operator

Returns the approximate type of an object as a string.

```js
typeof new String("str1"); // "object"

typeof "str2"; // "string"

typeof 123e5; // "number"

var b3 = true; 
typeof b3; // "boolean"

var arr_4 = ["a", 1, null];
typeof arr_4; // "object"

var object5 = {
    name:"EC6", 
    a:4.5, 
    color:"blue"
};
typeof object5; // "object"

```

### 2.2 Null Objects

There are two empty objects in js, null and undefined, with the following differences:
(1) null is of type Object; undefined is Undefined

```js
typeof null; // "object"
typeof undefined // "undefined"

```

(2) undefined indicates that an expected value or parameter is missing; a variable declared using var is undefined when it is not assigned a value, when a function is passed as a parameter it is undefined, and when an undefined function returns a value - it returns undefined;

(3) null is often used to explicitly represent an empty or invalid object, array, or variable; to empty a variable or release a reference to an object, set it to null.

### 2.3 Variables and scopes

Variables are declared using var in ES5 and earlier versions of js, and let and const were introduced in ES6; common browsers are compatible with these two keywords and can use them directly.

2.3.1 The var keyword

- Functional level scoping: the scope of a variable is restricted to inside the function in which it is declared, and accessing it from outside the function will result in an error.
- Variable promotion: variable declarations are promoted to the top of the scope.
- Repeatable declarations: subsequent declarations overwrite previous ones.

2.3.2 The let keyword

- Block level scoping: the variable is scoped to the block it is in, i.e. accessing it from outside the block will result in an error.
- No repeated declarations: within the same scope, the same variable cannot be declared repeatedly using let.
- No variable promotion: the variable declared by let can only be used after the declaration statement.

2.3.3 The const keyword

- Constant: cannot be modified after being assigned a value.
- Block level scope: same as let, block level scope.
- Not to be repeated: within the same scope, using const to declare the same variable several times will report an error.

The characteristics and limitations of let and const can advance the possible introduction of hot misoperation in var to the development stage, thus avoiding bugs; therefore, it is recommended to use let and const instead of var in the development process.

### 2.4 Common String and JSON Operations

```js
//1.JSON.stringify()  Converting objects to JSON strings
var obj = {name:"seong", age: 28}
var objStr = JSON.stringify(obj);
console.log(objStr);
//2.JSON.parse()  Converting JSON strings to objects
var obj2 = JSON.parse(objStr)

```

### 2.5 if and switch-case

```js
if (conditional expression 1) {
    // Code to be executed when conditional expression 1 is true
} else if (conditional expression 2) {
    // Code to be executed when conditional expression 2 is true
} else if (conditional expression N) {
    // Code to be executed when conditional expression N is true
} else {
    // Code to execute when all conditional expressions are false
}

```

if-else syntax and Java is basically the same, need to pay attention to the conditional expression for the variable, the zero value to false, non-zero value to true.

```js
let scoreLevel = "A";
switch(scoreLevel){
    case "A":
        //...
        break;
    case "B":
        //...
        break;
    default:
        //...
}

```

The syntax of switch-case is the same as that of Java, and the usage of passthrough and break is also the same.

### 2.6 Try-catch exception handling

```js
try {
 //...
} catch(err) {
    //...
   console.writeln( err.name+ err.message);
} finally {
    //...
}

```

The exception object has name and message information.

### 2.7 for loops and while loops

```js
for (var i = 1; i <= 5; i++) {
 if (i == 3) {
  break;
 }
 console.log('message：' + i);
}

continue、break

var num = 1;
while (num <= 10) {
 console.log(num + '\n');
 num++; 
}

```

for and while usage with Java, continue and break usage is also the same.

### 2.8 With or Without

with(&&), or(||), not(!) is exactly the same as Java

### 2.9 Equality

== determines whether only values are equal; === determines whether values and types are equal.

```js
var str1 = "1";
var int1 = 1;
console.log(str1 == int1);  // true
console.log(str1 === int1); // false

```

