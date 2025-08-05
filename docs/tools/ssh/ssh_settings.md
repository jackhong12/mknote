# SSH Settings

## Ubuntu Settings
Add the following settings to your `~/.ssh/config` file to simplify SSH connections:

```config title="~/.ssh/config"
Host myserver
    HostName <ip>
    User <username>
    Port <port>
```

Directly type `ssh myserver` to connect to the server instead of using the full command.
```bash
ssh myserver
```
