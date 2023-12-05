# Class-07 Reading Notes: Node.JS

## Node.js

source: [An Introduction to Node.js on sitepoint.com](https://www.sitepoint.com/an-introduction-to-node-js), chatGPT

### What is node.js?

Node.js is a runtime environment that allows developers to run JavaScript on servers instead of just in web browsers. It enables the creation of dynamic and scalable web applications by allowing server-side execution of JavaScript code, which was traditionally limited to client-side scripting in web browsers. This helps in building fast and efficient applications, making it a popular choice for web development.

### In your own words, what is Chrome’s V8 JavaScript Engine?

Chrome's V8 JavaScript Engine is an open-source JavaScript engine developed by the Chromium project for the Google Chrome web browser. It's also used in other browsers like Microsoft Edge and various server-side environments via Node.js. The V8 engine is responsible for executing JavaScript code in the browser or server environment. It employs just-in-time (JIT) compilation to translate JavaScript code into machine code for faster execution. V8 is known for its high performance and efficiency, contributing to the speed and responsiveness of modern web applications.

### What does it mean that node is a JavaScript runtime?

When we say that Node.js is a JavaScript runtime, it means that Node.js provides an environment for executing JavaScript code outside of a web browser. Traditionally, JavaScript was primarily used for client-side scripting within web browsers. However, Node.js extends the use of JavaScript to the server-side.

As a JavaScript runtime, Node.js includes a set of tools and libraries that allow you to execute JavaScript code on a server, enabling the development of server-side applications. It includes the V8 JavaScript engine (the same engine used by Google Chrome) to interpret and execute JavaScript code efficiently. Node.js facilitates tasks such as file system operations, networking, and other server-related functionalities, making it possible to build scalable and high-performance server applications using JavaScript.

### What is npm?

package manager that comes bundled with Node

### What version of node are you running on your machine?

`v21.2.0`

### What version of npm are you running on your machine?

`10.2.3`

### What command would you type to install a library/package called ‘jshint’?

`npm install -g jshint`
This command installs 'jshint' globally (`-g` flag), making it accessible as a command-line tool throughout your system. If you prefer to install it locally for a specific project, you can omit the `-g` flag.

### What is node used for?

can be used for anything from bundling your JavaScript files and dependencies into static assets, to running tests, or automatic code linting and style checking.

[6 Reasons for Pair Programming](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)

1. What are the 6 reasons for pair programming?

- Greater efficiency
- work environment readiness
- Engaged collaboration
- Learning from others
- social skills
- Job interview readiness

1. In your experience, which of these reasons have you found most beneficial?

-  Greater efficiency - while pair programming may take slightly longer, it produces higher-quality code that requires less troubleshooting and debugging. I think this makes sense, since the code must be clear from multiple perspectives and you have another person working through bugs and creative problem solving together
- work environment readiness - since many companies utilize pair programming for building a project or feature, or debugging an existing code base, learning pair programming in training is good practice
2. How does pair programming work?

- Driver and Navigator
- Driver is the one with their hands on the keyboard
- Navigator is talking through the code with the Driver and helping to research