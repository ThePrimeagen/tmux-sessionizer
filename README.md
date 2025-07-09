## tmux sessionizer
its a script that does everything awesome at all times

## Requirements
fzf and tmux

## Usage
```bash
tmux-sessionizer [<partial name of session>]
```

if you execute tmux-sessionizer without any parameters it will FZF set of default directories or ones specified in config file.

## Session Commands
Session commands are for you to write / navigate without using tmux navigation commands.
They are meant to be used with zsh/vim/tmux remaps.

The basic idea is that you want long running commands on a per session basis.
You can start them by calling tmux-sessionizer with the -s option.  This will
start the long running session starting at window 69.  This means if you open 6
windows, it wont interfere with your way of using tmux.

### Example
tmux-sessionizer config file
```bash
# file: ~/.config/tmux-sessionizer/tmux-sessionizer.conf
TS_SESSION_COMMANDS=(opencode .)
```

There is one command which means you can call `tmux-sessionizer -s 0` only (`-s 1` is out of bounds)
This will effectively call the following command:
```bash
tmux neww -t $SESSION_NAME:69 opencode .
```

### How i use it
Here are my vim remaps for tmux-sessionizer.  C-f will do the standard
sessionizer experience but Alt+h will mimic my harpoon navigation.  C-h is
first file harpoon.  M-h is first sessionizer command.

**vim**
```lua
vim.keymap.set("n", "<C-f>", "<cmd>silent !tmux neww tmux-sessionizer<CR>")
vim.keymap.set("n", "<M-h>", "<cmd>silent !tmux neww tmux-sessionizer -s 0<CR>")
vim.keymap.set("n", "<M-t>", "<cmd>silent !tmux neww tmux-sessionizer -s 1<CR>")
vim.keymap.set("n", "<M-n>", "<cmd>silent !tmux neww tmux-sessionizer -s 2<CR>")
vim.keymap.set("n", "<M-s>", "<cmd>silent !tmux neww tmux-sessionizer -s 3<CR>")
```

**zsh**
```bash
bindkey -s ^f "tmux-sessionizer\n"
bindkey -s '\eh' "tmux-sessionizer -s 0\n"
bindkey -s '\et' "tmux-sessionizer -s 1\n"
bindkey -s '\en' "tmux-sessionizer -s 2\n"
bindkey -s '\es' "tmux-sessionizer -s 3\n"
```
**oh-my-zsh**
Install zsh using a proper plugin from [oh-my-zsh](https://github.com/jeffreytse/zsh-vi-mode?tab=readme-ov-file#as-an-oh-my-zsh-custom-plugin).
Then, add the following to your `~/.zshrc`:

```bash
zvm_after_init_commands+=("bindkey -s '^f' 'tmux-sessionizer\n'")
zvm_after_init_commands+=("bindkey -s '\eh' 'tmux-sessionizer -s 0\n'")
zvm_after_init_commands+=("bindkey -s '\et' 'tmux-sessionizer -s 1\n'")
zvm_after_init_commands+=("bindkey -s '\en' 'tmux-sessionizer -s 2\n'")
zvm_after_init_commands+=("bindkey -s '\es' 'tmux-sessionizer -s 3\n'")
```

Doing so will ensure that the keybindings are set up after other potentially conflicting keybindings are initialized.

**tmux**
```bash
bind-key -r f run-shell "tmux neww ~/.local/bin/tmux-sessionizer"
bind-key -r M-h run-shell "tmux neww tmux-sessionizer -s 0"
bind-key -r M-t run-shell "tmux neww tmux-sessionizer -s 1"
bind-key -r M-n run-shell "tmux neww tmux-sessionizer -s 2"
bind-key -r M-s run-shell "tmux neww tmux-sessionizer -s 3"
```

## Enable Logs
This is for debugging purposes.

```bash
# file: ~/.config/tmux-sessionizer/tmux-sessionizer.conf
TS_LOG=file | echo # echo will echo to stdout, file will write to TS_LOG_FILE
TS_LOG_FILE=<file> # will write logs to <file> Defaults to ~/.local/share/tmux-sessionizer/tmux-sessionizer.logs
```
