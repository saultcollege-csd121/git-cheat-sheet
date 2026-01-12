# CSD121 Git Cheat Sheet

## Cloning a Repository

> **WARNING**
> - Always **CLONE**, never download ZIP files from GitHub.  Cloning preserves the Git history and allows you to use Git commands. Copying does not.
> - Never clone into a directory that is already part of a Git repository.  This can cause conflicts and issues with tracking changes.

- `git clone <repository-url>`: Clone a repository from GitHub to the current directory.
- `git clone <repository-url> <directory-path>`: Clone a repository into a specific directory.

## Repositoy Info / State

- `git status`: Check the status of your repository.
- `git log`: View commit history.
- `git branch -a`: List all branches, including remote branches.
- `git remote -v`: Show remote repository URLs.
- `git diff`: Show changes between working directory and the staged changes.
- `git diff --staged`: Show changes between staged changes and the last commit.

## Staging and Committing

> **IMPORTANT**
> - It is good practice to make small, focused commits with clear messages.
> - Git allows you to 'stage' changes before committing them. This gives you control over what goes into each commit. E.g., you can stage only changes related to a specific feature or bug fix and leave out unrelated changes.
> - If your GUI seems to be freezing after a commit, you probably forgot to set a commit message. Look for an open text editor tab containing commit info. Add your commit message to the top and save/close it to complete the commit.

**NOTE**: Staging and committing is often easier using the GUI tools in IDEs like VS Code, but here are the equivalent command line commands.

- `git add <files>`: Stage selected files for the next commit.  **NOTE**: This 'staging' step allows you to control which changes are included in a commit. E.g. Add only changes related to a specific feature or bug fix.
- `git add --patch <file>`: Interactively stage portions of a file.
- `git add .`: Stage all changed files in the current directory and its subdirectories.
- `git restore <file>`: Discard unstaged changes for a specific file.
- `git restore --staged <file>`: Unstage a file that has been staged.
- `git commit -m "your commit message here"`: Commit staged changes with a message.
- `git reset --hard HEAD~1`: Undo the last commit and discard changes.  **NOTE**: If you have already pushed the commit to a remote repository, use `git revert <commit-hash>` instead to create a new commit that undoes the changes instead.
- `git diff`: Show changes between working directory and the staged changes.
- `git diff --staged`: Show changes between staged changes and the last commit.

## Working with Remote Repositories

- `git remote -v`: Show remote repository URLs.
- `git remote add <name> <url>`: Add a new remote repository with the given name.
- `git push <remote> <branch>`: Push commits to the remote repository, e.g. `git push origin lab-1`.
- `git fetch <remote>`: Fetch changes from the remote repository without merging. (The changes will be stored in `origin/<branch>` branches.)
- `git merge <branch>`: Merge a branch into the current branch. **Make sure you're on the correct branch before merging!**

## Branches

> **WARNING**: Before switching branches, make sure to `commit` or `stash` any uncommitted changes to avoid losing work!  Use `git status` to check for uncommitted changes before switching branches.

- `git branch -a`: List all branches, including remote branches.
- `git branch <branch>`: Create a new branch with a given name.
- `git switch <branch>`: Switch to the branch with the given name.  **See warning above!**

## Synchronizing With the Template Repository

Your lab repository is a fork of your teacher's template repository, meaning that they share a common history.  This means that you can easily sync your repository with any updates made to the template repository.

> **IMPORTANT**: The instructions below are intended to be done on your LOCAL repository on your development machine, (NOT on GitHub). You will need to add the template repository as a remote repository in order to fetch changes from it.
>
> E.g. `git remote add template https://github.com/saultcollege-csd121/lab-starter.git`
> 
> You only need to do this once.  After that, you can fetch changes from the template repository at any time.
>
> You can verify that the remote was added successfully by running `git remote -v`, which should show the URL of the template repository under the name `template`.

If your teacher updates the template repository, you can sync your repository with the latest changes by following these steps:

1. On your development machine, run `git fetch template` to download the latest changes from the template repository into your local repository.
2. **IMPORTANT**: Commit/stash any current uncommitted changes.
3. **IMPORTANT**: Switch to the branch you are updating (e.g., `git switch lab-1-starter`).
4. Run `git merge template/<the branch name here>` to merge the fetched changes into your local branch (e.g., `git merge origin/lab-1-starter`).