# Bash

Graphical user interfaces are super friendly to computer users. They were introduced in reaction to the perceived steep learning curve of command-line interfaces (CLIs).

However, they often require more resources, are less powerful and hard to automate via scripting.

As a computer expert, we want to be more efficient and do our jobs better. We know that command words may not be easily discoverable or mnemonic, so we try to list some common tasks that you might be tempted to do in GUI.

## Copy a file

Copy `readme.txt` to the `documents` directory

```shell
$ cp readme.txt documents/
```

## Duplicate a file

```shell
$ cp readme.txt readme.bak.txt
```
More advanced:
```shell
$ cp readme{,.bak}.txt
# Note: learn how the {} works with touch foo{1,2,3}.txt and see what happens.
```

## Copy a directory

Copy `myMusic` directory to the `myMedia` directory

```shell
$ cp -a myMusic myMedia/
# or
$ cp -a myMusic/ myMedia/myMusic/
```

## Duplicate a directory

```shell
$ cp -a myMusic/ myMedia/
# or if `myMedia` folder doesn't exist
$ cp -a myMusic myMedia/
```

## Move a file

```shell
$ mv readme.txt documents/
```

Always use a trailing slash when moving files, [for this reason](http://unix.stackexchange.com/a/50533).

## Rename a file

```shell
$ mv readme.txt README.md
```

## Move a directory

```shell
$ mv myMedia myMusic/
# or
$ mv myMedia/ myMusic/myMedia
```

## Rename a directory

```shell
$ mv myMedia/ myMusic/
```

## Merge directories

```shell
$ rsync -a /images/ /images2/	# note: may over-write files with the same name, so be careful!
```

## Create a new file

```shell
$ touch 'new file'    # updates the file's access and modification timestamp if it already exists
# or
$ > 'new file'        # note: erases the content if it already exists
```

## Create a new directory

```shell
$ mkdir 'untitled folder'
# or
$ mkdir -p 'path/may/not/exist/untitled\ folder'
```

## Show file/directory size

```shell
$ du -sh node_modules/
```

## Show file/directory info

```shell
$ stat -x readme.md   # on macOS
$ stat readme.md      # on Linux
```

## Open a file with the default program

```shell
$ xdg-open file   # on Linux
$ open file       # on MacOS
```

## Zip a directory

```shell
$ zip -r archive_name.zip folder_to_compress
```

## Unzip a directory

```shell
$ unzip archive_name.zip
```

## Peek files in a zip file

```shell
$ zipinfo archive_name.zip
# or
$ unzip -l archive_name.zip
```

## Remove a file

```shell
$ rm my_useless_file
```

IMPORTANT: The rm command deletes my_useless_file permanently, which is equivalent to move my_useless_file to Recycle Bin and hit Empty Recycle Bin.

## Remove a directory

```shell
$ rm -r my_useless_folder
```

## List directory contents

```shell
$ ls my_folder        # Simple
$ ls -la my_folder    # -l: show in list format. -a: show all files, including hidden. -la combines those options.
$ ls -alrth my_folder # -r: reverse output. -t: sort by time (modified). -h: output human-readable sizes.
```

## Tree view a directory and its subdirectories

```shell
$ tree                                                        # on Linux
$ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'      # on MacOS
# Note: install homebrew (https://brew.sh) to be able to use (some) Linux utilities such as tree.
# brew install tree
```

## Find a stale file

Find all files modified more than 5 days ago

```shell
$ find my_folder -mtime +5
```

## Show a calendar

Display a text calendar

```shell
$ cal
```
Display selected month and year calendar

```shell
$ cal 11 2018
```

## Find a future date

What is todays date?

```shell
$ date +%m/%d/%Y
```

What about a week from now?

```shell
$ date -d "+7 days"                                           # on Linux
$ date -j -v+7d                                               # on MacOS
```

## Use a calculator

```shell
$ bc
```

## Force quit a program

```shell
$ killall program_name
```

## Check server response

```shell
curl -i umair.surge.sh
# curl's -i (--include) option includes HTTP response headers in its output.
```

## View content of a file

```shell
$ cat apps/settings.py
# if the file is too big to fit on one page, you can use a 'pager' (less) which shows you one page at a time.
$ less apps/settings.py
```

## Search for a text

```shell
$ grep -i "Query" file.txt
```


## View an image

```shell
$ imgcat image.png
# Note: requires iTerm2 terminal.
```

## Show disk size

```shell
$ df -h
```

## Check performance of your computer

```shell
$ top
```


## Hotkeys

```
Ctrl + A  Go to the beginning of the line you are currently typing on
Ctrl + E  Go to the end of the line you are currently typing on
Ctrl + L  Clears the Screen, similar to the clear command
Ctrl + U  Clears the line before the cursor position. If you are at the end of the line, clears the entire line.
Ctrl + H  Same as backspace
Ctrl + R  Lets you search through previously used commands
Ctrl + C  Kill whatever you are running
Ctrl + D  Exit the current shell
Ctrl + Z  Puts whatever you are running into a suspended background process. fg restores it.
Ctrl + W  Delete the word before the cursor
Ctrl + K  Clear the line after the cursor
Ctrl + T  Swap the last two characters before the cursor
Esc + T   Swap the last two words before the cursor
Alt + F   Move cursor forward one word on the current line
Alt + B   Move cursor backward one word on the current line
Tab       Auto-complete files and directory names
```

## I can't remember these cryptic commands

You can always google or `man` the commands you are not familiar with. Or, checkout [tldr](https://github.com/tldr-pages/tldr), a collection of simplified and community-driven man pages.
