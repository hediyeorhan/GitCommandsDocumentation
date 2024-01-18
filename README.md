<h2> GIT COMMANDS </h2>

Git is a version control system. It allows us to access old and new versions of the code we are working on. It allows us to check what changes have been made in the project and by whom. 
Let's now examine the common commands used in the git versioning system.

First, we create a git folder in the project we will work on in our local directory with the command given below.

```ini
  git init
  ```

Then, if we want to add files to the project, we can add files with the touch command. 

```ini
  touch add_file
  mkdir folder # create folder
  ```

We use the git add command to make these and similar changes permanent in the project. The Add command loads all files into the transition zone.

```ini
  git add . # adds all files
  git add add_file # adds the file we specifically specified
  ```

After adding the files, a commit message should be written to these files.

```ini
  git commit -m "commit message"
  ```

To run the add and commit commands on a single line, use : 

```ini
  git commit -am "commit message"
  ```

The *rm* command deletes files in the directory, the *mv* command changes the file name. It is used to move files.

If we want to get the files back after adding them with git add command:

```ini
  git reset HEAD filename
  git checkout --filename
  ```

In Git, the *status* command is used to check if there is a change in the project that has not been committed.

```ini
  git status
  ```

The log command is used to see by whom and when commit messages were made.

```ini
  git log
  ```
