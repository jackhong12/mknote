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
```bash title="bash"
ip addr show eth0 | grep inet
```

Forward the SSH port from WSL to Windows using `netsh` command in PowerShell:
```powershell title="powershell"
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=0.0.0.0 connectport=22 connectaddress=<WSL IP>
```

Enable the port `2222` in Windows Firewall:
```powershell title="powershell"
netsh advfirewall firewall add rule name="WSL SSH" dir=in action=allow protocol=TCP localport=2222
```

??? note "SSH Port Forwarding Settings"
    - Show all port forwarding rules with:
        ```powershell title="powershell"
        netsh interface portproxy show all
        ```

        It will show something like this:
        ```
        Listen on ipv4:             Connect to ipv4:

        Address         Port        Address         Port
        --------------- ----------  --------------- ----------
        0.0.0.0         2222        xxx.xxx.xxx.xxx 22
        ```

    - Remove the port forwarding rule if needed:
        ```powershell title="powershell"
        netsh interface portproxy delete v4tov4 listenport=2222 listenaddress=0.0.0.0
        ```

??? note "Firewall Configuration"
    - Show all firewall rules with:
    ```powershell title="powershell"
    netsh advfirewall firewall show rule name=all | Out-File tmp.txt
    ```
