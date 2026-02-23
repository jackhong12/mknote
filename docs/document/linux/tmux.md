# Tmux Settings

## Commands

- Create a new session in tmux:
    ```bash
    tmux new-session -d -s <session-name>
    ```

## .oh-my-tmux
- Change the icon in the left status bar
  - Open `~/.tmux.conf.local`
  - Find the line that starts with `tmux_conf_theme_status_left`

```
tmux_conf_theme_status_left=" <new icon> #S ..."
```
