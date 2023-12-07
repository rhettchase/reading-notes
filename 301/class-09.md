# Class-09 Reading Notes: Functional Programming

source: [Functional Programming Concepts](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa), chatGPT

1. **What is functional programming?**

    Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing state and mutable data. In functional programming, functions are first-class citizens, meaning they can be assigned to variables, passed as arguments, and returned as values. Key concepts in functional programming include immutability, pure functions, and higher-order functions.
    
2. **What is a pure function and how do we know if something is a pure function?**
    
    A pure function is a function that satisfies two main criteria:
    
    - It returns the same result if given the same arguments (deterministic).
    - It does not cause any observable side effects.
    
    To determine if a function is pure:
    
    - Check if it relies on external state or mutable data.
    - Verify that it consistently returns the same result for the same input.
    - Ensure it doesn't cause side effects, such as modifying global objects or performing I/O operations.
    
1. **What are the benefits of a pure function?**
    
    The benefits of pure functions include:
    
    - **Predictability:** Given the same inputs, a pure function will always produce the same output.
    - **Testability:** Pure functions are easy to test since they don't rely on external state or produce side effects.
    - **Reasoning:** Pure functions are easier to reason about, making code more understandable and maintainable.
    - **Concurrency:** Pure functions facilitate parallel and concurrent programming, as they don't depend on shared mutable state.
4. **What is immutability?**
    
    Immutability refers to the concept that once an object is created, its state cannot be changed. In functional programming, immutability is encouraged to create more predictable and safer code. Instead of modifying existing data structures, immutability involves creating new objects with the desired changes.
    
5. **What is Referential transparency?**
    
    Referential transparency is a property of functions in which a function's output is solely determined by its inputs, and calling the function with the same inputs always yields the same result. In other words, a referentially transparent function can be replaced with its result without affecting the program's behavior. This property is closely related to the concept of pure functions.

## Videos

source: [Node JS Tutorial for Beginners #6 - Modules and require()](https://www.youtube.com/watch?v=xHLd36QoS4k), chatGPT

1. **What is a module in Node.js?**
    
    In Node.js, a module is a separate file that encapsulates a set of related functionality, making it reusable and maintainable. Each file in Node.js is treated as a module, and the code within a module is scoped to that module by default. Modules in Node.js can include functions, variables, and objects that can be exported and imported across different parts of a Node.js application.
    
2. **What does the word ‘require’ do in Node.js?**
    
    In Node.js, the `require` function is used to include and import external modules into the current file. When you use `require('module-name')`, Node.js searches for a module with the specified name and loads it into the current file. The loaded module becomes an object that contains the exported functionality, and you can assign it to a variable for use within your application.
    
3. **How do we bring another module into the file that we are working in in Node.js?**
    
    To bring another module into the file you are working in Node.js, you use the `require` statement. For example:
    
    javascriptCopy code
    
    `const moduleName = require('./path/to/module');`
    
    The path can be relative (as shown) or an absolute path, and it specifies the location of the module file. The `moduleName` variable then becomes a reference to the exported functionality of the specified module.

4. **What do we have to do to make a module available in Node.js?**

    To make a module available for use in Node.js, you need to export the functions, variables, or objects that you want to expose. This is typically done using the `module.exports` or `exports` object. For example:

```js
// module.js
const myFunction = () => {
  // function implementation
};

module.exports = myFunction;

```

In another file, you can use:

```js
   // anotherFile.js
const myFunction = require('./module');

// Now you can use myFunction in this file

```

Exporting makes the specified functionality available for import in other modules within your Node.js application.