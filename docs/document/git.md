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
