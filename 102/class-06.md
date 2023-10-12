# Class-06 Reading Notes: Dynamic web pages with JavaScript

## What are variables in JavaScript?

- A `variable` is a container for a value (data), such as a number or a string
- They do not _contain_ values; they _grasp_ them—two variables can refer to the same value
- A program can access only the values that it still has a reference to
- Variables can also contain complex data and even entire functions

## What does it mean to `declare` a variable?

- To use a variable, you must first create it, which is `declaring` the variable
- To declare the variable, you type the key word `let`, `var`, or `const` followed by the name you want to call your variable to to declare a variable

```js
let age = 25;
let name = 'Patty';
```

> When to use `var`, `let`, or `const`
>
> - Always declare variables
> - Always use `const` if the value should not be changed
> - Always use `const` if the type should not be changed (Arrays and Objects)
> - Use `let` if the value of the variable will be reassigned
> - Only use `var` if you MUST support old browsers

## What is an `assignment` operator, and what does it do?

The **assignment (`=`)** operator is used to assign a value to a variable or property

### Examples of assignment operators

The `=` operator assigns a value to a variable

```js
let x = 10;
let x = 10 + y;
```

The `+=` (addition operator) adds a value to a variable

```js
let x = 10;  
x += 5;
// 10 + 5 
// Expected output: 15
```

The `*=` (multiplier operator) multiples a variable

``` js
let x = 10;  
x *= 5;
// 10 * 5 
// Expected output: 50
```

## What is information received from the user called?

- Information received from the user is called `user input` 
- We use the `prompt()` function to ask for user input
- User input is typically stored in a variable to use the information in the program
