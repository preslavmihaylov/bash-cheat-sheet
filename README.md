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
    * \<command\> | tee \<file1\> \<file2\>...  
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
  
## Basic usage:  
sed '\<range\>\<option\>/\<pattern\>/\<flags\>'  
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
  
# Viewing Hardware Information  
  
lscpu - info about CPU  
lsmod - info about currently loaded kernel modules  
lsblk - info about block devices (e.g. partitions)  
lspci - info about pci devices (peripherals & controllers)  
lsscsi - info about hard disk/ssd devices  
lsusb - info about usb devices  
  
# Managing shared libaries  
  
ldd <executable> - see shared libraries the executable is dependent upon  
ldconfig - updates local system cache with shared libaries on system  
* use when a new shared library is added  
  
## Configuration  
/etc/ld.so.conf.d/\*.conf - include path for all shared libraries on system  
  
# Debian package management  
  
/etc/apt - location for apt configuration files (e.g. list of repositories)  
/etc/apt/sources.list - a repository list that comes with our distro  
/etc/apt/sources.list.d/\*.list - store all third-party repositories here  

## Using apt to manage packages
apt install <package> - install deb package with dependencies  
apt install -d <package> - only download package + dependencies, without installing  
apt install -f - search installed packages and finish installing unconfigured packages  
* Used to fix dependency problems from installing with dpkg  

apt update - refresh the list of packages taken from repos  
apt upgrade - upgrade the packages installed on the system  
apt dist-upgrade - upgrade to latest distro  

apt remove <package> - remove package without conf files  
apt purge <package> - remove app AND related configuration files  

## Using apt-cache to search repo of installed packages
apt-cache search <name> - search repos for given package  
apt-cache show <package-name> -detailed info about package  

## Using dpkg to manually install .deb packages
dpkg vs. apt - dpkg only installs package, apt installs package along with dependencies  

dpkg -i (--install) <package> - install a package  
* dpkg -i --force-reinstreq - force reinstalling a package (overwrite all config files and package related files)  

dpkg -c (--contents) <package> - show files contained in package (and where they will get installed  
dpkg -S (--search) <keyword> - search for keyword in all installed packages  
dpkg -L (--listfiles) <package> - similar to --contents, but for already installed packages  
dpkg -P (--purge) <package> - remove package along with conf files  

dpkg-reconfigure <package> - run external configuration of package if any and overwrite the existing one  
* e.g. postfix package - runs a GUI window after installation for configuring mail server  

# Red Hat Package management
yum - analog to apt-get  
rpm - analog to dpkg  

/etc/yum.conf - main yum configuration file  
/etc/yum.repos.d/ - location of yum repositories  
* gpgcheck - an option of a yum repository. Verifies that a package comes from a given repo with a gpgkey. Security against man in the middle attacks.  

/var/log/yum.log - log file for the yum package manager  

yum update (same as upgrade) == apt-get update && apt-get upgrade  
yum install == apt-get install  
yum install --downloadonly - only download package without installing  
* Downloaded packages are located in /var/cache/yum/(x86\_64/base/packages). (Specified in /etc/yum.conf)  

yumdownloader - yum util tool for downloading packages

yumdownloader --source <package> - download source only  
yumdownloader --urls <package> - urls from where the package will be downloaded  
yumdownloader --resolve <package> - download package and dependencies  
yumdownloader --destdir <dir> <package> - specify destination directory  

## Using rpm to install .rpm packages
/var/lib/rpm - location of rpm database

rpm -i (--install) <package> - install rpm package  
* -v (--verbose) - verbose mode  
* -h (--hash) - see status bar  
* --nodeps - ignore dependencies  

rpm -e <package> - remove rpm package  

rpm -q <package> - query for package. Check if installed  
* -i - detailed info about package  
* -l - info about installed files on system  
* -R - see dependencies  
* -p - provide info about package even if not installed. NOTE: The full path to .rpm file is needed then.  

rpm -V <package> - difference between original package and installed package  

rpm -U <package> - update installed .rpm package to new version (the provided package should be the newer version)/
If rpm package does not exists, it acts like an installation.

rpm2cpio - archive .rpm package in a cpio. Used to extract rpm packages on a non-redhat system and later manually install.  
* Use `cpio` command to extract archive in current directory  

# Environment variables
set - show bash settings + environment variables  
env - show environment variables  
shopt - show bash settings  

PATH - env variable with info about directories to look for executables  
HIST\_FILE - location of bash history file  
HISTCONTROL - Bash history options  
HISTFILESIZE - count of commands to record in history  

