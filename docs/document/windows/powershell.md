# Powershell Settings

## Quick Commands
- Open the current folder:
    ```powershell
    explorer .
    ```
- Open the current folder in VS Code:
    ```powershell
    code .
    ```

## Git
Install git from [git-scm](https://git-scm.com/install/windows).

## SSH
Gererate ssh key by the following command:
```powershell
ssh-keygen
```


## Vim
1. Install by the following command:
    ```powershell
    winget install Vim.Vim
    ```

2. Add vim path:
    ```powershell
    [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Program Files\Vim\vim82", [EnvironmentVariableTarget]::User)
    ```

## Oh My Posh
1. Install by the following command:
    ```powershell
    winget install JanDeDobbeleer.OhMyPosh
    ```
2. Enable ps1 file execution:
    - Check the current execution policy:
        ```powershell
        Get-ExecutionPolicy -List
        ```
    - Set the execution policy for the current user:
    ```powershell
    Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
    ```

3. Add profile:
    - Create the folder:
        ```powershell
        New-Item -ItemType Directory -Force -Path (Split-Path $PROFILE)
        ```
    - Check if the profile file exists:
        ```powershell
        Test-Path $PROFILE
        ```
    - Edit the profile file:
        ```powershell
        vim $PROFILE
        ```
    - Add the following content to the profile file:
        ```powershell
        oh-my-posh init pwsh | Invoke-Expression

        # Better history & completion
        Import-Module PSReadLine
        Set-PSReadLineOption -PredictionSource History
        ```
??? Note "PowerShell Too Old"
    If you get the error, it might be because your PowerShell version is too old. You can check your PowerShell version by running:
    ```powershell
    Install-Module PSReadLine -Force -Scope CurrentUser

    # Check Oh My Posh version
    $PSVersionTable.PSVersion
    ```
