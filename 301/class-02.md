# Class-02 Reading Notes: State and Props

## Based off the diagram, what happens first, the ‘render’ or the ‘componentDidMount’?

Render phase

## What is the very first thing to happen in the lifecycle of React?

### Mounting Phase:

1. **constructor():**
    - Called before the component is mounted.
    - Initialize state and bind event handlers.
    - Avoid using `this.setState()` here.
2. **static getDerivedStateFromProps():**
    - Used for rare cases where state relies on changes in props over time.
3. **render():**
    - The only required method in a class component.
    - Examines `this.props` and `this.state`.
    - Should not modify the component state.
    - Will not be invoked if `shouldComponentUpdate()` returns false.
4. **componentDidMount():**
    - Invoked immediately after a component is mounted.
    - Used for network requests, DOM initialization, and setting up subscriptions.
    - `setState()` can be called here but should be used sparingly.

## Put the following things in the order that they happen: `componentDidMount`, `render`, `constructor`, `componentWillUnmount`, `React Updates`

1. **`constructor`:**
    - The constructor is called when a component is being initialized.
    - It is the first method called during the component's lifecycle.
2. **`render`:**
    - The `render` method is responsible for rendering the component's UI.
    - It is called after the `constructor`.
3. **`componentDidMount`:**
    - `componentDidMount` is called after the component has been rendered to the DOM.
    - It is commonly used for initial data fetching and setup.
4. **`React Updates` (e.g., `static getDerivedStateFromProps`, `shouldComponentUpdate`, `render`, `getSnapshotBeforeUpdate`, `componentDidUpdate`, etc.):**
    - These methods are part of the updating phase and are called when the component is being re-rendered due to changes in props or state.
5. **`componentWillUnmount`:**
    - `componentWillUnmount` is called just before a component is removed from the DOM.
    - It is used for cleanup tasks, such as canceling network requests or cleaning up subscriptions.

## What does `componentDidMount` do?

### **componentDidMount():**

- Invoked immediately after a component is mounted.
- Used for network requests, DOM initialization, and setting up subscriptions.
- `setState()` can be called here but should be used sparingly.