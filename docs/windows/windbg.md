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

## Threads

- Show all threads in the process:

    ```
    ~* k
    ```

- Switch to a specific thread (e.g., thread 3):

    ```
    ~3s
    ```
