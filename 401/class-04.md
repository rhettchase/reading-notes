# Class-04 Reading: Classes and Objects, Recursion, Pytest

sources: links below, chatGPT

- [Classes and Objects](https://www.learnpython.org/en/Classes_and_Objects)
- [Thinking Recursively](https://realpython.com/python-thinking-recursively/)
- [Pytest Fixtures and Coverage](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)
- [Pytest Fixtures](https://docs.pytest.org/en/latest/fixture.html)

## What are the key differences between classes and objects in Python, and how are they used to create and manage instances of a class?

### Class

- A class is a blueprint or a template for creating objects.
- It defines a set of attributes (variables) and methods (functions) that the objects created from the class will have.
- It encapsulates data and behavior into a single unit.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} is barking!")
```

### Object

- An object is an instance of a class. It is a concrete entity created based on the blueprint provided by the class.
- Objects have unique values for their attributes, and they can perform actions defined by the methods of the class.
- In this example, `dog1` and `dog2` are instances of the `Dog` class.

```python
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)
```

**Usage to Create and Manage Instances:**

- To create an instance of a class, you call the class as if it were a function. This invokes the class constructor (`__init__` method) and creates a new object.

```python
my_dog = Dog("Fido", 2)
```

You can access the attributes and methods of an object using dot notation.

```python
print(my_dog.name)  # Accessing attribute
my_dog.bark()       # Calling method
```

- You can create multiple instances of a class, each with its own unique attribute values.
- Classes can have class attributes (shared among all instances) and instance methods (operating on specific instances).
- Objects provide a way to model and represent real-world entities in your code, making it more modular and maintainable.

## Explain the concept of recursion and provide an example of how it can be used to solve a problem in Python. What are some best practices to follow when implementing a recursive function?

A recursive function is a function defined in terms of itself via self-referential expressions.

This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result. All recursive functions share a common structure made up of two parts: base case and recursive case.

1. Decompose the original problem into simpler instances of the same problem. This is the recursive case:

    `n! = n x (n−1) x (n−2) x (n−3) ⋅⋅⋅⋅ x 3 x 2 x 1 n! = n x (n−1)!`

2. As the large problem is broken down into successively less complex ones, those subproblems must eventually become so simple that they can be solved without further subdivision. This is the base case:

    `n! = n x (n−1)!  n! = n x (n−1) x (n−2)! n! = n x (n−1) x (n−2) x (n−3)! ⋅ ⋅ n! = n x (n−1) x (n−2) x (n−3) ⋅⋅⋅⋅ x 3! n! = n x (n−1) x (n−2) x (n−3) ⋅⋅⋅⋅ x 3 x 2! n! = n x (n−1) x (n−2) x (n−3) ⋅⋅⋅⋅ x 3 x 2 x 1!`

 `1!` is our base case, and it equals `1`.

Recursive function for calculating `n!` implemented in Python:

```python
def factorial_recursive(n):
    # Base case: 1! = 1
    if n == 1:
        return 1

    # Recursive case: n! = n * (n-1)!
    else:
        return n * factorial_recursive(n-1)
```

### Best Practices

1. Define base case
2. decompose the problem
3. maintain state property
4. use memoization
5. mind the call stack
6. watch for efficiency
7. avoid treating mutables as immutable

## What is the purpose of pytest fixtures and code coverage in testing Python code? Explain how they can be used together to improve the quality and maintainability of a project

Fixtures in pytest serve as a powerful mechanism to provide a defined and consistent context for tests. They help in setting up and tearing down resources or states needed for testing.

Code coverage is a metric that measures the percentage of code lines or branches executed during testing. It helps assess the thoroughness of testing by identifying which parts of the code are exercised by tests and which parts are not.

**Using pytest Fixtures and Code Coverage Together:**

1. **Setup Fixtures for Testing:** Use pytest fixtures to set up the testing environment, including any required configurations, resources, or test data.
2. **Define Test Functions:** Write test functions that utilize pytest fixtures to access the arranged environment and data. The fixtures provide a consistent context for tests.
3. **Integrate Code Coverage Tools:** Integrate code coverage tools, such as `coverage` or `pytest-cov`, into the testing process. Configure them to measure coverage for the specific parts of the codebase.
4. **Run Tests with Coverage Analysis:** Execute tests using the test runner (e.g., `pytest`) along with the code coverage tool. This provides a report on which parts of the code were covered during the tests.
5. **Analyze Code Coverage Reports:** Review the code coverage reports to identify areas with low coverage. Consider writing additional tests to cover those parts and improve overall coverage.
6. **Monitor Code Coverage in CI/CD:** Integrate code coverage analysis into the continuous integration and continuous deployment (CI/CD) pipeline. Monitor code coverage trends to ensure ongoing code quality.