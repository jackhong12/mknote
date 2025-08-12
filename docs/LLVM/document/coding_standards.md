# Coding Standards

## Assert
If the peice of code should not be executed, use `llvm_unreachable` instead of `llvm_assert`.
    ```cpp
    llvm_unreachable("This code should not be executed");
    ```

??? note "Tags"
    - [[clang-format]]
