# Fundamentals

## script tag
A browser execute js code automatically when it processes the tag.

### external script
```html
<script src="path/to/script.js"></script>
```

We can use full URL as well for this src.

# Code structure
Use ';' to seperate lines.

# Modern mode -"use strict"
This is to tell the engine that this function is used for the modern browsers.

# Variables

Use "let" or "const" to declare a variable.

## naming convention
* can contain $ or _
* can't start with a digit
* case sensitive
* can be unicode

# Data types

## number
Number type can be integer or float.
Special numeric values:
* Infinity
* NaN (Not a Number)


## BigInt
Number has a range of -2^53 - 1 ~ 2^53 - 1. If BigInt is needed, put an 'n' at the end
```js
const bigInt = 123141231231231231231412312312312313121312n;
```

## string
* single quote
* double quote
* backticks
Backticks allow use to embed variables in a string. 

## Boolean
"true" or "false"

## null
It means "nothing, empty"
```js
let name = null;
```

## undefined
"Value is not assigned"
```js
let age;
alert(age);
```

## Objects and Symbols
Objects are used to stored collections of data and more complex entities.

## typeof operator
Typeof is an operator, not an function. So
```
let age = 10;
typeof age
```
# Interaction
## alert
## prompt
## confirm

# Type conversion
# Nullish coalescing operation '??'
Returns the first argument if not null. Otherwise the second. Same idea as the get function of a python dict.

# functions

## default input value
```js
function foo(input='apple')
```

## function is a value
A function can be assigned to a variable. Note the difference between assigning a function or a function return to a variable.
```js
function foo(){
    console.log('foo');
}
let func = foo;
```
Function can be passed as function argument as well.

# Arrow functions
If function has a single line expression, arrow function can be used
```js
let sum =(a,b) => a+b;
```
If there are multiple line, then
```js
let sum = (a, b) => {
    return a + b;
}
```



