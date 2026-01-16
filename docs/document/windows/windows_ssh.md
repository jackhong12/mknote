# SSH Settings for Windows

## Setting up SSH config in Windows

Create a config file in `C:\Users\<YourUsername>\.ssh\config` with the following content:
```config title="SSH Config"
Host myserver
    HostName example.com
    User myuser
    Port 22
```

Generate SSH keys if you haven't already:
```powershell title="powershell"
ssh-keygen -t rsa
```

Copy the public key to the server:
```powershell title="powershell"
cd C:\Users\<YourUsername>
type .ssh\id_rsa.pub | ssh myserver "cat >> .ssh/authorized_keys"
```

## Forwarding SSH Port in WSL to Windows

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
