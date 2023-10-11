# Class-03 Reading Notes: Revisions and the Cloud

## What is Version Control?

- System that allows you to revisit various versions of a file or set of files by recording changes
- Allows you to revert a file or project to a previous version, track modifications (and who made the modification), and compare changes
- Enables mistakes to be easily rectified
- **Git** is a version control system

## What is `cloning` in Git?

- `cloning` creates a copy of an existing Git repository from a particular server by using the clone command with a repository’s URL
- By cloning the file, you have copied all versions of all files for a project

## What is the command to track and stage files?

- _**Single file**_ `git add [file name]`
- _**All files**_ `git add *`

- After using these commands, files are tracked and staged for committing
- Staging is like placing items into a scene to photograph
- It tells Git to include these changes in the next snapshot

## What is the command to take a snapshot of your changed files?

Use the `git status` command to see information regarding changes to be committed

```text
$ git status

On branch master

Changes to be committed:

  (use "git reset HEAD ..." to unstage)

  new file: EXAMPLE
```

This information tells us that there are changes to be committed and that the file has been staged.

## What is the command to send your changed files to Github?

### Committing a File

After staging one or multiple files, you should commit the changes and record what you did within the commit message:

```text
$git commit -m “made change x,y,z because x”
```

### Committing All Changes

```text
$git commit -a
```

This command commits a snapshot of all modifications to tracked files in the working directory.

### Pushing Changes to GitHub remote repository

Type **`git push origin main`**

This command sends any new commits (the snapshots of your code) to GitHub
