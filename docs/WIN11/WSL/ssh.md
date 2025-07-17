# SSH Settings in WSL

## Forwarding SSH Port

In WSL, find IP address with:
```bash
ip addr show eth0 | grep inet
```

Forward the SSH port from WSL to Windows using `netsh` command in PowerShell:
```powershell
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=0.0.0.0 connectport=22 connectaddress=<WSL IP>
```

Enable the port `2222` in Windows Firewall:
```powershell
netsh advfirewall firewall add rule name="WSL SSH" dir=in action=allow protocol=TCP localport=2222
```
