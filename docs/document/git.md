# Git

- [[git_base|Merge branches in git]]
- [[git_remote|Add a remote repository]]

## Tips

??? Note "Create a new branch and push to remote"
    ```bash
    git checkout -b <new-branch>
    git push -u origin <new-branch>
    ```

??? Note "Edit a remote branch"
    ```bash
    git fetch origin <remote-branch>
    git checkout <remote-branch>
    # Make changes and commit
    git push origin <remote-branch>
    ```

??? Note "Rename a branch name"
    - Rename the current branch:
        ```bash
        git branch -m <new-branch-name>
        ```
    - Rename a specific branch:
        ```bash
        git branch -m <old-branch-name> <new-branch-name>
        ```

??? Note "Drop a commit"
    ```bash
    git rebase -i HEAD~<number-of-commits>
    ```

    - In the interactive rebase editor, change `pick` to `drop` for the commit you want to remove.
