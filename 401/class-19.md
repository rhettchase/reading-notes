# Class 19 Reading Notes: Automation

sources: links below, chatGPT
- [Python Regular Expressions Tutorial](https://www.datacamp.com/community/tutorials/python-regular-expression-tutorial)
- [shutil](https://pymotw.com/3/shutil/)
- [os](https://pymotw.com/3/os/)
- [Watchdog](https://pythonhosted.org/watchdog/)


## How can you use regular expressions in Python to search for specific patterns in a string, and what is the primary module to work with them?

In Python, regular expressions (regex) are supported by the `re` module. This module provides a way to search for patterns within strings. Here's a brief overview of how to use regular expressions in Python, including the primary functions provided by the `re` module:

### Importing the `re` Module

First, you need to import Python's regex module before you can use it:

```python
import re
```

### Basic Usage

- **Compiling Patterns:** For efficiency, especially when you need to use a pattern multiple times, it's a good practice to compile it.

    ```python
    pattern = re.compile(r"your_regex_here")
    ```

- **Searching:** To search for the first location where the regular expression pattern produces a match, use `search()`.

    ```python
    match = re.search(r"your_regex_here", "your_string_here")
    if match:
        print("Match found:", match.group())
    ```

- **Matching:** To check if the beginning of a string matches a pattern, use `match()`.

    ```python
    match = re.match(r"your_regex_here", "your_string_here")
    if match:
        print("Match found:", match.group())
    ```

- **Finding All Matches:** To find all substrings where the regex pattern matches and return them as a list, use `findall()`.

    ```python
    matches = re.findall(r"your_regex_here", "your_string_here")
    print("Matches found:", matches)
    ```

- **Replacing Substrings:** To replace occurrences of a pattern within a string, use `sub()`.

    ```python
    replaced_string = re.sub(r"your_regex_here", "replacement", "your_string_here")
    print("Replaced String:", replaced_string)
    ```

- **Splitting Strings:** To split a string by occurrences of a pattern, use `split()`.

    ```python
    split_list = re.split(r"your_regex_here", "your_string_here")
    print("Split list:", split_list)
    ```

### Special Characters and Sequences

Regular expressions use special characters and sequences to define patterns. For example:

- `.` matches any character except a newline.
- `^` matches the start of a string.
- `$` matches the end of a string.
- `\d` matches any decimal digit.
- `\w` matches any alphanumeric character.
- `+`, `*`, and `?` are quantifiers that match one or more, zero or more, and zero or one occurrence of the preceding element, respectively.
- `[abc]` matches any one of the characters a, b, or c.
- `(xyz)` defines a group.

### Flags

You can modify the behavior of the regex functions with flags:

- `re.IGNORECASE` (or `re.I`) makes the pattern case-insensitive.
- `re.MULTILINE` (or `re.M`) treats each line of the string as a separate string.
- `re.DOTALL` (or `re.S`) makes the `.` match all characters, including newline characters.

### Practical Example

Here's a simple example to demonstrate searching for a pattern in a string:

```python
import re

text = "Python is fun"
pattern = r"\b\w{3}\b"  # Matches words that are exactly 3 letters long

matches = re.findall(pattern, text)
print("Matches found:", matches)
```

This basic introduction to Python's `re` module and regular expressions should help you get started with pattern searching and manipulation in strings. Regular expressions are a powerful tool for text processing, and mastering them can greatly enhance your ability to work with textual data.

## What is the purpose of the shutil module in Python, and provide an example of a common use case for file or directory management with this module?

The `shutil` module in Python is used for high-level file operations, such as copying, moving, renaming, and deleting files and directories. It also supports file archiving and directory tree operations, making it a versatile module for file system manipulation.

### Purpose

The primary purpose of the `shutil` module is to simplify tasks that involve file and directory management, such as:

- Copying files and directories
- Moving or renaming files and directories
- Deleting files and directories
- Archiving and extracting files

### Common Use Case: Copying Files

One common use case for the `shutil` module is copying files from one location to another. This can be done using the `shutil.copyfile()` function, which copies the contents of a source file to a destination file. If the destination file does not have permission to be written, an `IOError` will be raised.

#### Example: Copying a File

Let's consider an example where we want to copy a Python script named `example.py` to a new file named `example_backup.py`.

```python
import shutil

# Define the source and destination file paths
source_file = 'example.py'
destination_file = 'example_backup.py'

# Copy the source file to the destination
shutil.copyfile(source_file, destination_file)

print(f'File copied from {source_file} to {destination_file}')
```

In this example, the `shutil.copyfile()` function is used to copy the content of `example.py` to a new file `example_backup.py`. After running this script, you will have a copy of the original file under a new name in the same directory.

### Why Use `shutil`?

Using `shutil` for file and directory operations is beneficial because:

- It abstracts the complexity of file operations, making it easier to write code for these tasks.
- It provides a higher level of interaction than the `os` module for certain operations, like copying entire directory trees with `shutil.copytree()` or removing them with `shutil.rmtree()`.
- It is cross-platform, meaning scripts written with `shutil` can work across different operating systems without modification.

## Compare and contrast the os and shutil modules. When would you choose to use one over the other?

The `os` and `shutil` modules in Python both provide functions for interacting with the file system, but they serve different purposes and offer different levels of abstraction for common file and directory operations. Understanding the distinctions between these two modules can help you choose the most appropriate one for your specific task.

### `os` Module

- **Purpose**: The `os` module provides a way to interact with the operating system and includes functions for creating, removing, and changing directories and files, as well as querying information about them. It also allows you to execute system commands, handle paths, and work with environment variables.

- **Functionality**:
  - File and directory manipulation at a lower level (e.g., `os.rename()`, `os.remove()`, `os.mkdir()`, `os.rmdir()`).
  - Access to system information and environment variables (e.g., `os.environ`, `os.system()`).
  - Path manipulation (e.g., `os.path.join()`, `os.path.split()`, `os.path.exists()`).

- **Use Cases**:
  - When you need detailed information and control over the file system and operating system, such as working with file descriptors.
  - For manipulating environment variables or executing system commands.
  - When working with paths and need functions to manipulate or query path information.

### `shutil` Module

- **Purpose**: The `shutil` module is focused on high-level file operations, such as copying, moving, renaming, and deleting files and directories. It also supports archiving and extracting files, making it more suited for file management tasks that involve groups of files and directories.

- **Functionality**:
  - Copying and moving files and directory trees (`shutil.copy()`, `shutil.copytree()`, `shutil.move()`).
  - Removing directory trees (`shutil.rmtree()`).
  - File archiving and extraction (e.g., `shutil.make_archive()`, `shutil.unpack_archive()`).

- **Use Cases**:
  - When you need to copy, move, or delete groups of files or directories.
  - For archiving (compressing) and extracting files and directories.
  - When you need a high-level interface that abstracts away the details of file operations.

### Comparison and Choice Criteria

- **Level of Abstraction**: `os` provides a lower-level interface that closely mirrors the underlying operating system's interface for file and directory operations. `shutil` offers a higher-level interface that abstracts many common tasks into simpler functions.

- **Scope of Functionality**: `os` is broader in scope, touching on system calls, environment variables, and low-level file operations. `shutil` is more focused on file and directory management tasks.

- **Use Case Specificity**: For detailed and granular control over files and directories, or when needing to interact with the operating system beyond file management, `os` is more suitable. For straightforward file and directory copying, moving, and removal, especially when dealing with multiple files or directories at once, `shutil` is the better choice.

### Conclusion

Choose `os` when you need granular control over file and directory operations or need to access system-specific functionality. Opt for `shutil` when working with high-level file operations, especially those involving multiple files or directories, and when you prefer simplicity and abstraction over direct control. In practice, it's common to use both modules in the same project, selecting each based on the specific task at hand.