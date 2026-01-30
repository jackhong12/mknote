# GDB Tips

## Lauch GDB

- Start GDB with a program:
    ```bash
    $ gdb ./your_program
    ```

- Run a program with arguments:
    ```bash
    $ gdb --args ./your_program arg1 arg2
    ```

- Run a program with a GDB command:
    ```bash
    $ gdb -ex "<command>" --args ./your_program arg1 arg2
    ```

- Run a program with a GDB script:
    ```bash
    $ gdb -x ./script --args ./your_program arg1 arg2
    ```
