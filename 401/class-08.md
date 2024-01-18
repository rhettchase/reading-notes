# Class 08 Reading Notes: List Comprehension, decorators

source: [List Comprehensions](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python), chatGPT

## What is the basic syntax of Python list comprehension, and how does it differ from using a for loop to create a list? Provide an example of a list comprehension that squares the elements in a given list of integers

List comprehension in Python is a concise and efficient way to create lists. It differs from using a traditional for loop in its syntax and often in its readability and efficiency. Here's a basic comparison:

**For Loop**

In this approach, you start with an empty list, iterate over each item in the original list, square it, and then append it to the new list.

```python
squared_list = []
for item in original_list:
    squared_list.append(item ** 2)

```

**List Comprehension:**

```python
squared_list = [item ** 2 for item in original_list]

```

With list comprehension, the same operation is condensed into a single, readable line. You specify the expression (`item ** 2`) followed by the loop (`for item in original_list`), all enclosed within square brackets.

Here's an example of a list comprehension that squares the elements in a given list of integers. This will produce `[1, 4, 9, 16, 25]`, which is a list of the squares of the original list's elements.

```python
original_list = [1, 2, 3, 4, 5]
squared_list = [item ** 2 for item in original_list]

```

## What is a decorator in Python?

A decorator in Python is a powerful tool that allows for the modification or enhancement of functions or methods.

## Explain the concept of decorators in Python. How do they work, and what are some common use cases for them? Provide an example of a simple decorator function from the reading.

- **Function Wrappers**: Decorators are essentially functions that wrap and modify other functions or methods. They add functionality to existing code without changing its structure.
- **Syntax**: Decorators are preceded by an `@` symbol and placed above the function definition they are modifying. For example, `@my_decorator`.
- **Reusability**: They promote code reusability and modularity by allowing you to apply the same functionality to multiple functions or methods.
- **Examples of Use**: Common uses include timing functions, logging, enforcing access control and permissions, memoization, and modifying or extending function behavior in various ways.
- **Stacking Decorators**: Multiple decorators can be applied to a single function, stacking their effects in the order they are applied.
- **Implementing a Decorator**: A decorator is implemented as a function that takes another function as an argument, defines an inner function that typically calls the original function with its arguments, and returns this inner function.
