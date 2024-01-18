<h2> GIT COMMANDS </h2>

Git is a version control system. It allows us to access old and new versions of the code we are working on. It allows us to check what changes have been made in the project and by whom. 
Let's now examine the common commands used in the git versioning system.

Email and username configuration must be done before starting to operate in git system.

```ini
  git config --global user.name "hediyeorhan"
  git config --global user.email hediyeorhan2015@gmail.com # Please add your username and e-mail address here.
  ```

First, we create a git folder in the project we will work on in our local directory with the command given below.

```ini
  git init # initilazition
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
  git status # Shows current git status. It shows if the current directory is linked to any git.
  ```

The log command is used to see by whom and when commit messages were made.

```ini
  git log
  ```
To return to the old commit version, you can list the commits with the log command and then return to that commit by obtaining the commit hash code.

Hash code: Each commit has its own number.

```ini
  git log
  git checkout version_hash_code
  git commit -m "old version copied"
  ```

A .gitignore file should be created to hide the files in our local directory that we do not want to upload to github. Then we write the files we want to hide into .gitignore.

```ini
  touch .gitignore # You can find .gitignore templates on Google according to the technology you use.
  ```

"Branch" are independent workspaces that represent different development paths of the project. Branches are used to track and test different features or enhancements of the project, or to allow different teams to work on different tasks.

Head indicates / points to which branch and which commit we are on.

Create new branch:

```ini
  git branch new_branch_name
  ```

Branch switching:

```ini
  git switch branch_name
  ```

Merge two branches

```ini
  git switch branch1   # We went into branch1 and merged it with branch2.
  git merge branch2
  ```

List current branches

```ini
  git branch # It indicates which branch we are in with '*'.
  ```

Files / folders created in each branch belong to that branch. If not merge, they cannot be accessed by other branches. 
Commits from different branches are also not visible to each other.

Fast forwarding: It is the process of merge the changes made in a branch derived / created from the master branch to the master.

*When there are conflicting codes in both branches: when the other branch is merged while in the master branch, the changes in the other branch are written to the file in the master branch.*

When a file deleted in the master is modified in the other branch and merge is desired, the *merge conflic* situation arises because there is no file in the master.

!!! To merge any two branches, there must be no overlap.