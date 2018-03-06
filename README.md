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
* Usage: find \<location\> \<flags\>  
* Flags: -name, -perm, -type  
  
whereis - find location of binary  
  
whoami - who is logged on system  
  
pwd - current working directory  
  
diff - check difference between two files  
  
ls - list contents of directory  
* Useful Options:  
  * -a - show all files (including hidden)  
  * -l - long listing (show extended info for file)  
  
cut - cut file into columns  
* Options:  
    * -f<num> - the column to display  
    * -d<delim> - the delimiter to use  
* e.g. cut -f1 -d: passwd  
  
tee - read from stdin and write to file AND stdout  
* Usage:  
    * <command> | tee <file1> <file2>...  
* Useful options:  
    * -a - append instead of overwriting  
  
# Grepping  
  
grep - command for filtering lines from stream  
* e.g. grep "hello" hello.txt  
* Can use regular expressions  
    * e.g. grep "^hello$" hello.txt  
  
### Useful options  
  
-i - case-insensitive search  
-n - show line numbers of matched lines  
-f - read expression from file  
-E - extended RegEx  
-F - don't use regex. Treat expression literally  
-e - grep for several expressions.  
* e.g. grep -e "hello" -e "world" hello.txt  
  
egrep == grep -E  
fgrep == grep -F  

# Sed stream editor
sed - command for manipulating streams

Basic usage:
* sed '\<range\>\<option\>/\<pattern\>/\<flags\>'
    * range - define range for sed to operate on
        * e.g. % - operate on all lines
        * e.g. 2, - operate on lines [2, $)
        * e.g. ,5 - operate on lines (^, 5]
        * e.g. 2,5 - operate on lines [2, 5]
    * option - can be one of the following
        * s - substiture matched pattern with something else
        * d - delete line where pattern is found
        * i - insert after line where pattern matched
    * pattern - a single regex expression
        * if s option used - use <pattern>/<replaced> instead of simply <pattern>
    * flags
        * g - global match. Match more than one pattern on a line if applicable.
        * c - ask before performing operation
        * w <file> - write matched patterns operation to file


# Manipulating streams

\> - redirect stdin to file (overwriting it)  
\>\> - redirect stdin to file (appending)  
\| - redirect output of left-hand command as input to right-hand command  

