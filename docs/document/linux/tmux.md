# Tmux

## Commands

- Create a new session in tmux:
    ```bash
    tmux new-session -d -s <session-name>
    ```
- Rename the name of session:
    - Command line:
        ```bash
        tmux rename-session -t <old-session-name> <new-session-name>
        ```
    - Shortcut:
        - Press `Ctrl + b` then `$` and type the new name of session


## Tmux configuration
- Change the icon in the left status bar
  - Open `~/.tmux.conf.local`
  - Find the line that starts with `tmux_conf_theme_status_left`

```
tmux_conf_theme_status_left=" <new icon> #S ..."
```
