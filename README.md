## tmux sessionizer
its a script that does everything awesome at all times

## Usage
```bash
tmux-sessionizer [<partial name of session>]
```

if you execute tmux-sessionizer without any parameters it will assume FZF and
try to fuzzy find over a set of directories.

If you want to have a default set of paths but extend these on the fly then simply set `TMUX_PATHS` for example:
`export TMUX_PATHS="$HOME/Documents"`
