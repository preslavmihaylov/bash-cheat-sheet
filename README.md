# bash-cheat-sheet  
  
# Command Line Shortcuts  
Ctrl-a - go to beginning of line  
Ctrl-e - go to end of line  
  
Ctrl-d - delete one character forward  
Ctrl-h - delete one character backwards  
Ctrl-w - delete the last typed word on cli  
  
Ctrl-k - delete everything after the cursor  
Ctrl-u - delete everything before the cursor  
Ctrl-c - delete currently typed command  
  
Ctrl-l - clear all terminal output while preserving currently typed command  
  
Ctrl-f - go forward one character  
Ctrl-b - go backwards one character  
  
Ctrl-p - same as up arrow. Show last executed command  
  
Ctrl-r - backwards search  

# Useful linux commands

wc - word count  
* wc -l - total lines of file  

cat - concat contents of file  
* E.g. cat file1 file2 - concatenates output of both files

head - show first lines of file  

tail - show last lines of file  

grep - search for pattern in file/text stream  

find - find something in the system  
* Usage: find <location> <flags>  
* Flags: -name, -perm, -type  

whereis - find location of binary  

whoami - who is logged on system  

pwd - current working directory  

diff - check difference between two files  

ls - list contents of directory
* Useful Options:
  * -a - show all files (including hidden)
  * -l - long listing (show extended info for file)

# Grepping

grep - command for filtering lines from stream  
* e.g. grep "hello" hello.txt
* Can use regular expressions
    * e.g. grep "^hello$" hello.txt

### Useful options

-i - case-insensitive search  
-n - show line numbers of matched lines  
-e - grep for several expressions.  
* e.g. grep -e "hello" -e "world" hello.txt

# Manipulating streams

\> - redirect stdin to file (overwriting it)  
>> - redirect stdin to file (appending)  
| - redirect output of left-hand command as input to right-hand command  

