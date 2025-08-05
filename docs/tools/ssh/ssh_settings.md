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

---

## Remote Port Forwarding

Forward a port from a remote server to your local machine. When you connect to `<remote-port>` on the remote server, it will forward the connection to `<local-port>` on your local machine.

```bash
ssh -N -f -R <remote-port>:localhost:<local-port> user@remote-host
```

??? Note "Flags"
    - `-N`: Do not execute a remote command.
    - `-f`: Run in the background.
    - `-R`: Specifies that the given port on the remote host is to be forwarded to the local machine.

### Turn Off Remote Port Forwarding

Find the process ID (PID) of the SSH connection and kill it:

```bash
ps aux | grep "ssh.*-R"
```

Then, use the `kill` command with the PID:

```bash
kill -9 <PID>
```
