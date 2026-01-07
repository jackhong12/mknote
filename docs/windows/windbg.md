# WinDbg

## Command Line
How to launch WinDbg from the command line:
```powershell title="Command to launch WinDbg"
& "C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\windbg.exe"
& "C:\Program Files\WindowsApps\Microsoft.WinDbg_1.2506.12002.0_x64__8wekyb3d8bbwe\DbgX.Shell.exe"
```

## Attach to a Process

There are two ways to attach WinDbg to a running process:

1. File -> Attach to a Process -> Select the desired process.
2. Press `F6` and select the desired process from the list.

## Breakpoints

- Add a breakpoint at a specific address:
    ```bash
    # Add a breakpoint at a specific function (e.g., function in module):
    bp <exe>!<function>
    bp <module>!<function>
    bp <function>

    # Continue execution:
    g
    ```
- Remove breakpoints:
    ```bash
    # Remove a specific breakpoint (e.g., breakpoint number 1):
    bc 1

    # Remove all breakpoints:
    bc *
    ```

- List all breakpoints:
    ```
    bl
    ```

## Module Info
- List all loaded modules:

    ```
    lm
    ```
- Show detailed information about a specific module:

    ```
    !lmi <module>
    ```

## Threads

- Show all threads in the process:

    ```
    ~* k
    ```

- Switch to a specific thread (e.g., thread 3):

    ```
    ~3s
    ```
