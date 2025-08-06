# Copilot Settings

## Panel for Completion
Open a window with up to 10 completions.

```vim title="vim command mode"
:Copilot panel
```

## Accepting Completions
Default keybinding to accept a completion is `<tab>`. You can map it to another key if you prefer. For example, to use `<c-j>`:

```vim title=".vimrc"
imap <silent><script><expr> <C-J> copilot#Accept("\<CR>")
let g:copilot_no_tab_map = v:true
```

## Reference
- [Copilot Document](https://github.com/github/copilot.vim/blob/release/doc/copilot.txt)
