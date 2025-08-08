# zsh

## Custom Icons
Modify the following settings in `~/.p10k.zsh` to add custom icons:

```zsh title="~/.p10k.zsh"
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
  os_icon # Add this line for OS icon
  ...
)

# Add your custom icon here
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='⭐'
```

You can search icons from [Nerd Fonts](https://www.nerdfonts.com/cheat-sheet).

- Suggested font: [Ubuntu Mono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/UbuntuMono.zip)
