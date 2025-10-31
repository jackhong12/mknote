# WinDbg

## Attach to a Process

There are two ways to attach WinDbg to a running process:

1. File -> Attach to a Process -> Select the desired process.
2. Press `F6` and select the desired process from the list.

## Threads

- Show all threads in the process:

    ```
    ~* k
    ```

- Switch to a specific thread (e.g., thread 3):

    ```
    ~3s
    ```
