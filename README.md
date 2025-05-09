## tmux sessionizer
its a script that does everything awesome at all times

## Usage
```bash
tmux-sessionizer [<partial name of session>]
```

### Changing search paths
```bash
export TMUX_SESSIONIZER_PATHS="~/projects ~/work"
```

if you execute tmux-sessionizer without any parameters it will assume FZF and
try to fuzzy find over a set of directories.
