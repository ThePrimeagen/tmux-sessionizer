## tmux sessionizer
its a script that does everything awesome at all times

## Usage
```bash
tmux-sessionizer [<partial name of session>]
```

if you execute tmux-sessionizer without any parameters it will assume FZF and
try to fuzzy find over a set of directories.

### Setup Directories
At the path `$XDG_CONFIG_HOME/tmux-sessionizer/directories` you can define all
the directories you want the script to look over.

```
~/
~/personal
~/personal/dev/env/.config
```
