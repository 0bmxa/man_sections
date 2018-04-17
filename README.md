# man_sections
A wrapper around `man` to show in which sections the command is available.

## What it does
You type `man somecooltool` as usual. Now, if `somecooltool` has an entry in multiple man sections, instead of opening the first one only, this tool tells you like so:
```
$ man tty
Manual entry for tty found in sections 1, and 4.
```

To then open one of those sections, you explicitly specify the section, as always:
```
$ man 4 tty
```


If your command is found only once, its man page is opened directly, but you get informed where it has been found (visible only after you closed the man viewer, obviously).
```
$ man rm
# [Man viewer open now]
Manual entry for rm found in section 1 only.
```


## Installation
Copy the [man script file](man) somewhere into your `$PATH` before the real `man` command. That's it. 

Optionally, you might also want to adapt the `ORIGINAL_MAN='/usr/bin/man'` variable to reflect the path to your original `man`.


## It doesnt work!!!
* Make sure this script really sits somewhere in your `$PATH`, and that this location is also found _before_ your the location of your real man. You might want to verify this with `which man`.
* Commands which only occur in one section (like `man ls`) open the man viewer directly, as usual.


## Caveats / ToDo
* This tool calls the original `man` command 9 times on each invocation. Checking the relevant locations directly might be more efficient
* It makes use of non-`sh` arrays, so the shebang is set to `zsh` right now. There might be a more universal solution.
* Some tab-autocompletion of possible/found sections might be handy, but i have no idea how to do this
