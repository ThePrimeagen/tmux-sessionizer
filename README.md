# tmux sessionizer
its a script that does everything awesome at all times

## Basic usage
```bash
tmux-sessionizer [<partial name of session>]
tmux-sessionizer -add PATH_TO_FOLDER_YOU_WANT_IN_YOUR_LIST [Optional: all]
tmux-sessionizer -delete
tmux-sessionizer -list
```


## Options
    -a, -add
        Adds the provided directory to your tmux-sessionizer list. This only
        adds the actual directory which you provide. Alternatively, you can add
        the "all" keyword after your filepath to automatically add any
        directories directly within the filepath directory to your
        tmux-sessionizer list
    
    -d, -delete
        Opens a fzf window that you can use to delete any directory paths that
        you no longer want in your list. You can select multiple options to
        delete by clicking tab on the paths you want to delete and then
        clicking enter to confirm
        
    -l, -list
        List all the paths in your tmux-sessionizer list
    

### Example commands

if you execute tmux-sessionizer without any parameters it will assume FZF and
try to fuzzy find over a set of directories.
/home/john/personal/tmux-sessionizer/direct_paths_fullpath
