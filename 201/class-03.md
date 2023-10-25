# Class-03 Reading Notes: HTML Lists, Control Flow with JS, and the CSS Box Model

## When should you use an `unordered list` in your HTML document?

- grouping a collection of items that do not have a numerical ordering, and their order in the list is meaningless. Typically, unordered-list items are displayed with a bullet

## How do you change the `bullet style` of unordered list items?

- update the associated CSS using the `list-style-type` property

_source:_ [Unordered lists](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul)

## When should you use an `ordered list` vs an `unorder list` in your HTML document?

- use an `ordered list` when the order of the list has meaning (e.g., steps in a recipe, turn-by-turn directions, list of ingredients in decreasing proportion)
- ordered list items display with a preceding marker, such as a number or letter.

_source:_ [Ordered lists](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol)

## Describe two ways you can change the numbers on `list items` provided by an `ordered list`

- Use Roman Numeral type by changing `<ol type="i">`
- Use the start attribute by changing `<ol start="4">` - in this example the list will start at 4

*source:* [Ordered lists](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol)

## Describe the CSS properties of `margin` and `padding` as characters in a story. What is their role in a story titled: “The Box Model”?

```ai
Margin introduced the Box to the world, creating space for it to shine, while Padding embraced the Box with its gentle padding. They worked together to create a balance of visibility and protection.
```

*source:* Open AI playground

## List and describe the **four** parts of an HTML elements box as referred to by the `box model`

- `content` box is the area where your content is displayed
  - size it using properties like `inline-size` and `block-size` or `width` and `height`.
- `padding` sits around the content as white space
  - size it using `padding` and related properties
- `border` box wraps the content and any padding
  - size it using border and related properties
- `margin` box is the outermost layer of the box model, wrapping the content, padding and border as whitespace between this box and the other elements
  - size it using `margin` and related properties

![Box Model](box-model.png)

> In the **standard box model**, if you give a box an `inline-size` and a `block-size` (or `width` and a `height`) attributes, this defines the inline-size and block-size (width and height in horizontal languages) of the *content box*. Any padding and border is then added to those dimensions to get the total size taken up by the box

*source:* [The Box Model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)

## What `data types` can you store inside of an `Array`?

- strings, numbers, objects, and even other arrays
- We can also mix data types in a single array

## Is the `people` array a valid JavaScript array? If so, how can I access the values stored? If not, why?

- Yes, it's an array of arrays, where each inner array represents information about a person
- to access the values stored by using array indexing (see below)
To access the first person's name (Pete), you would use `people[0][0]`.

    ```js
     const people = [['pete', 32, 'librarian', null], ['Smith', 40, 'accountant', 'fishing:hiking:rock_climbing'], ['bill', null, 'artist', null]];
    ```

*sources:* [Arrays(MDN)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Arrays); chatGPT

## List **five** shorthand operators for assignment in javascript and describe what they do

- Assignment - The **assignment (`=`)** operator is used to assign a value to a variable or property. The assignment expression itself has a value, which is the assigned value.
- The **addition assignment (`+=`)** operator performs [addition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Addition) (which is either numeric addition or string concatenation) on the two operands and assigns the result to the left operand.
- The **subtraction assignment (`-=`)** operator performs [subtraction](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Subtraction) on the two operands and assigns the result to the left operand.
- The **multiplication assignment (`*=`)** operator performs [multiplication](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Multiplication) on the two operands and assigns the result to the left operand.
- The **remainder assignment (`%=`)** operator performs [remainder](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Remainder) on the two operands and assigns the result to the left operand.

*source:* [Expressions and operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#assignment_operators)

## Read the code below and evaluate the last `expression` and explain what the result would be and why

- the below will first evaluate `a + c` since it's in the parentheses
- `10 + false` - since `a` is a number and `c` is a boolean, JavaScript will try to convert `c` to a number; `false` is treated as `0`, therefore `10 + false` returns `10`
- next, it will evaluate `10 + b,` which is `10 + `'dog'`
- the `+` will concatenate since there is a string involved, resulting in `10dog`

    ```js
     let a = 10;
     let b = 'dog';
     let c = false;
    
     // evaluate this
     (a + c) + b;
    ```

*source:* chatGPT

## Describe a real world example of when a conditional statement should be used in a JavaScript program

A real world example of a conditional statement being used in a JavaScript program is validating a user input. If the user input does not meet some criteria, the JavaScript can return an error message to the user asking them for a correction.

## Give an example of when a `Loop` is useful in JavaScript

A loop can be useful to run code multiple times until a condition is met. For example, in the example above a `while` loop can run to prompt the user for corrections until the valid condition is met on the user input criteria
