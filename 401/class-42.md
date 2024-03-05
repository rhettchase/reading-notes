# Class 42 Reading Notes: Pythonisms

sources: links below, chatGPT

- [Dunder Methods](https://dbader.org/blog/python-dunder-methods)
- [Iterators](https://dbader.org/blog/python-iterators)
- [Generators](https://dbader.org/blog/python-generators)
- [What are Generators](https://realpython.com/lessons/what-are-python-generators/) (video)
- [Decorators](https://realpython.com/primer-on-python-decorators/)

## What are dunder methods in Python, and how do they allow for the customization of built-in behavior in classes? Provide an example of a common dunder method and its purpose

Dunder methods, short for "double underscore" methods, are special methods in Python that begin and end with double underscores (`__`). They are also known as magic methods or special methods. These methods allow you to customize or define the behavior of Python classes in a variety of ways, making them extremely powerful for object-oriented programming. Dunder methods let you emulate the behavior of built-in types or implement operator overloading, among other things. This means you can define how objects of your classes should behave with respect to language constructs such as iteration, context management, attribute access, arithmetic operations, and more.

### Example of a Common Dunder Method: `__init__`

One of the most commonly used dunder methods is `__init__`, which is the initializer for a class. It's called when an object is created from a class, allowing the class to initialize the object's attributes.

#### Purpose of `__init__`

The `__init__` method is used to:

- Initialize a new object's state.
- Assign values to object properties.
- Execute any initialization logic necessary for the object's creation.

#### Example Usage of `__init__`

Let's look at an example of a class that represents a book. We'll use the `__init__` method to initialize objects of this class with properties like `title`, `author`, and `year`.

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year

    def __str__(self):
        return f"'{self.title}' by {self.author} ({self.year})"

# Creating an instance of the Book class
my_book = Book("1984", "George Orwell", 1949)

# Printing the book instance
print(my_book)  # Output: '1984' by George Orwell (1949)
```

In this example, the `__init__` method takes three parameters besides `self` (which is a reference to the current instance) and assigns them to the instance's attributes. The `__str__` method is another dunder method that we've implemented to return a human-readable string representation of the object. When you print the object, Python automatically calls the `__str__` method.

### Customizing Built-in Behavior

By implementing dunder methods, you can define how objects of your class should interact with Python's built-in functions (`len()`, `str()`, `iter()`, etc.) and operators (`+`, `-`, `==`, etc.). This allows for a high degree of customization and makes your custom objects more Pythonic, behaving more like the built-in types.
    
## Explain the concept of an iterator in Python. How do you create a custom iterator using the **iter**() and **next**() methods, and why are they important for enabling iteration in a class?

In Python, an iterator is an object that can be iterated over, meaning you can traverse through all the values. Technically, an iterator is an object which implements the iterator protocol, consisting of the methods `__iter__()` and `__next__()`.

### Iterator Protocol:

- **`__iter__(self)`**: This method returns the iterator object itself. It is called on the initialization of an iterator. This method should always return the iterator object (usually `self`).
- **`__next__(self)`**: This method returns the next value for the iterable. When an iterator is used with a `for` loop, the loop implicitly calls `next()` on the iterator object. This method should return the next value for the iterable. When there are no more items to return, it should raise a `StopIteration` exception.

### Creating a Custom Iterator

To create a custom iterator, you need to implement the `__iter__()` and `__next__()` methods in your iterator class.

Here's a simple example to illustrate how to create a custom iterator that produces squares of numbers up to a given number:

```python
class Squares:
    def __init__(self, max_root):
        self.max_root = max_root
        self.current = 0

    def __iter__(self):
        # An iterator must return itself as an iterator.
        return self

    def __next__(self):
        # Increment the current number
        self.current += 1
        # Check if we've reached the maximum limit
        if self.current > self.max_root:
            # If so, raise StopIteration
            raise StopIteration
        # Otherwise, return the next square
        return self.current ** 2

# Using the custom iterator
squares = Squares(5)
for square in squares:
    print(square)
```

Output:
```
1
4
9
16
25
```

### Importance of `__iter__()` and `__next__()` for Enabling Iteration

- **`__iter__()`**: This method makes an object iterable. The presence of `__iter__()` method in a class signals that objects of the class are iterable. When an object is required to support iteration (for example, in a `for` loop, or when using the `iter()` built-in function), Python checks for the `__iter__()` method on the object.
  
- **`__next__()`**: This method provides a way to compute and return the next value in the sequence. By defining custom logic inside `__next__()`, you can control how iteration proceeds, which is especially useful for complex or unconventional sequences that aren't easily expressed with a simple range or list.

Together, these methods allow you to define custom iteration logic that fits the specific needs of your class, making it possible to iterate over objects in a clear and Pythonic way. This is particularly important for creating objects that represent complex sequences or data structures where you need precise control over the iteration behavior.
    
## What is a generator in Python, and how does it differ from a regular function? Illustrate your answer with an example of a generator function using the ‘yield’ keyword

In Python, a generator is a special type of iterator, a function that returns an iterator object. Generators simplify the creation of iterators by automatically implementing the `__iter__()` and `__next__()` methods with a simpler syntax. The key feature that distinguishes a generator from a regular function is the presence of one or more `yield` statements instead of a `return` statement. When a generator function calls `yield`, it produces a value to the caller and suspends its own execution, maintaining its state for when it's called again.

### Differences Between Generators and Regular Functions

- **State Preservation**: Generators preserve their execution state between successive calls. This means that variables, loop progress, and exception states are saved between each `yield` and the next call to `next()`. Regular functions, in contrast, do not preserve state; they start fresh on every invocation.
- **Memory Efficiency**: Generators are memory efficient because they only produce one item at a time, perfect for processing large datasets or streams of data where you don't want to store the entire dataset in memory.
- **Laziness**: Generators compute values on demand ('lazily'), which allows them to be used for potentially infinite sequences.

### Example of a Generator Function

Let's illustrate the concept of a generator with a simple example. Suppose we want to create a generator that yields the first `n` Fibonacci numbers. The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones, usually starting with 0 and 1.

```python
def fibonacci(n):
    a, b = 0, 1
    count = 0
    while count < n:
        yield a  # Produce the current value of a
        a, b = b, a + b  # Update the values of a and b
        count += 1

# Create a generator for the first 5 Fibonacci numbers
fib_generator = fibonacci(5)

# Iterate through the generator
for num in fib_generator:
    print(num)
```

Output:
```
0
1
1
2
3
```

In this example, the `fibonacci` function is a generator function because it uses the `yield` keyword. It maintains its state between yields, so every time it's called by the `for` loop, it picks up where it left off and yields the next Fibonacci number. This behavior is fundamentally different from a regular function, which would require managing state manually if it needed to produce a sequence of values over successive calls.
    
## Define decorators in Python and explain their primary use case. How can you create and apply a custom decorator to a function or method? Provide a simple example to demonstrate this concept

Decorators in Python are a very powerful and useful tool, allowing you to modify the behavior of a function or method without permanently modifying the function itself. They are defined by the `@` symbol and placed before a function definition. A decorator takes in a function, adds some functionality to it, and returns it. Decorators can be used to enforce access control, logging, caching, or even add functionality that enhances the decorated function in some way.

### Primary Use Case of Decorators

The primary use cases of decorators include:

- **Logging**: To log information about which functions are called and with what arguments.
- **Access Control**: To check for permissions before allowing calls to certain functions.
- **Caching/Memoization**: To store the results of expensive function calls and return the cached result when the same inputs occur again.
- **Instrumentation/Profiling**: To measure execution time, memory usage, or other performance metrics.
- **Modification of Function Behavior**: To modify inputs, outputs, or the behavior of the function itself.

### Creating and Applying a Custom Decorator

Creating a custom decorator involves defining a wrapper function inside another function. The outer function accepts the function to be decorated, and the inner function (wrapper) includes the modifications or additional functionality. The decorator returns this wrapper function.

Here's a simple example demonstrating how to create and apply a custom decorator that logs the execution of a function:

```python
def log_decorator(func):
    def wrapper(*args, **kwargs):
        print(f"Executing '{func.__name__}' with arguments {args} and keyword arguments {kwargs}")
        result = func(*args, **kwargs)  # Call the original function
        print(f"'{func.__name__}' returned {result}")
        return result
    return wrapper

# Applying the decorator
@log_decorator
def add(a, b):
    return a + b

# Using the decorated function
add(5, 3)
```

Output:
```
Executing 'add' with arguments (5, 3) and keyword arguments {}
'add' returned 8
```

In this example, `log_decorator` is a decorator that logs the name of the function being executed, its arguments, and its return value. When we apply `@log_decorator` to the `add` function, any call to `add` will first print the log messages defined in `log_decorator` before executing `add` itself. This demonstrates how decorators can add functionality to a function without changing the function's code.