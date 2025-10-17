# SOCKS Proxy

## Establis a SOCKS Proxy with SSH

Run this command to establish a SOCKS proxy using SSH:
```bash
ssh -N -f -D <port> <user>@<host>
```

## Open Chrome with SOCKS Proxy

Add the following command to a batch file to open Chrome with the SOCKS proxy:

```bat title="chrome.bat"
"C:\Program Files\Google\Chrome\Application\chrome.exe" --proxy-server="socks://127.0.0.1:<port>"
exit # Close the terminal
```

```bat title="edge.bat"
# kill existing Edge instances
taskkill /IM msedge.exe /F

"C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --proxy-server="socks://127.0.0.1:<port>"
exit # Close the terminal
```
