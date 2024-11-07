* [X] Make quick command to add the current working directory

* [X] Make quick command to add all directories in the current working
      directory

* [ ] After the quick commands, resolve how to do this when piping an entire
      file

* [ ] handle duplicate entries, maybe do a check before inserting another path

* [ ] make a separate list for wildcard dirs such as /home/user/* These will
      get expanded upon running tmux-sessionizer so they stay up to date.

* [ ] Get rid of creating and removing files, do everything with bash arrays
      and only use files when it is the only other way

* [ ] Allow tmux-sessionizer -a to accept a second argument being a path, if it
      is a relative path, we simply add it to the relative path list, if it
      matches multiple directories we can add it to the wildcard list

* [ ] Eventually i don't want the storage files to clutter the home, and
      instead have a better place to hold their data. Unless maybe the $HOME is
      ideal...? idk

* [ ] Eventually even later, add a separate file for specific commands to run
      that are even more specific past wildcards, such as a find command for
      example. Or maybe its better to just simply pipe find into
      tmux-sessionizer -a and deal with it that way?
