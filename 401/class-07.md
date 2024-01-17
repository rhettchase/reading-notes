# Class 06 Reading Notes: Scope, Rolling Dice

source: links below, chatGPT

- [Python Scope](https://realpython.com/python-scope-legb-rule/)
- [Big O notation is simpler than you might think](https://www.youtube.com/watch?v=dNorFNlDbX0)
- [Rolling Dice Examples](https://web.archive.org/web/20220608035657/https://artofproblemsolving.com/wiki/index.php/Basic_Programming_With_Python#Random)

## Explain the concept of variable scope in Python and describe the difference between local and global scope. Provide an example illustrating the usage of both

- **Concept**: Variable scope in Python refers to the accessibility of variables in different parts of the program. A variable's scope is determined by where it is defined and dictates where it can be accessed and modified.
- **Local Scope**: Local variables are declared inside a function and can only be accessed within that function. They are created when the function is called and destroyed when the function exits. This encapsulation ensures that local variables in one function are not accessible to other functions unless passed as arguments.
- **Global Scope**: Global variables are defined outside of functions and can be accessed throughout the program, including within functions. They persist for the duration of the program’s execution.
- **Example**:

```python
def my_function():
    local_var = 5  # Local variable
    print(global_var + local_var)

global_var = 10  # Global variable
my_function()  # Outputs 15
# print(local_var)  # Would raise an error as local_var is not accessible here
```

## How do the global and nonlocal keywords work in Python, and in what situations might you use them?

**Global Keyword**: Used to declare a variable as global inside a function, allowing you to modify the global variable from within the function.

- **Usage**: Typically used when a function needs to modify a variable defined outside of it.
- **Example**:

```python
counter = 0
def increment_counter():
    global counter
    counter += 1

```

**Nonlocal Keyword**: Used in nested functions to declare a variable as non-local, i.e., it belongs to an outer (enclosing) function and allows modifying it.

- **Usage**: Useful in closures or nested functions where you want to modify a variable defined in an outer function.
- **Example**:

```python
def outer_function():
    outer_var = 10
    def inner_function():
        nonlocal outer_var
        outer_var += 5
    inner_function()
    return outer_var

```

## In your own words, describe the purpose and importance of Big O notation in the context of algorithm analysis

Big O notation is a mathematical representation used to describe the efficiency of an algorithm in terms of time (time complexity) or space (space complexity) relative to the size of the input data (n). It focuses on the worst-case scenario to provide an upper bound on the time or space requirements.

Understanding Big O notation is crucial for evaluating and comparing the efficiency of different algorithms, especially with large datasets. It helps in predicting performance, optimizing code, and making informed decisions about which algorithm to use in a given context. For example, an algorithm with a time complexity of O(n^2) will typically perform worse than one with O(n) as the dataset grows larger.

## Based on the Rolling Dice Example, explain how you would simulate a dice roll using Python. Describe how you would use code to calculate the probability of rolling a specific number (e.g., the probability of rolling a 6) over a large number of trials

**Simulate a Dice Roll (Program Example 1):**

- We use the `random` module in Python, which provides functions for generating random numbers.
- The `random.randint(1,6)` function is used to generate a random integer between 1 and 6, inclusive, which simulates the roll of a fair six-sided dice.

```python
import random
print(random.randint(1,6))

```

**Calculate the Probability of Rolling a 6 (Program Example 2)**:

- To simulate rolling the dice multiple times, a loop is used. In this case, the dice is rolled 1000 times.
- Each roll is checked to see if it results in the desired number (in this case, 6).
- A counter (`count`) is used to track the number of times the desired number is rolled.
- After all rolls are completed, the probability is calculated by dividing the count of successful rolls (rolls that resulted in 6) by the total number of rolls.

```python
import random

def roll_dice():
    return random.randint(1, 6)

total_rolls = 1000
count_sixes = 0

for _ in range(total_rolls):
    if roll_dice() == 6:
        count_sixes += 1

print("Number of sixes rolled:", count_sixes)
probability_of_six = count_sixes / total_rolls
print(f"Probability of rolling a 6: {probability_of_six}")

```

In this code, we roll the dice 1000 times and count how many times a 6 is rolled. The probability is then calculated as the ratio of the number of times a 6 is rolled to the total number of rolls.

It's important to note that as the number of trials increases, the calculated probability will converge closer to the theoretical probability. For a fair six-sided dice, the theoretical probability of rolling any specific number, such as a 6, is 1661​ or approximately 0.1667.