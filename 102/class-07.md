# Class-07 Reading Notes: Programming with JavaScript

## What is `control flow`?

- Order in which the computer executes statements in a script
- Code is run in order from the first line in the file to the last line, unless it runs across the  structures that change the control flow (e.g. conditionals and loops)

## What is a JavaScript `function`?

- Set of statements that performs a task or calculates a value
- A `function` takes some input and returns an output (where there is some obvious relationship between the input and the output
- To use a `function`, you must define (`declare`) it somewhere in the scope from which you wish to call it

### Basic order of operations

- Step 1: `declare` (define) a function, which outlines the parameters and instructions
- Step 2: `invoke` or `call` (execute) a function

## What does it mean to `invoke` - or `call` - a function?

A function is *executed* when something `invokes` (`calls`) it

- When an event occurs (e.g., when a user clicks a button)
- When it is invoked (called) from JavaScript code
- Automatically (self invoked)

## What are the parenthesis `()` for when you define a function?

### The () operator invokes (calls) the function

```js
function toCelsius(f) {
  return (5/9) * (f-32);
}

let value = toCelsius(77);

// 25
```

### Accessing a function with incorrect parameters can return an incorrect answer:

```js
function toCelsius(f) {
  return (5/9) * (f-32);
}

let value = toCelsius();

//NaN
```

### Accessing a function without () returns the function and not the function result

```js
function toCelsius(f) {
  return (5/9) * (f-32);
}

let value = toCelsius;

// function toCelsius(f) { return (5/9) * (f-32); }
```
