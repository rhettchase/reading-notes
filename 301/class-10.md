# Class-10 Reading Notes: In Memory Storage & Errors

## In Memory Storage

source: [Understanding the JavaScript Call Stack](https://medium.freecodecamp.org/understanding-the-javascript-call-stack-861e41ae61d4), chatGPT

1. **What is a ‘call’?**

    In JavaScript, a 'call' refers to the invocation of a function. When a function is called, it gets added to the call stack, and its execution begins. The call includes pushing the function and its parameters onto the call stack.

2. **How many ‘calls’ can happen at once?**

    In JavaScript, only one call can happen at a time. The language is single-threaded, and the call stack processes function calls synchronously, following the Last In, First Out (LIFO) principle.

3. **What does LIFO mean?**

    LIFO stands for Last In, First Out. In the context of the call stack, it means that the last function that is pushed onto the stack is the first one to be popped off and executed. This follows a stack data structure where the last item added is the first one removed.

4. **Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.**

```md
| thirdFunction |
| secondFunction|
| firstFunction  |
|_______________|

```

The call stack is populated in the order: `thirdFunction` calls `secondFunction`, which in turn calls `firstFunction`. The functions are stacked in the order they are invoked, and they are popped off in reverse order when their execution is completed.

5. **What causes a Stack Overflow?**

    A Stack Overflow occurs when there is a recursive function (a function that calls itself) without a proper exit condition. The call stack keeps growing with each recursive call until it reaches its maximum size, at which point the browser throws a "Maximum call size exceeded" error. In the given example, the `callMyself` function calls itself indefinitely without a base case, leading to a stack overflow.

## Error Messages

source: [JavaScript error messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c), chat GPT

### What is a ‘reference error’?

A 'ReferenceError' occurs when you try to use a variable that has not been declared. For example:

```js
console.log(foo); // Uncaught ReferenceError: foo is not defined

```

### What is a ‘syntax error’?

A 'SyntaxError' occurs when there is a mistake in the structure of your code that prevents it from being parsed correctly. For example:

```js
JSON.parse( {'foo': 'bar'} ); // Uncaught SyntaxError: Unexpected token o in JSON at position 1
// In this case, the object should be a valid JSON string enclosed in double quotes.
```

### What is a ‘range error’?

A 'RangeError' occurs when you manipulate an object with some kind of length and give it an invalid length. For example:

```js
var foo = [];
foo.length = foo.length - 1; // Uncaught RangeError: Invalid array length
// In this case, trying to set a negative length for an array results in a 'RangeError'.
```

### What is a ‘type error’?

A 'TypeError' occurs when the types (number, string, etc.) you are trying to use or access are incompatible. For example:

```js
var foo = {};
foo.bar.baz; // Uncaught TypeError: Cannot read property 'baz' of undefined
// Here, the error is thrown because `foo.bar` is undefined, and you cannot access the property 'baz' of undefined.
```

### What is a breakpoint?

A 'breakpoint' is a point in your code where the execution will pause, allowing you to inspect the state of your program at that moment. It's a tool used during debugging to analyze variables, check the call stack, and step through code one line at a time.

### What does the word ‘debugger’ do in your code?

The 'debugger' statement is used to set a breakpoint in your code. When the browser encounters the 'debugger' statement, it will pause execution at that point, giving you the opportunity to inspect the current state of variables and step through your code. It's a powerful tool for identifying and fixing issues in your JavaScript programs.
