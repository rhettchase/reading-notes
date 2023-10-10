# Class-02 Reading Notes: The Coder's Computer

## Text Editor Critical Features

1. Code completion
2. Syntax highlighting
3. Variety of formatting themes to choose from
4. Good selection of extensions

## Basic Commands

- `pwd` - *Where are we?* Print Working Directory (It tells you what your current or present working directory is)
- `ls` - *What's in our current location?* `ls` (short for list)  shows a List of the contents of a directory
  - With no arguments, it will just do a plain listing of our current location
- `cd [location]` - Change Directory (move) to specified location
  - If you run `cd` without any arguments then it will always take you back to your home (root) directory
- `mkdir` - Creates a directory
- `touch` - Used to create, change or modify a file
  - `touch [file name]` creates a new file with the specified file name in the current directory

## Scenario

1. `cd projects`
2. `mkdir new-project`
3. `touch new-project/newfile.md`
4. `cd ..`
5. `ls projects/new-project`

If the above commands and arguments are entered in the terminal, the below will happen:

1. Change Directory to the `projects` directory
2. Create new folder called `new-project` in the `projects` directory
3. Create new file called `newfile.md` in the `new-project` directory
4. Changes Directory up one level in the hierarchy in reference to the parent directory up to `projects` directory
5. Shows a List of the contents of `ls projects/new-project` directory
