# Class 01 Reading Notes: Introduction to React and Components

## Component-Based Architecture

source: [Component-Based Architecture](https://www.tutorialspoint.com/software_architecture_design/component_based_architecture.htm)

### What is a “component”?

- modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.
- a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities. It has an obviously defined interface and conforms to a recommended behavior common to all components within an architecture.
- A software component can be defined as a unit of composition with a contractually specified interface and explicit context dependencies only. That is, a software component can be deployed independently and is subject to composition by third parties.

### What are the characteristics of a component?

- **Reusability** − Components are usually designed to be reused in different situations in different applications. However, some components may be designed for a specific task.
- **Replaceable** − Components may be freely substituted with other similar components.
- **Not context specific** − Components are designed to operate in different environments and contexts.
- **Extensible** − A component can be extended from existing components to provide new behavior.
- **Encapsulated** − A component depicts the interfaces, which allow the caller to use its functionality, and do not expose details of the internal processes or any internal variables or state.
- **Independent** − Components are designed to have minimal dependencies on other components.

### What are the advantages of using component-based architecture?

- Reduced time in market and the development cost by reusing existing components.
- Increased reliability with the reuse of the existing components.

## Props

reference: [What is Props and How to Use it in React](https://itnext.io/what-is-props-and-how-to-use-it-in-react-da307f500da0#:~:text=%E2%80%9CProps%E2%80%9D%20is%20a%20special%20keyword,way%20from%20parent%20to%20child)

### What is “props” short for?

**“Props”** is a special keyword in React, which stands for **properties** and is being used for **passing data from one component to another**.

> Props are arguments passed into React components

### How are props used in React?

- Object to pass data between components
- Props data is 'read-only'

- Firstly, define an attribute and its value(data)
  - We can define our own attributes & assign values with **interpolation { }:**  `<ChildComponent someAttribute={value} anotherAttribute={value}/>`
  - Here I’m declaring a **“text”** attribute to the **ChildComponent** and then assign a string value: “**I’m the 1st child**”. `<ChildComponent text={“I’m the 1st child”} />`
  - Now the **ChildComponent** has a property and a value. Next, we need to pass it via **Props.**
- Then pass it to child component(s) by using Props
  - Passing props is very simple. Like we pass arguments to a function, we pass props into a React component and props bring all the necessary data.

```js
// Arguments passed to a function:
const addition = (firstNum, secondNum) => {  
  return firstNum + secondNum; 
};

// Arguments passed to a React component:
const ChildComponent = (props) => {  
  return <p>I'm the 1st child!</p>; 
};

```

- Finally, render the Props Data
  - so far, we have created an attribute and its value, then we passed it through props but we still can’t see it because we haven’t rendered it yet.
  - **A prop is an Object:** In the final step, we will render the props object by using string interpolation: `{props}`
  - In JavaScript, we can access object elements with dot(.) notation. So, let’s render our text property with an interpolation:

```js
const ChildComponent = (props) => {  
  return <p>{props.text}</p>; 
};
```

### What is the flow of props?

But the important part here is that data with props are being passed in a **uni-directional flow**. (one way from parent to child)
