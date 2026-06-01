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

## Local Port Forwarding (-L)
Forward local port to remote host.


---

## Remote Port Forwarding (-R)

Forward remote port to local host.

```bash
ssh -N -f -R <remote-port>:localhost:<local-port> user@remote-host
```

??? Note "Flags"
    - `-N`: Do not execute a remote command.
    - `-f`: Run in the background.
    - `-R`: Specifies that the given port on the remote host is to be forwarded to the local machine.
    - Redirect the message to a file:
        ```bash
        ssh -N -f -v -R <remote-port>:localhost:<local-port> user@remote-host > <file path> 2>&1
        ```
        - `-v`: Basic debugging output.
        - `-vv`: Medium debugging output.
        - `-vvv`: Detailed debugging output.

### Turn Off Remote Port Forwarding

Find the process ID (PID) of the SSH connection and kill it:

```bash
ps aux | grep "ssh.*-R"
```

Then, use the `kill` command with the PID:

```bash
kill -9 <PID>
```

---

## [[socks_proxy|Dynamic Port Forwarding]] (-D)
Create a SOCKS proxy that forwards traffic through the SSH connection.
