# Dive into REACT


Reference: [A High Level Overview Of React](https://www.youtube.com/watch?v=FRjlF74_EZk), chatGPT

## What is React?

- user interface library
- agnostic user interface **library**
  - React is a JavaScript library for building user interfaces, and it follows a component-based architecture
  - a React Element is NOT a DOM element (until passed through React DOM)
  - usually used on conjunction with other companion libraries
- component architecture
- one way data flow (vs. two way binding)
- component state - single part of user interface have state that can be shared with others

## What is a component?

- component architecture
- Component is a reusable, self-contained piece of code that represents a part of a user interface (UI). React is a JavaScript library for building user interfaces, and it follows a component-based architecture. Components can be thought of as **building blocks** that encapsulate the structure, behavior, and style of different parts of a web application.
- Components can be composed together to form the complete UI of an application. They promote reusability, maintainability, and a modular structure in your codebase. Components can also accept data through props and communicate with each other through callbacks and a unidirectional data flow.
- **Functional Components:** These are stateless components that are just JavaScript functions. They take in props (short for properties) as arguments and return React elements, which describe what should be rendered on the UI. With the introduction of React Hooks in React 16.8, functional components can also manage local state and side effects. 

```js
import React from 'react';

const MyFunctionalComponent = (props) => {
  return <div>Hello, {props.name}!</div>;
};

export default MyFunctionalComponent;

```

- **Class Components:** These are ES6 classes that extend from `React.Component`. Class components have a `render` method that returns React elements, and they can also have local state and lifecycle methods.

```js
import React, { Component } from 'react';

class MyClassComponent extends Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
}

export default MyClassComponent;

```

## What is the dataflow of React?

- data flows down one way through a React app (unidirectional)
- The basic idea is that data changes originate from a single source of truth, typically the component that manages that data, and then flow down through the component tree to the child components.
- state exists at a component level and is passed down

1. **State:** Data starts in a component's state. State is essentially an object that represents the current condition of the component. It's mutable and can be changed by the component that owns it.

1. **Props:** The state data is then passed down to child components as props (short for properties). Props are immutable and are used to pass data from parent components to their children. Child components can't directly modify the props they receive.
2.**Render:** Components render based on their props and state. The `render` method of a component describes what the UI should look like based on the current state and props.
3. **User Interaction:** When a user interacts with the UI, events are triggered (e.g., button clicks, form submissions). These events typically lead to changes in the component's state.
4. **State Update:** When the component's state changes, React re-renders the component, updating the UI to reflect the new state.
5. **Child Components:** If the state change affects props passed down to child components, the changes propagate down the component tree. This can trigger re-renders in those child components, and the process repeats.

## How do we make a React element a DOM element?

- In React, the process of turning a React element into a DOM element involves rendering the React element to the actual DOM. React provides a method for rendering elements into the DOM, and this is typically done using the `ReactDOM.render()` function.
- First, you need to include the necessary dependencies in your project. In a typical React application, you would have React and ReactDOM included, and you might install them using npm or yarn:

```bash
npm install react react-dom
```

- Once you have the dependencies, you can use them in your code. In this example:
  - The `myElement` variable is a React element representing an `<h1>` element with the text "Hello, World!".
  - The `ReactDOM.render()` function takes two arguments:
	- The React element (`myElement` in this case) that you want to render.
	- The DOM container where you want to render the element. In this example, the `document.getElementById('root')` selects an HTML element with the id of 'root'.

```js
import React from 'react';
import ReactDOM from 'react-dom';

// Define a React element
const myElement = <h1>Hello, World!</h1>;

// Render the React element into the DOM
ReactDOM.render(myElement, document.getElementById('root'));

```

- Make sure you have an HTML element with the specified id in your HTML file. For example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>React DOM Example</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>

```

- When you run this code, React will take care of updating the DOM to match the specified React element. The text "Hello, World!" will be rendered inside the `<div>` with the id of 'root'.

## React is a User Interface **`Library`**

- its primary purpose is to facilitate the creation and management of user interfaces (UI) in web applications
- React provides a set of tools and abstractions for efficiently building and managing the user interface of a web application. React helps developers create UI components, manage the state of those components, and efficiently update the UI in response to user interactions or changes in data.

1. **User Interface (UI):** The UI is the visual part of a software application that users interact with. It includes components like buttons, forms, text fields, and other elements that users see and interact with on a webpage.
2. **Library:** React is described as a library rather than a framework. In the context of software development, a library is a collection of pre-written code that provides common functionalities and can be used by developers to achieve specific tasks. React focuses on a specific aspect of development—building user interfaces—while allowing developers the flexibility to integrate it into existing projects or use it alongside other libraries.

## Which direction does data flow in React?

- The parent component is the source of truth for the data, and it passes that truth down to its children, creating a hierarchical and predictable flow of information.

## Every component manages its own **`state`**

- The state is a JavaScript object that represents the current conditions or data of the component. The state is mutable, meaning it can be changed over time in response to user actions, network responses, or other factors.
- Whether using functional components with hooks or class components, each component maintains its own state, allowing it to manage and respond to changes independently of other components.

### **Functional Components with Hooks:**

- Functional components can now manage state by using the `useState` hook.
- The `useState` hook returns an array with two elements: the current state value and a function that allows you to update the state.

```js
import React, { useState } from 'react';

const MyComponent = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
};

```

### **Class Components:**

- Class components use the `setState` method to update their state.
- The `setState` method takes an object that describes the changes to be made to the state.

```js
import React, { Component } from 'react';

class MyClassComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}

```
