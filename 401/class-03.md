# Reading 03: FileIO and Exceptions

source: below links, chatGPT

## Reading

[Read & Write Files in Python](https://realpython.com/read-write-files-python/)
[Exceptions in Python](https://realpython.com/python-exceptions/)
[Reading and Writing Files in Python Quiz](https://realpython.com/quizzes/read-write-files-python/)

## Videos

[File Objects - Reading and Writing to Files](https://www.youtube.com/watch?v=Uh2ebFW8OYM)
## What is the purpose of the `with` statement when opening a file in Python, and how does it help manage resources while reading and writing files?

The `with` statement in Python is used to simplify the management of resources, particularly for objects that require clean-up or releasing resources, such as file handling operations. When working with file I/O, using the `with` statement is recommended because it ensures that the file is properly opened and closed, even if an exception occurs during the file operation.

The primary purpose of the `with` statement when opening a file is to provide a convenient way to handle the opening and closing of the file. When a file is opened using `with`, the file is automatically closed when the block inside the `with` statement is exited. This helps in managing resources efficiently and prevents potential issues like file leaks or resource exhaustion.

```python
with open('dog_breeds.txt', 'r') as reader:
    # Further file processing goes here
```

1. **Automatic Resource Management:** The `with` statement takes care of the resource management, ensuring that the file is closed properly, even if an exception occurs.
2. **Cleaner Code:** It results in cleaner and more readable code by eliminating the need for explicit `try` and `finally` blocks to ensure proper resource cleanup.
3. **Reduced Risk of Errors:** It reduces the risk of errors related to resource management, making the code more robust.
## Explain the difference between the `read()` and `readline()` methods for file objects in Python. Provide examples of when to use each method.

### `read()` Method

The `read()` method is used to read a specified number of characters from the file, or if no size is specified, it reads the entire content of the file. It returns a string containing the read characters.

```python
# Example using read() to read the entire file content
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)

```

### `readline()` Method

The `readline()` method is used to read a single line from the file. It stops reading when it encounters a newline character (`'\n'`) or reaches the end of the file. It returns a string containing the read line.

```python
# Example using readline() to read a single line from the file
with open('example.txt', 'r') as file:
    line = file.readline()
    print(line)

```

### When to Use Each Method

- Use `read()` when you want to read the entire content of the file or a specific number of characters at once.
- Use `readline()` when you want to read one line at a time, especially in scenarios where you are processing a file line by line.

Here's an extended example that demonstrates reading multiple lines from a file using `readline()`: In this example, the `while True` loop continues reading lines from the file until it reaches the end. The `strip()` method is used to remove newline characters for cleaner output.

```python
# Example using readline() to read multiple lines from the file
with open('example.txt', 'r') as file:
    while True:
        line = file.readline()
        if not line:
            break  # Break the loop if the end of the file is reached
        print(line.strip())  # Remove newline characters and print each line

```
## Briefly describe the concept of exception handling in Python. How can the `try`, `except`, and `finally` blocks be used to handle exceptions and ensure proper execution of code? Provide a simple example

1. **try:** The `try` block is used to enclose the code that might raise an exception. If any exception occurs within the `try` block, it is caught, and the corresponding `except` block is executed.
2. **except:** The `except` block is used to handle specific exceptions that might be raised within the `try` block. It contains the code that should be executed when a particular exception occurs.
3. **finally:** The `finally` block is optional and is used to define code that will be executed regardless of whether an exception occurred or not. It is often used for cleanup operations, such as closing files or releasing resources.

```python
def divide_numbers(a, b):
    try:
        result = a / b
        print(f"The result of {a} / {b} is: {result}")
    except ZeroDivisionError:
        print("Error: Division by zero is not allowed.")
    finally:
        print("This code always runs, regardless of whether an exception occurred or not.")

# Example usage
divide_numbers(10, 2)   # Normal case
divide_numbers(5, 0)    # Division by zero, triggers the except block

```

- The `try` block attempts to perform the division operation.
- If the division is successful, the `except` block is skipped, and the `finally` block is executed.
- If a `ZeroDivisionError` occurs (division by zero), the `except` block is executed, and then the `finally` block is also executed.

#### output

```
The result of 10 / 2 is: 5.0
This code always runs, regardless of whether an exception occurred or not.
Error: Division by zero is not allowed.
This code always runs, regardless of whether an exception occurred or not.

```