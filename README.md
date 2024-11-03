# tmux sessionizer
its a script that does everything awesome at all times

## Basic usage
```bash
tmux-sessionizer [<partial name of session>]
```

By default, tmux-sessionizer holds its state in .tmux-sessionizer.txt in your
$HOME directory, but this can be changed within the top of tmux-sessionizer
itself

## Options
    -a, -add
        Adds full filepaths to your tmux-sessionizer list via stdin or
        interactive mode. It will automatically reject duplicates, and will
        only accept valid absolute filepaths to folders that exist.
    
    -d, -delete
        Opens a multi-select fzf of your current tmux-sessionizer list which
        can be used to delete files in your list by selecting either one file
        to delete using the enter key, or multiple files using tab to select
        multiple files and then enter to delete those files. CTRL-C to exit
    
    -l, -list
        Lists the contents of the tmux-sessionizer list.

### Example commands
Add all directories within the current working directory to your list.
```bash
find $(pwd) -maxdepth 1 -type d | tmux-sessionizer -a
```

Enter fzf and delete folders in your tmux-sessionizer list by selecting them
with tab and then clicking enter
```bash
tmux-sessionizer -d
```

List all the directories in your tmux-sessionizer list
```bash
tmux-sessionizer -l
```

if you execute tmux-sessionizer without any parameters it will assume FZF and
try to fuzzy find over a set of directories.
