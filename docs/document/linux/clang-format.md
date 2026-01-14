# clang-format

## Format Code

- Format the previous commit using clang-format:
    ```bash
    git clang-format HEAD~1
    ```

- Format only one file in the previous commit:
    ```bash
    git clang-format HEAD~1 <file>
    ```

- Add the changes to the commit:
    ```bash
    git commit --amend --no-edit
    ```


??? Note "Tags"
    - [[git|git]]
