<h2> GIT COMMANDS </h2>

Git is a version control system. It allows us to access old and new versions of the code we are working on. It allows us to check what changes have been made in the project and by whom. 
Let's now examine the common commands used in the git versioning system.

Email and username configuration must be done before starting to operate in git system.

```ini
  git config --global user.name "hediyeorhan"
  git config --global user.email hediyeorhan2015@gmail.com # please add your username and e-mail address here.
  ```

First, we create a git folder in the project we will work on in our local directory with the command given below.

```ini
  git init # initilazition
  ```

Then, if we want to add files to the project, we can add files with the touch command. 

```ini
  touch add_file # create file
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

The ***rm*** command deletes files in the directory, the ***mv*** command changes the file name. It is used to move files.

If we want to get the files back after adding them with git add command:

```ini
  git reset HEAD filename
  git checkout --filename
  ```

In Git, the ***status*** command is used to check if there is a change in the project that has not been committed.

```ini
  git status # shows current git status. It shows if the current directory is linked to any git.
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
  touch .gitignore # you can find .gitignore templates on Google according to the technology you use.
  ```

If the files we added to our .gitignore file are not hidden and are being uploaded to github, we can use : 

```ini
  git rm --cached file_name
  git commit -m "cache cleared"
  ```

"Branch" are independent workspaces that represent different development paths of the project. Branches are used to track and test different features or enhancements of the project, or to allow different teams to work on different tasks.

Head indicates / points to which branch and which commit we are on.

Create new branch:

```ini
  git branch new_branch_name
  ```

Branch switching :

```ini
  git switch branch_name
  ```

Merge two branches : 

```ini
  git switch branch1   # we went into branch1 and merged it with branch2.
  git merge branch2
  ```

List current branches

```ini
  git branch # it indicates which branch we are in with '*'.
  ```

Files / folders created in each branch belong to that branch. If not merge, they cannot be accessed by other branches. 
Commits from different branches are also not visible to each other.

Fast forwarding: It is the process of merge the changes made in a branch derived / created from the master branch to the master.

***When there are conflicting codes in both branches: when the other branch is merged while in the master branch, the changes in the other branch are written to the file in the master branch.***

When a file deleted in the master is modified in the other branch and merge is desired, the ***merge conflic*** situation arises because there is no file in the master.

***!!! To merge any two branches, there must be no overlap.***

To restore the file from the last commit : 

```ini
  git restore filename
  ```

Git can store changes that are not added and committed on itself with ***stash***. When done in this way, the changes are not visible in the 'git status' command.
Git stores it inside itself and we can retrieve it whenever we want.

```ini
  git stash  # hiding the file that was not committed.
  ```

To get the information stored in git stash back into files in our project : 

```ini
  git stash pop  # it brings it back and deletes it from the list.
  ```

When different changes are made in a row, all stashes are listed and kept in ids.

```ini
  git stash list  # it shows what we keep up to date.
  ```

If we want to add stashes one by one : 

```ini
  git stash apply stash_id  # it does not delete it from the list.
  ```

Clear all stash : 

```ini
  git stash clear
  ```

<h3> Returning to past commits </h3>

To return to an old commit : 

```ini
  git log # from here, the hash code of the desired commit can be obtained.
  git checkout commit_hash_code
  ```

When returning to an old commit, the ***'HEAD detached'*** branch is switched to instead of the master branch.
You can go back to the master branch with the git switch command. Or a new branch can be created and the edits of the old commit can be kept here.

To return to the commit only one step before : 

```ini
  git reset HEAD~1
  ```

The ***reset*** command can be used to delete all commits after the specified commit from the ***git log*** history. However, this command only deletes commits from the commit history and does not delete the changes made to the commits deleted in the project. 

```ini
  git reset commit_hash_code
  ```

Changes made to the project by commits deleted with the ***hard*** parameter can also be deleted.

```ini
  git reset --hard commit_hash_code
  ```

The ***revert*** command is used to keep commits in the commit history and only delete changes from the project. It undoes the actions and creates a new commit. It does not delete commits in the ***git log*** history.

```ini
  git revert commit_hash_code  # the project gets this commit back.
  ```

To see changes/differences between two commits or in a project, use : 

```ini
  git diff HEAD # what shows differently according to the last commit.

  git diff commit1_hash_code commit2_hash_code # it shows the difference between two commits.

  git diff commit1_hash_code : commit2_hash_code # it can also be used this way.
  ```

To see the difference between the two branches : 

```ini
  git diff branch1_name branch2_name

  git diff branch1_name : branch2_name
  ```

To clear the logs and rewrite the date and get rid of merge commits in between : 

```ini
  git switch branch1_name
  git rebase branch2_name  # first the commits in branch2 are sorted, then the commits in branch1 are sorted.
  ```

<h3> Uploading the project to github </h3>

To upload our local project to Github, a github repo must first be created. Afterwards, we can check the updates of the additions and commits we made in the project with git status. 
The remote command should be used to remotely connect to the repository we created.

```ini
  git remote add origin github_repo_url.git # the term "origin" represents the repo url for easier use in later commands. 
  ```

After the remote connection is established, the ***push*** command is used to upload our local files to github.

```ini
  git push -u origin main # if your branch name is different, it can be changed. For example: master, feat .. 
  ```

Here, when the ***push*** command is executed, you are asked to log in to your github account from the terminal screen or browser.

If main / master branch will be pushed, only ***git push*** command will be enough. If a different branch is to be pushed, the ***git push origin branch_name*** command should be used.

***PULL REQUEST***

It is a request to modify a repo that belongs to someone else. Or someone else's request to modify a repo that belongs to me.

In order to see the changes we made in the project on Github on local, we need to pull the project to local. 
Branches on Github are considered remote branches. To list these branches, you can use : 

```ini
  git branch -r 
  ```

To pull the final version of the project from github to local : 

```ini
  git fetch # can be used when merge is not desired.
  ```

To navigate between remote branches, use : 

```ini
  git checkout origin/branch_name
  ```

To merge the current version of the project that we have localized from Github : 

```ini
  git pull 
  ```

***git pull = git fetch + git merge***

***push -> sends to Github***

***pull -> pulls from Github.***

To pull a repo that belongs to someone else and make changes to it, we need to ***fork*** that repo on Github so that it is listed among our own repos. Then we should clone it to our local repository by getting the url address among our own repos.

```ini
  git clone repo_url.git # move repo to local.
  ```

***This way we can push and pull this repo.***