# Git Commands Cheat Sheet

- [Git Commands Cheat Sheet](#git-commands-cheat-sheet)
  - [Here are some of the most common and useful Git commands](#here-are-some-of-the-most-common-and-useful-git-commands)
  - [Git Configuration](#git-configuration)
  - [Create Project](#create-project)
  - [Local Changes](#local-changes)
  - [Track Changes](#track-changes)
  - [Commit History](#commit-history)
  - [Ignoring files](#ignoring-files)
  - [Branching](#branching)
    - [Git branch](#git-branch)
    - [Git checkout](#git-checkout)
    - [Git stash](#git-stash)
  - [Merging](#merging)
    - [Git merge](#git-merge)
    - [Git rebase](#git-rebase)
  - [Remote](#remote)
  - [Pushing Updates](#pushing-updates)
  - [Pulling Updates](#pulling-updates)
    - [Git pull](#git-pull)
    - [Git fetch](#git-fetch)
  - [Undo Changes](#undo-changes)
    - [Git revert](#git-revert)
    - [Git reset](#git-reset)
  - [Removing Files](#removing-files)
  - [Reference](#reference)

![Ebook_Cover](../images/git-cover.png)

**[Buy PDF](https://buymeacoffee.com/kananinirav/e/260740)**

## Here are some of the most common and useful Git commands

## Git Configuration

| Command                                                     | Description                                    |
| ----------------------------------------------------------- | ---------------------------------------------- |
| `$ git config`                                              | 🛠️ Get and set configuration variables for Git. |
| `$ git config --global user.name "User name"`               | ✏️ Set the name.                                |
| `$ git config --global user.email "your-email@example.com"` | ✉️ Set the email.                               |
| `$ git config --global core.editor "your-editor"`           | 📝 Set the default editor.                      |
| `$ git config --global color.ui auto`                       | 🌈 Turns on color output for Git commands.      |
| `$ git config --list`                                       | ℹ️ See all your settings.                       |

## Create Project

| Command       | Description                  |
| ------------- | ---------------------------- |
| `$ git init`  | 🏁 Create a local repository. |
| `$ git clone` | 🔄 Clone a remote repository. |

## Local Changes

| Command                             | Description                                       |
| ----------------------------------- | ------------------------------------------------- |
| `$ git add file-path`               | ➕ Adds a file to the staging area.                |
| `$ git add .`                       | ➕ Add all files to the staging area.              |
| `$ git commit -m " Commit Message"` | 💾 Commit file permanently in the version history. |

## Track Changes

| Command                                     | Description                                                        |
| ------------------------------------------- | ------------------------------------------------------------------ |
| `$ git diff`                                | 🔄 Shows the differences between your folder and the stage.         |
| `$ git diff --staged`                       | 🔄 Shows the differences between the stage and the last commit.     |
| `$ git diff HEAD`                           | 🔄 Track the changes after committing a file.                       |
| `$ git diff <branch-2>`                     | 🔄 Track the changes between two commits.                           |
| `$ git status`                              | ℹ️ Display the state of the working directory and the staging area. |
| `$ git show`                                | ℹ️ Show the newest commit on a branch.                              |
| `$ git diff -- file-path`                   | 🔄 Show changes for a particular file.                              |
| `$ git diff branch-1 branch-2 --name-only`  | 🔄 Show difference between two branches (file names only).          |
| `$ git diff branch-1 branch-2 -- file-path` | 🔄 Show differences between two branches for a specific file.       |

## Commit History

| Command              | Description                                                   |
| -------------------- | ------------------------------------------------------------- |
| `$ git log`          | 📜 Display the most recent commits and the status of the head. |
| `$ git log -oneline` | 📜 Display the output as one commit per line.                  |
| `$ git log -stat`    | 📜 Displays the files that have been modified.                 |
| `$ git log -p`       | 📜 Display the modified files with location.                   |

## Ignoring files

| Command                                             | Description                                                        |
| --------------------------------------------------- | ------------------------------------------------------------------ |
| `$ touch .gitignore`                                | 📝 Create a file named `.gitignore` to list ignored files.          |
| `$ git update-index --skip-worktree <file_name>`    | 📝 Mark a file as "skip-worktree" to ignore changes in it.          |
| `$ git update-index --no-skip-worktree <file_name>` | 📝 Unmark a file as "skip-worktree" to stop ignoring changes in it. |

A collection of useful `.gitignore` templates for different languages or frameworks: [gitignore](https://github.com/github/gitignore)

## Branching

### Git branch

| Command                  | Description                                                              |
| ------------------------ | ------------------------------------------------------------------------ |
| `$ git branch`           | 🌿 Show a list of all branches in your local repository.                  |
| `$ git branch -a`        | 🌿 Show all branches in both local and remote repositories.               |
| `$ git branch -r`        | 🌿 Show only remote branches.                                             |
| `$ git branch name`      | 🌿 Creates a new branch called `name` based on the current commit.        |
| `$ git branch name hash` | 🌿 Create a new branch based on a specific commit identified by its hash. |

### Git checkout

| Command                         | Description                                |
| ------------------------------- | ------------------------------------------ |
| `$ git checkout branch-name`    | 🔀 Switch between branches in a repository. |
| `$ git checkout -b branch-name` | 🔀 Create a new branch and switch to it.    |

### Git stash

| Command                           | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| `$ git stash`                     | 📦 Stash current work.                          |
| `$ git stash save "your message"` | 📦 Saving stashes with a message.               |
| `$ git stash list`                | 📦 Check the stored stashes.                    |
| `$ git stash apply`               | 📦 Re-apply the changes that you just stashed.  |
| `$ git stash show`                | 📦 Track the stashes and their changes.         |
| `$ git stash pop`                 | 📦 Re-apply the previous commits.               |
| `$ git stash drop`                | 📦 Delete the most recent stash from the queue. |
| `$ git stash clear`               | 📦 Delete all the available stashes at once.    |
| `$ git stash branch`              | 📦 Stash work on a separate branch.             |

## Merging

### Git merge

| Command               | Description                                                                                                                        |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `$ git merge name`    | 🤝 Merges branch called `name` into the current branch, creating a new commit that incorporates both changes.                       |
| `$ git merge --abort` | 🤝 Aborts the merge process and restores the original state of your project, if there are any conflicts or errors during the merge. |

### Git rebase

| Command                  | Description                                                         |
| ------------------------ | ------------------------------------------------------------------- |
| `$ git rebase`           | 🔀 Apply a sequence of commits from one branch to another.           |
| `$ git rebase -continue` | 🔀 Continue the rebasing process after resolving conflicts manually. |
| `$ git rebase --skip`    | 🔀 Skip a commit when rebasing.                                      |

## Remote

| Command                            | Description                                                                     |
| ---------------------------------- | ------------------------------------------------------------------------------- |
| `$ git remote`                     | 🌐 Show a list of all remote repositories associated with your local repository. |
| `$ git remote -v`                  | 🌐 Check the configuration of the remote server.                                 |
| `$ git remote show name`           | 🌐 Show information about a specific remote repository called `name`.            |
| `$ git remote add origin repo-url` | 🌐 Add a remote for the repository.                                              |
| `$ git remote rm`                  | 🌐 Remove a remote connection from the repository.                               |
| `$ git remote rename`              | 🌐 Rename a remote server.                                                       |
| `$ git remote show`                | 🌐 Show additional information about a particular remote.                        |
| `$ git remote set-url name url`    | 🌐 Change the URL of a remote repository called name to url.                     |

## Pushing Updates

| Command                    | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `$ git push origin master` | 📤 Push data to the remote repository.                 |
| `$ git push --all`         | 📤 Push all branches to the default remote repository. |
| `$ git push --all origin`  | 📤 Specify the remote repository explicitly.           |
| `$ git push -f`            | 📤 Force push data to the remote repository.           |

## Pulling Updates

### Git pull

| Command                    | Description                                                   |
| -------------------------- | ------------------------------------------------------------- |
| `$ git pull`               | 📥 Pull changes from the default remote repository and branch. |
| `$ git pull origin master` | 📥 Specify the remote repository and branch explicitly.        |

### Git fetch

| Command                        | Description                          |
| ------------------------------ | ------------------------------------ |
| `$ git fetch <repository URL>` | 📥 Fetch the remote repository.       |
| `$ git fetch`                  | 📥 Fetch a specific branch.           |
| `$ git fetch --all`            | 📥 Fetch all branches simultaneously. |
| `$ git fetch origin`           | 📥 Synchronize the local repository.  |

## Undo Changes

### Git revert

| Command               | Description                                                                                 |
| --------------------- | ------------------------------------------------------------------------------------------- |
| `$ git revert HEAD`   | ⏪ Undo the latest commit.                                                                   |
| `$ git revert hash`   | ⏪ Create a new commit that undoes changes made by a specific commit identified by its hash. |
| `$ git revert branch` | ⏪ Undo all commits on a branch.                                                             |

### Git reset

| Command                    | Description                                                                                                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$ git reset --soft hash`  | ⏪ Reset your current branch to a specific commit identified by its hash, keeping your working directory and staging area unchanged.                                             |
| `$ git reset --mixed hash` | ⏪ Reset your current branch to a specific commit identified by its hash, resetting your staging area to match it, but keeping your working directory unchanged.                 |
| `$ git reset --hard hash`  | ⏪ Reset your current branch to a specific commit identified by its hash, resetting your working directory and staging area to match it, discarding any changes made since then. |

## Removing Files

| Command                  | Description                                                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `$ git rm file`          | 🗑️ Delete a file from both your working directory and staging area, staging the deletion for the next commit. |
| `$ git rm --cached file` | 🗑️ Delete a file only from the staging area, but not from the working directory.                              |

## Reference

- [Git Docs](https://www.git-scm.com/docs/git#_git_commands)
