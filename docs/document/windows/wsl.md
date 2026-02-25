# WSL

## Install

Open PowerShell as Administrator and run:

```powershell title="PowerShell"
wsl --install
```

## Don't shut down WSL on exit

```ini title="/etc/wsl.conf"
[boot]
systemd=true
```

## Release disk space

WSL will occupy disk space even after removing resources. To free up disk space, run the following command in PowerShell:

- Shutdown WSL:
    ```powershell title="PowerShell"
    wsl --shutdown
    ```

- Compress the virtual disk:
    ```powershell title="PowerShell"
    diskpart
    DISKPART> select vdisk file="C:\Users\<你的帳號>\AppData\Local\Packages\wsl\...\ext4.vhdx"
    DISKPART> attach vdisk readonly
    DISKPART> compact vdisk
    DISKPART> detach vdisk
    DISKPART> exit
    ```
