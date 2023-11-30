# Class-04 Reading Notes: React & Forms

source: [How to use Forms in React](https://www.robinwieruch.de/react-form/), chatGPT

## What is a ‘Controlled Component’?

- form element (like an input or textarea) whose value is controlled by the React component's state. In other words, the component's state is the single source of truth for the value of the form element. The component's state is updated in response to user input, and the value of the form element is always set explicitly through the component's state.
- By maintaining control over the input value through the component's state, React can manage the state of the form elements and ensure that the user interface reflects the current state of the application. This is particularly useful for handling form submissions, validation, and other interactions in a React application.

```jsx
import React, { useState } from 'react';

const ControlledComponentExample = () => {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      <label htmlFor="controlledInput">Type something:</label>
      <input
        type="text"
        id="controlledInput"
        value={inputValue}
        onChange={handleChange}
      />
      <p>You typed: {inputValue}</p>
    </div>
  );
};

export default ControlledComponentExample;

```

- The `inputValue` state variable holds the value of the input field.
- The `handleChange` function is called whenever the input field changes. It updates the `inputValue` state with the new value.
- The value of the input field is set to the `inputValue` state, making it a controlled component.

## Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why?

Whether to store user responses in the state as they type or wait until they submit the form depends on the requirements of your application and the user experience you want to provide. Both approaches have their merits, and the decision may be influenced by factors such as form complexity, user feedback, and performance considerations. Here are some considerations for both approaches:

### Store as they type

1. **Real-time feedback:** Storing responses in the state as users type allows you to provide real-time feedback or validation. For example, you can instantly show error messages, perform live character count validation, or enable/disable certain features based on input.
2. **Enhanced user experience:** Users may appreciate seeing immediate feedback, and it can help catch and correct errors early in the process.
3. **Progress tracking:** If the form is lengthy or has multiple sections, storing responses as they type can help track the user's progress and provide a sense of completion.

### Wait until form submission

1. **Reduced state updates:** Storing responses only on form submission can reduce the number of state updates and potentially improve performance, especially in complex forms with many inputs.
2. **Simplified logic:** Waiting until submission can simplify the logic in your component. You only need to update the state once, and you can handle validation and other actions at the form level.
3. **Avoid unnecessary re-renders:** If your form has many fields and complex validation, updating the state on every keystroke might lead to unnecessary re-renders. In such cases, you might prefer to validate and update the state only when the user submits the form.

## How do we target what the user is entering if we have an event handler on an input field?

when you have an event handler on an input field, you can access the user's input through the `event` object that is passed to the event handler function. The user's input can be obtained from the `value` property of the input field. Here's an example:

```jsx
import React, { useState } from 'react';

const MyForm = () => {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    // Access the user's input from the event object
    const userInput = event.target.value;

    // Update the state with the user's input
    setInputValue(userInput);
  };

  return (
    <div>
      {/* Input field with the event handler */}
      <input
        type="text"
        value={inputValue}
        onChange={handleChange}
      />

      {/* Display the user's input (for demonstration purposes) */}
      <p>User entered: {inputValue}</p>
    </div>
  );
};

export default MyForm;

```

- The `handleChange` function is the event handler for the `onChange` event of the input field.
- The `event` parameter in the `handleChange` function is automatically provided by React.
- `event.target` refers to the element that triggered the event (in this case, the input field).
- `event.target.value` gives you the current value of the input field, which is the user's input.

>By accessing `event.target.value`, you can obtain the user's input and use it as needed, such as updating the component's state, performing validation, or sending it to a server.


source: [The Conditional (Ternary) Operator Explained](https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff), chatGPT

## Why would we use a ternary operator?

concise way to write simple conditional statements in a single line. It takes three operands and returns a value based on the evaluation of a condition. The general syntax is:

```js
// Without ternary operator
let result;
if (condition) {
  result = 'Value for true';
} else {
  result = 'Value for false';
}

// With ternary operator
let result = condition ? 'Value for true' : 'Value for false';

```

**Conciseness and Readability:**

- Ternary operators are concise and can make your code more readable, especially for simple conditions.
- They are often used when the true/false expressions are short and don't involve complex logic.

**Inline Conditionals:**

- Ternary operators are useful for inline conditionals within JSX or string templates.

**Assignment in a Single Line:**

- Ternary operators allow you to perform conditional assignment in a concise manner.

**Returning Values:**

- Ternary operators are often used when a value needs to be conditionally returned from a function or a block of code.

**Avoiding Repetition:**

- If you have a simple condition that needs to be checked in multiple places, a ternary operator can help avoid code repetition.

## Rewrite the following statement using a ternary statement:

```js
// if statement
   if(x===y){
      console.log(true);
    } else {
      console.log(false);
    }
// ternary operator
(x === y) ? console.log(true) : console.log(false);
```
