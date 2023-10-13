# Class-08 Reading Notes: Operators and Loops

## What is an `expression` in JavaScript?

- Valid unit of code that resolves to a value
- There are two types of expressions: those that have side effects (such as assigning values) and those that purely *evaluate*

### Type 1

>`x + 7` expression uses the `=` operator to assign the value `7` to the variable `x` and the expression evaluates to `7`

### Type 2

>`3 + 4` expression uses the `+` operator to add `3` and `4` together and produce a value of `7`

- However, unless it produces any side effects (e.g., is variable declaration, its result is discarded)
- Expressions are joined by *operators* (e.g., `+` and `=`)

## Why would we use a loop in our code?

Loops enable us to do something repeatedly (iterate)

## When does a `for` loop stop executing?

a `for` loop repeats until a specified condition evaluates to false

```js
for (intial value; conditional to evaluate; increment/decrement) {
execute this code;
}

for (let i = 0; i < 5; i++) {
console.log(i);
}
// for loop will execute until condition of 'i < 5' evaluates to false
```

## How many times will a `while` loop execute?

- a `while` loop will execute as long a specified condition evaluates to true
- if the condition becomes `false`, `statement` within the loop stops executing and control continues on to the statement following the loop
- The condition test occurs *before* `statement` in the loop is executed
- If the condition returns `true`, `statement` is executed and the `condition` is tested again
- If the condition returns `false`, execution stops, and control is passed to the statement following `while`

```js
while (condition)
  statement

let n = 0;
let x = 0;
while (n < 3) {
  n++;
  x += n;
}

// while loop will execute until n < 3 is no longer `true`
// 1: n = 1 and x = 1
// 2: n = 2 and x = 3
// 3: n = 3 and x = 6
// after 3rd pass, condition n < 3 is no longer `true`, so loop terminates

```
