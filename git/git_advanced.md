The advanced Git commands along with their descriptions and example usage:

# Advanced Git Commands

## 1. `git stash`
- **Command**:
  ```sh
  git stash
  git stash apply
  git stash pop

- **Description**: Temporarily saves changes that are not ready to be committed, allowing you to work on something else. apply reapplies the changes without removing them from the stash. pop reapplies and removes the changes from the stash.

## 2. `git cherry-pick`
  - **Command**:

    ```sh

    git cherry-pick <commit>

- **Description**: Applies the changes introduced by an existing commit onto your current branch. Useful for applying specific commits from another branch.

## 3. `git rebase`

 - **Command**:

    ```sh

    git rebase <branch>
    git rebase -i <commit>

- **Description**: Reapplies commits on top of another base tip. The interactive mode (-i) allows you to edit commit messages, squash commits, and reorder commits.

## 4. `git reset`

 - **Command**:

    ```sh

    git reset <mode> <commit>

- **Description**: Moves the current branch to a specified commit. Modes include:
        --soft: Keeps changes in the index
        --mixed: Keeps changes in the working directory
        --hard: Discards all changes

## 5. `git reflog`

 - **Command**:

    ```sh

    git reflog

- **Description**: Shows a log of all references to the head, allowing you to recover lost commits and branches.

## 6. `git bisect`

 - **Command**:

    ```sh

    git bisect start
    git bisect bad <commit>
    git bisect good <commit>

- **Description**: Helps to find the commit that introduced a bug by binary search.

## 7. `git diff`

 - **Command**:

    ```sh

    git diff <commit1> <commit2>
    git diff <branch1> <branch2>

- **Description**: Shows the differences between commits, branches, or the working directory and the index.

## 8. `git log`

- **Command**:

    ```sh

    git log --oneline
    git log --graph
    git log --stat

- **Description**: Shows the commit logs. Options like --oneline, --graph, and --stat enhance the display.

## 9. `git submodule`
 - **Command**:

    ```sh

    git submodule add <repo> <path>
    git submodule update --init

- **Description**: Manages submodules within a repository. Use to add, initialize, and update submodules.

## 10. `git blame`

  - **Command**:

    ```sh

    git blame <file>

- **Description**: Shows who last modified each line of a file.

## 11. `git clean`

 - **Command**:

    ```sh

    git clean -f
    git clean -fd

- **Description**: Removes untracked files from the working directory. -f removes files, and -fd removes directories.

## 12. `git tag`

 - **Command**:

    ```sh

    git tag <tagname>
    git tag -a <tagname> -m "message"

- **Description**: Creates tags for commits, useful for marking release points (e.g., v1.0).
