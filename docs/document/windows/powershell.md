# Powershell Settings

## File Path
- Powershell
    ```
    ~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
    ```
- Developer Powershell for VS
    ```
    ~\Documents\PowerShell\profile.ps1
    ```

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

2. Find the path of vim:
    ```powershell
    Get-ChildItem "C:\Program Files\Vim" -Recurse -Filter "vim.exe"
    ```

    It will show something like this:
    ```
        Directory: C:\Program Files\Vim\vim92

    Mode                 LastWriteTime         Length Name
    ----                 -------------         ------ ----
    -a---           5/25/2026  7:39 AM         209920 vim.exe
    ```

2. Add vim path. You need to change the path according to the output of the previous command:
    ```powershell
    [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Program Files\Vim\vim92", [EnvironmentVariableTarget]::User)
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

        function Clean-Path {
            $seen = @{}
            $newPaths = @()
            foreach ($p in $env:PATH -split ";") {
                $normalized = $p.Trim().ToLower()
                if ($normalized -ne "" -and -not $seen.ContainsKey($normalized)) {
                    $seen[$normalized] = $true
                    $newPaths += $p.Trim()
                }
            }
            $env:PATH = $newPaths -join ";"
        }

        Import-Module PSReadLine # Better history & completion
        Set-PSReadLineOption -PredictionSource History

        Clean-Path # Remove duplicate paths from PATH environment variable

        $env:PATH += ";<new path>" # Add new path to PATH environment variable
        ```
??? Note "PowerShell Too Old"
    If you get the error, it might be because your PowerShell version is too old. You can check your PowerShell version by running:
    ```powershell
    Install-Module PSReadLine -Force -Scope CurrentUser

    # Check Oh My Posh version
    $PSVersionTable.PSVersion
    ```
