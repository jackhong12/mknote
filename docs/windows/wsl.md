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
