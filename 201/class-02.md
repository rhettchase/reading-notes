# Class-02 Reading Notes: Basics of HTML, CSS & JS

## Introduction to HTML (cont'd)

### Why is it important to use semantic elements in our HTML?

- by using the correct semantic elements, it gives content the correct meaning, function, or appearance
- using semantic elements helps to give text meaning, so that the browser knows how to display it correctly

*source:* [Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)

### How many levels of headings are there in HTML?

- There are 6 levels of headings in HTML
- These are used to define the structure and hierarchy of a web page's content

### What are some uses for the `<sup>` and `<sub>` elements?

- `<sup>` is used to superscript text; uses include:
  - dates - example: 13th of March `13<sup>th</sup> of March`
  - mathematical equations - example: x<sup>2</sup> `x<sup>2</sup>`
- `<sub>` is used to subscript text; uses include:
  - C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub> => `C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>`

*source:* [HTML Advanced Text Formatting](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting).

### When using the `<abbr>` element, what attribute must be added to provide the full expansion of the term?

- used to wrap around an abbreviation or acronym. 
- When including either, provide a full expansion of the term in plain text on first use

```html
We use <abbr>HTML</abbr>, Hypertext Markup Language, to structure our web documents.
```

*source:* [HTML Advanced Text Formatting](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting).

## Learn CSS

### What are ways we can apply CSS to our HTML?

- **external stylesheet**
  - An external stylesheet contains CSS in a separate file with a .css extension.
  - using an external stylesheet is best practice
  - You can link a single CSS file to multiple web pages, styling all of them with the same CSS stylesheet.

```html
  <head>
    <meta charset="utf-8" />
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
```

- **internal stylesheet**
  - An internal stylesheet resides within an HTML document. 
  - To create an internal stylesheet, you place CSS inside a `<style>` element contained inside the HTML `<head>`.
  
- **inline styles**
  - Inline styles are CSS declarations that affect a single HTML element, contained within a style attribute

```html
<h1 style="color: blue;background-color: yellow;border: 1px solid black;">
      Hello World!
    </h1>
```

*source:* [How CSS Is Structured](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured).

### Why should we avoid using inline styles?

- least efficient implementation of CSS for maintenance -- one styling change might require multiple edits within a single web page.
- mixes (CSS) presentational code with HTML and content, making everything more difficult to read and understand.
  - Separating code and content makes maintenance easier for all who work on the website.

*source:* [How CSS is Structured](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured)

### Review the block of code below and answer the following questions

#### What is representing the selector?

- h2 is representing the selector
- the selector targets HTML to apply styles to content
- The element or elements which are selected by the selector are referred to as the subject of the selector

#### Which components are the CSS declarations?

- When a property is paired with a value, this pairing is called a CSS declaration. CSS declarations are found within CSS Declaration Blocks
- In the example below, the `color: black;` and `padding: 5px;` are the declarations

#### Which components are considered properties?

- Properties: identifiers that indicate which stylistic features you want to modify. For example, font-size, width, background-color.
- In the example below, `color` and `padding` are the properties

```html
   h2 {
     color: black;
     padding: 5px;
   }
```

## Learn JS

### What data type is a sequence of text enclosed in single quote marks?

string

### List 4 types of JavaScript operators

**Arithmetic operators** - used to perform mathematical operations, examples below:

- `+` is the `addition` operator - adds two numbers together or combines two strings
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `%` (Modulo, returns the remainder after division)
- `++` (Increment by 1)
- `--` (Decrement by 1)

**Comparison operators** - used to compare values and return a Boolean result (true or false), examples below:

- `==` (Equal to)
- `!=` (Not equal to)
- `===` (Strictly equal to, compares both value and data type)
- `!==` (Strictly not equal to, compares both value and data type)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

**Logical operators** - used to combine or manipulate Boolean values, examples below:

- `&&` (Logical AND, returns true if both operands are true)
- `||` (Logical OR, returns true if at least one operand is true)
- `!` (Logical NOT, negates the value, true becomes false and vice versa)

**Assignment operators** - used to assign values to variables, examples below:

- `=` is the assignment operator - this assigns a value to a variable
- - `+=` (Add and assign, adds the right value to the variable and assigns the result)
- `-=` (Subtract and assign)
- `*=` (Multiply and assign)
- `/=` (Divide and assign)
- `%=` (Modulo and assign)

*sources:* [JavaScript Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics), ChatGPT

### Describe a real world Problem you could solve with a Function.

- you could create a function to convert the currency from USD to Euros

```js
function conversion (usd) {
let result = usd * 0.94;
return result;
}
```

[Making Decisions In Your Code – Conditionals](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals).

### An if statement checks a **__** and if it evaluates to **__**_, then the code block will execute.

- checks a condition
- if it evaluates to true, then the code block will execute

### What is the use of an `else if`?

- can be used to chain extra choices/outcomes by checking multiple conditions in a sequence and execute different blocks of code depending on which condition it evaluates as true

- `else if` is used when more than two possible outcomes are possible, which makes it a good tool for handling complex decision-making 

```js
if (condition1) {
  // Code to be executed if condition1 is true
} else if (condition2) {
  // Code to be executed if condition2 is true
} else if (condition3) {
  // Code to be executed if condition3 is true
} else {
  // Code to be executed if none of the above conditions are true
}

```

*sources:* [Making decisions in your code - conditionals](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals), ChaptGPT

### List 3 different types of comparison operators.

Comparison operators are used to test the conditions inside our conditional statements. Three different types are:

- **Equality operators**
  - `===` and `!==` — test if one value is identical to, or not identical to, another.
- **Relational Operators**
  - `<` and `>` — test if one value is less than or greater than another.
  - `<=` and `>=` — test if one value is less than or equal to, or greater than or equal to, another.
- **Logical operators** (used for combining and modifying conditions):
  - `&&` (Logical AND): Returns true if both conditions on the left and right are true.
  - `||` (Logical OR): Returns true if at least one of the conditions on the left or right is true.
  - `!` (Logical NOT): Negates the condition, turning true into false and vice versa.
  
*sources:* [Making decisions in your code - conditionals](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals), ChatGPT

### What is the difference between the logical operator `&&` and `||`?

- `&&` — AND; allows you to chain together two or more expressions so that all of them have to individually evaluate to `true` for the whole expression to return `true`.
- `||` — OR; allows you to chain together two or more expressions so that one or more of them have to individually evaluate to `true` for the whole expression to return `true`.

*source:* [Making decisions in your code - conditionals](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)