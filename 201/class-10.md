# Class-10 Reading Notes: Debugging

## What Went Wrong? Troubleshooting JavaScript

*sources:* [What Went Wrong? Troubleshooting JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_went_wrong), chatGPT

### Name some key differences between a **Syntax Error** and a **Logic Error**

- **Syntax errors**: These are spelling errors in your code that actually cause the program not to run at all, or stop working part way through — you will usually be provided with some error messages too. These are usually okay to fix, as long as you are familiar with the right tools and know what the error messages mean!
  - syntax errors are related to the structure and grammar of the code and are detected by the interpreter during parsing, preventing the code from running
  - **Cause:** Syntax errors occur when there are violations of the JavaScript language's rules or conventions. These can include missing or mismatched parentheses, braces, or quotes, incorrect variable names, or improper usage of JavaScript keywords.
  - **Detection:** Syntax errors are detected by the JavaScript interpreter (the browser or Node.js environment) at the parsing stage before the code is executed. The interpreter can identify these errors because they violate the language's grammar rules.
  - **Result:** Code containing syntax errors cannot be executed until the errors are fixed. When a syntax error is encountered, the interpreter usually provides an error message that describes the issue and its location in the code.
  - **Example:** Missing closing parenthesis in a function call, like `console.log("Hello, world";)` instead of `console.log("Hello, world");`.
  
- **Logic errors**: These are errors where the syntax is actually correct but the code is not what you intended it to be, meaning that program runs successfully but gives incorrect results. These are often harder to fix than syntax errors, as there usually isn't an error message to direct you to the source of the error.
  - related to the program's behavior and are not detected by the interpreter. They may result in incorrect program output or behavior, and they require careful debugging to identify and correct.
  - **Cause:** Logic errors occur when the code is syntactically correct but does not produce the expected or desired result due to a mistake in the algorithm or the logic of the program. These errors can include incorrect calculations, wrong conditions, or improper data manipulation.
  - **Detection:** Logic errors are more challenging to detect because the code runs without any error messages. The program executes, but it produces an outcome that is different from what the programmer intended.
  - **Result:** Logic errors can lead to unexpected and incorrect behavior in your program. They may require debugging techniques, such as code inspection and testing, to identify and fix the problem.
  - **Example:** Adding instead of subtracting numbers in a calculation or using the wrong condition in an `if` statement that leads to unexpected branching.

### List a few types of errors that you have encountered in past lab assignments and explain how you were able to correct them

- variable is `undefined` - it was being referred to in the wrong scope and therefore could not be accessed. fixed it by putting the variable in the appropriate scope (e.g., global)

### How will this topic continue to influence your long term goals?

- being able to detect bugs early and often (in my code but in others' code as well) will be critical to my long-term developer goals. it allows you to fix issues and move on to productive works such as building new features

## The JavaScript Depugger

*sources:* [The JavaScript Debugger](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools#the_javascript_debugger), chatGPT

### How would you describe the JavaScript Debugger tool and how it works to someone just starting out in software development?

The JavaScript Debugger is a crucial tool for software development that helps identify and fix code issues. It allows developers to pause the execution of their JavaScript code, inspect variables, and step through code lines to understand how it works. Beginners can set breakpoints at specific lines to examine data, locate errors, and gain insights into program flow. By running code in a step-by-step manner, developers can identify and resolve bugs and ensure their applications function as intended. The Debugger empowers developers to enhance code quality, making it an invaluable aid for those learning and practicing software development

### Define what a breakpoint is

- A breakpoint is a designated point in a program's source code where execution is *intentionally paused or halted during debugging*. 
- It allows developers to inspect the program's current state, including variable values and execution flow, and analyze how the code behaves up to that point.
- Breakpoints are a vital tool for debugging because they help identify and diagnose issues in the code. Developers can set breakpoints at specific lines or functions in their code to gain insights into program behavior and track down errors. When a breakpoint is encountered, the debugging tool allows step-by-step execution and inspection of the program's internal state.

### What is the call stack?

The **Call stack** section shows you what code was executed to get to the current line. You can see that the code is in the function that handles a mouse click, and that the code is currently paused on the breakpoint.
