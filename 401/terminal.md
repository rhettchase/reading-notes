# Terminal

sources: [Ryan's Tutorials](https://ryanstutorials.net/linuxtutorial/), chatGPT

## [Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)

## [The Command Line](https://ryanstutorials.net/linuxtutorial/commandline.php)

### Terminals

- A command line or terminal is a text-based interface to the system where commands are entered by typing on the keyboard, and feedback is given as text.
- The command line typically displays a prompt (e.g., user@bash), and you enter commands after it.
- Commands are followed by command line arguments, separated by spaces. The first argument is often an option (e.g., -l), which modifies the command's behavior.
- Output from commands is displayed below the command and provides information about the command's execution.
- After a command runs, the terminal presents a new prompt, indicating that it's ready for another command.
- Commands may not always produce output, or they might display information only in case of errors.

### The Shell, Bash

- within a terminal you have a `shell`, part of the OS that defines how the terminal will behave and look like after running (executing) commands
- most common shell is called `bash`
- If you would like to know which shell you are using you may use a command called **echo** to display a system variable stating your current shell. echo is a command which is used to display messages. `echo $SHELL`

> When you enter commands, they are actually stored in a history. You can traverse this history using the up and down arrow keys. So don't bother re-typing out commands you have previously entered, you can usually just hit the up arrow a few times. You can also edit these commands using the left and right arrow keys to move the cursor where you want.

## [Basic Navigation](https://ryanstutorials.net/linuxtutorial/navigation.php)

### where are we?

- `pwd` (Print Working Directory): tells you what your current or present working directory is

### what's in our current location

- `ls` (list)
- `ls [options] [location]`
  - `[]` indicates optional

```shell
4. ls -l
5. total 3
6. drwxr-xr-x  2 ryan users 4096 Mar 23 13:34 bin
7. drwxr-xr-x 18 ryan users 4096 Feb 17 09:12 Documents
8. drwxr-xr-x  2 ryan users 4096 May 05 17:25 public_html
```

We ran ls with a single command line option (`-l`) which indicates we are going to do a long listing. A long listing has the following:

- First character indicates whether it is a normal file ( - ) or directory ( d )
- Next 9 characters are permissions for the file or directory (we'll learn more about them in section 6).
- The next field is the number of blocks (don't worry too much about this).
- The next field is the owner of the file or directory (ryan in this case).
- The next field is the group the file or directory belongs to (users in this case).
- Following this is the file size.
- Next up is the file modification time.
- Finally we have the actual name of the file or directory.

```shell
10. ls /etc
11. a2ps.cfg aliases alsa.d cups fonts my.conf systemd
```

We ran ls with a command line argument (` /etc `). When we do this it tells ls not to list our current directory but instead to list that directories contents.

```shell
ls -l /etc
```

both a command line option and argument. As such it did a long listing of the directory /etc.

### paths

- There are two types of paths in Linux: absolute and relative. Both types can be used to refer to files or directories, directing the system to the same location.
- The Linux file system is hierarchical, with the root directory denoted by a single slash ( `/` ).
- Absolute paths specify a location in relation to the root directory and always begin with a forward slash.
  - A file or directory location relative to where we currently are in the file system.
  - begin with a forward slash ( `/` )
- Relative paths specify a location in relation to the current position in the system and do not begin with a slash.
	- A file or directory location in relation to the root of the file system.

Additional path-building elements:

- "`~`" (tilde): Shortcut for the home directory.
- "`.`" (dot): Reference to the current directory.
- "`..`" (dotdot): Reference to the parent directory.

Examples:
"`ls ~/Documents`": Uses the tilde as a shortcut for the home directory.
"`ls ./Documents`": Uses a relative path with a dot to refer to the current directory.
"`ls /home/ryan/Documents`": Uses an absolute path.
"`ls ../../`": Uses dotdot to navigate up the hierarchy.
`ls /`: lists the contents of the root directory ("`/`")

### Moving Around Directories

- `cd [location]` - Change Directories - ie. move to another directory.
- location is specified as a path and as such may be specified as either an absolute or relative path

>If you run the command cd without any arguments then it will always take you back to your home directory.

## [Files](https://ryanstutorials.net/linuxtutorial/aboutfiles.php)

- In Linux, everything, including text files, directories, keyboards, and monitors, is treated as a file.
- Linux is an extensionless system, meaning file extensions (e.g., .exe, .txt, .png) are not crucial for determining file types. The system looks inside the file to identify its type.
- The "file" command `file [path]` is used to determine the type of a file or directory by examining its content.

### Case-sensitive and spaces

- Linux is case-sensitive. File and directory names with different cases are treated as distinct.
- Spaces in file and directory names can be valid but may cause issues on the command line. Use quotes or escape characters to handle spaces.
- Example using quotes: `cd 'Holiday Photos'`
- Example using escape characters: `cd Holiday\ Photos`
- Tab Completion can automatically escape spaces when using it before encountering the space in the directory name.

### Hidden files and Directories

- Hidden files and directories in Linux have names starting with a dot (e.g., .hidden). To list hidden items with the "`ls -a`" command - lists the contents of a directory, including hidden files.
- Example: `ls -a Documents`

## [Manual Pages](https://ryanstutorials.net/linuxtutorial/manual.php)

- The manual pages are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept.
- `man <command to look up>`
- example: `man ls`
  - includes name, synopsis, detailed description, options available

> exit the man pages by pressing `q` for quit

### Search manual pages

- This can be helpful if you're not quite sure of what command you may want to use but you know what you want to achieve. 
- `man <command>`: Look up the manual page for a particular command.
- `man -k <search term>`: Do a keyword search for all manual pages containing the given search term.
- `/<term>`: Within a manual page, perform a search for 'term'
  - press forward slash '`/`' followed by the term you would like to search for and hit '`enter`' If the term appears multiple times you may cycle through them by pressing the '`n`' button for next.

### commands shorthand vs. long hand

 - A lot of these have both a long hand and short hand version. eg. Above you will notice that to list all directory entries (including hidden files) we can use the option `-a` or `-all`
 - One advantage of using shorthand is that you can chain multiple together easier.
 - - long hand command line options begin with two dashes ( -- ) and short hand options begin with a single dash ( - ).

```shell
ls -a
ls --all
ls -alh
```

#### per manual

- `-L`: Follow all symbolic links to final target and list the file or directory the link references rather than the link itself. 
- `-H`:  Symbolic links on the command line are followed.

#### per chatGPT

- `ls`: Lists files and directories.
- `-a`: Displays hidden files and directories (those starting with a dot).
- `-l`: Outputs the list in a long format, providing additional information like permissions, owner, group, size, and modification date.
- `-h`: Human-readable format for file sizes, such as KB, MB, GB.

So, the command `ls -alh` shows a detailed listing of all files and directories in the current directory, including hidden ones, with human-readable file sizes.

## [File Manipulation](https://ryanstutorials.net/linuxtutorial/filemanipulation.php)

### Make Directory `mkdir`

`mkdir [options] <Directory>`

when we supply a directory in the above command we are actually supplying a path. Is the path we specified relative or absolute? Here are a few more examples of how we can supply a directory to be created

- `mkdir /home/ryan/foo`
- `mkdir ./blah`
- `mkdir ../dir1`
- `mkdir ~/linuxtutorialwork/dir2`

### Options

- `-p` which tells mkdir to make parent directories as needed
- `-v` which makes mkdir tell us what it is doing 

#### make parent directories (`-p`)

```bash
➜  pre-work mkdir -p linuxtutorial/foo/bar
➜  pre-work cd linuxtutorial/foo/bar 
➜  bar pwd
/Users/rhettchase/projects/courses/code-401/pre-work/linuxtutorial/foo/bar
```

#### (`-v`)

```shell
mkdir -pv linuxtutorialwork/foo/bar
mkdir: created directory 'linuxtutorialwork/foo'
mkdir: created directory 'linuxtutorialwork/foo/bar'
```

### Remove a directory `rmdir`

> there is no undo when it comes to the command line on Linux

`rmdir [options] <Directory>`

- `mdir` supports the `-v` and `-p` options similar to mkdir.
- a directory must be empty before it may be removed (later on we'll see a way to get around this).

### Create a blank file

`touch [options] <filename>`

- touch is actually a command we may use to modify the access and modification times on a file
- if we touch a file and it does not exist, the command will do us a favor and automatically create it for us.

### copying a file or directory `cp`

`cp [options] <source> <destination>`

Note that both the source and destination are paths. This means we may refer to them using both absolute and relative paths. Here are a few examples:

1. `cp /home/ryan/linuxtutorialwork/example2 example3`
2. `cp example2 ../../backups`
3. `cp example2 ../../backups/example4`
4. `cp /home/ryan/linuxtutorialwork/example2 /otherdir/foo/example5`

When we use `cp` the destination can be a path to either a file or directory.
- If it is to a file (such as examples 1, 3 and 4 above) then it will create a copy of the source but name the copy the filename specified in destination. 
- If we provide a directory as the destination then it will copy the file into that directory and the copy will have the same name as the source.

In it's default behavior `cp` will only copy a file. Using the `-r` option, which stands for recursive, we may copy directories. Recursive means that we want to look at a directory and all files and directories within it, and for subdirectories, go into them and do the same thing and keep doing this.

#### copying file example

```shell
➜  linuxtutorial ls
example1 foo      foo2
➜  linuxtutorial cp example1 barney
➜  linuxtutorial ls
barney   example1 foo      foo2
```

#### copying directory example

```shell
➜  linuxtutorial ls
example1 foo
➜  linuxtutorial cp foo foo2
cp: foo is a directory (not copied).
➜  linuxtutorial cp -r foo foo2
➜  linuxtutorial ls
example1 foo      foo2
```

### Moving a file or Directory `mv`

- One slight advantage is that we can move directories without having to provide the `-r`option.
- source and destination are paths and may be referred to as either absolute or relative paths.
- we may provide a new name for the file or directory and as part of the move it will also rename it.

`mv [options] <source> <destination>`

#### example

- create new directory called backups
- moved the directory foo2 into the directory backups
- moved the file barney into backups (did not provide a destination name, it kept the same name)

```bash
➜  linuxtutorial ls
barney   example1 foo      foo2
➜  linuxtutorial mkdir backups
➜  linuxtutorial mv foo2 backups/foo3 
➜  linuxtutorial mv barney backups 
➜  linuxtutorial ls
backups  example1 foo
➜  linuxtutorial ls backups 
barney foo3
```

### Renaming files and directories

- can use the basic behavior of the `mv` command to achieve a different outcome (renaming)
- If we specify the destination to be the same directory as the source, but with a different name, then we have effectively used mv to rename a file or directory.

#### example

- renamed the file foo to be foo3 (both paths are relative).
- moved into our parent directory
- renamed the directory testdir to fred

```bash
➜  linuxtutorial ls
backups  example1 foo
➜  linuxtutorial mv foo foo3
➜  linuxtutorial ls
backups  example1 foo3
➜  linuxtutorial cd ..
➜  pre-work mkdir linuxtutorial/testdir
➜  pre-work mv linuxtutorial/testdir linuxtutorial/fred
➜  pre-work ls linuxtutorial 
backups  example1 foo3     fred
```

### Removing a file (and non empty directories) `rm`

`rm [options] <file>`

#### options

- `-r`: Similar to `cp` it stands for recursive. When rm is run with the `-r` option it allows us to remove directories and all files and directories contained within.
- A good option to use in combination with `r` is `i`which stands for interactive. This option will prompt you before removing each file and directory and give you the option to cancel the command.

```shell
➜  linuxtutorial ls
backups foo3    fred
➜  linuxtutorial rmdir backups 
rmdir: backups: Directory not empty
➜  linuxtutorial rm -r backups
➜  linuxtutorial ls
foo3 fred
```
