Linux began in 1991 as a personal project by Finnish student Linus Torvalds to create a new free operating system kernel. The resulting Linux kernel has been marked by constant growth throughout its history. [Wikipedia](https://en.wikipedia.org/wiki/History_of_Linux)

### echo

```zsh
echo Hello Linux
```

```zsh
os = Linux
echo Hello $os
```


*echo other than just printing a text or a variable's value?*
###### echo as ls
```zsh
echo *
```

```zsh
ls | grep txt 
```
This command can equivalently be done by ...
```zsh
echo *.txt

```

###### echo to write on or overwrite a file
```zsh
echo Hello linux >> text.txt
```

### find

- A command used to find over files and directories across the file system, or a given directory for a given name or expression 

```zsh
find [options] [path...] [expression]
```

One can find files
- by name -name text
- by extension -name '.pdf'
- by type -type f
- by size -size 21M
- by modification date -mtime 5
- by permission -perm 777
- by owner -user kal
[For more](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/)

### grep
(Global Regular Expression Print)
- command line utility that searches for a specific text string in one or more files.
```zsh
grep [OPTIONS] PATTERN [FILE...]

```

*Example*
```zsh
 grep "THM" access.log 
```
this command finds the pattern "THM" in a file acesss.log and prints out the line that contains that expression if any.

### Shell Operators

| Symbol/Operator | Description                                                                                                                                              |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| &               | This operator allows you to run commands in the background of your terminal.                                                                             |
| &&              | This operator allows you to combine multiple commands together in one line of your  terminal.                                                            |
| >               | This operator is a redirector - meaning that we can take the output from a command (such         as using cat to output a file) and direct it elsewhere. |
| >>              | This operator does the same function of the > operator but appends the output rather than replacing (meaning nothing is overwritten).<br>                |
