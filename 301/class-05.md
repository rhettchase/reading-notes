Class-05 Reading Notes: Thinking in React & Higher-order functions

source: [React Docs - Thinking in React](https://reactjs.org/docs/thinking-in-react.html)

### What is the `single responsibility principle` and how does it apply to components?

- component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents
- When applying the Single Responsibility Principle to React components, the idea is to design components in a way that each component has a single responsibility or concern. This helps in making the components more modular, reusable, and easier to maintain.

1. **Separation of Concerns:**
    - Each component should have a specific purpose or concern, such as handling data logic, rendering UI, or managing state.
    - Avoid mixing business logic with presentational logic. For example, separate data fetching or manipulation from the rendering of UI elements.
2. **Modularization:**
    - Break down complex components into smaller, more focused components that handle specific tasks.
    - Each component should ideally focus on doing one thing and doing it well.
3. **Reusable Components:**
    - Create components that can be reused across different parts of your application.
    - A well-designed component should be adaptable to various use cases without significant modifications.
4. **Container and Presentational Components:**
    - Adopt the concept of container components for managing state and data fetching, while presentational components focus on rendering UI based on props.
    - This helps in separating the concerns of data management and UI rendering.

```js
// Good example - following SRP
class UserProfile extends React.Component {
  render() {
    // Render user profile UI here
  }
}

class UserProfileContainer extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      user: null,
    };
  }

  componentDidMount() {
    // Fetch user data here
    // Update state with user data
  }

  render() {
    // Pass user data as props to UserProfile component
    return <UserProfile user={this.state.user} />;
  }
}

```

##  What does it mean to build a ‘static’ version of your application?

- Build it first without interactivity
- To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. 
- Props are a way of passing data from parent to child. (
- If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.

## Once you have a static application, what do you need to add?

- Find the minimal but complete representation of UI state
- Think of state as the minimal set of changing data that your app needs to remember. The most important principle for structuring state is to keep it DRY (Don’t Repeat Yourself). 
- Figure out the absolute minimal representation of the state your application needs and compute everything else on-demand.

##  What are the three questions you can ask to determine if something is state?

- Does it **remain unchanged** over time? If so, it isn’t state.
- Is it **passed in from a parent** via props? If so, it isn’t state.
- **Can you compute it** based on existing state or props in your component? If so, it _definitely_ isn’t state!

**What’s left is probably state.**

## How can you identify where state needs to live?

you need to identify which component is responsible for changing this state, or _owns_ the state. Remember: React uses **one-way data flow,** passing data down the component hierarchy from parent to child component. 

For each piece of state in your application:

1. Identify _every_ component that renders something based on that state.
2. Find their closest common parent component—a component above them all in the hierarchy.
3. Decide where the state should live:
    1. Often, you can put the state directly into their common parent.
    2. You can also put the state into some component above their common parent.
    3. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common parent component.

[Higher-Order Functions](https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK)

## What is a “higher-order function”?

- Functions that operate on other functions, either by taking them as arguments or by returning them, are called _higher-order functions_.
- allow us to abstract over _actions_, not just values. They come in several forms
  - functions that create new functions (see `greaterthan()` below)
  - functions that change other functions

```js
  function noisy(f) {
  return (...args) => {
    console.log("calling with", args);
    let result = f(...args);
    console.log("called with", args, ", returned", result);
    return result;
  };
}
noisy(Math.min)(3, 2, 1);
// → calling with [3, 2, 1]
// → called with [3, 2, 1] , returned 1

```

  - functions that provide new types of control flow

```js
  function unless(test, then) {
  if (!test) then();
}

repeat(3, n => {
  unless(n % 2 == 1, () => {
    console.log(n, "is even");
  });
});
// → 0 is even
// → 2 is even
```

  -  built-in array method, `forEach`, that provides something like a `for`/`of` loop as a higher-order function.

## Explore the `greaterThan` function as defined in the reading. In your own words, what is line 2 of this function doing?

- takes a parameter `m` and checks whether `m` is greater than the initially provided value `n`.
- line 2 is creating a closure that "remembers" the value of `n` (in this case, 10) and returns a function that checks if a given value is greater than that remembered `n`.

```js
  function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// → true
```

## Explain how either `map` or `reduce` operates, with regards to higher-order functions

- `Reduce` builds a value by repeatedly taking a single element from the array and combining it with the current value. When summing numbers, you’d start with the number zero and, for each element, add that to the sum.
- The parameters to `reduce` are, apart from the array, a combining function and a start value.

```js
function reduce(array, combine, start) {
  let current = start;
  for (let element of array) {
    current = combine(current, element);
  }
  return current;
}

console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0));
// → 10

```

The standard array method `reduce`, which of course corresponds to this function, has an added convenience. If your array contains at least one element, you are allowed to leave off the `start` argument. The method will take the first element of the array as its start value and start reducing at the second element.

```js
console.log([1, 2, 3, 4].reduce((a, b) => a + b));
// → 10
```
