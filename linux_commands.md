# Linux commands cheatsheet

## User
* __useradd__ - create user
* __userdel__ - delete user
* __usermod__ - change user configuration
* __su__ - switch user

## Process
* __pgrep__ - process grep
* __pkill__ - process kill (by name)
* __pstree__ - process tree
* __nice__ - start process with specific niceness value
* __renice__ - change running process niceness value (priority)
* __ulimit__ - set process resource limit for current shell
* __crontab__ - user's crontab utility
* __systemctl__ - systemd cli

## Filesystem
* __df__ - disk free space
* __du__ - disk usage
* __fdisk__ - low-level disk operations (use with caution!)
* __mkfs__ - format disk partition
* __fsck__ - check and repair filesystem
* __man hier__ - manual for linux filesystem hierarchy

## Network
* __dig__ - dns lookup
* __netstat__ - show network info
* __ethtool__ - ethernet device utility
* __nmap__ - map network infrastructure

## Security
* __chage__ - password aging

## Files and directories
* File types (as printed by ls):
  * __s__ - socket
  * __l__ - link
  * __d__ - directory
  * __b__ - block (communicates by blocks, e.g. disk)
  * __c__ - character (communicates by character, e.g. keyboard)
* __touch FILENAME__ - create empty file
* __mkdir DIRNAME__ - create empty directory
* __rm__ - delete file or directory
* __grep__ - search for file content
* __find__ - search for file name in filesystem
* __tree__ - show filesystem tree
* __ldd__ - show which dynamic libraries the executable binary file uses

## Backup, compress, archive
* __rsync__ - remote sync (remote backup)
* __tar__ - create archive
* __gzip/gunzip__ - compress/uncompress

## Kernel and drivers
* __lsmod__ - list loaded modules
* __lnsmod__ - install module
* __rmmod__ - remove module
* __modprobe__ - load module and any dependency
* __dmesg__ - print boot log

## Bash scripting
* __function () {}__ - do not specify parameters, call without ()
* __if [[ CONDITION ]]; then COMMANDS; elif [[ CONDITION ]]; then COMMANDS; else COMMANDS; fi__
* __case EXPRESSION in PATTERN_1) COMMANDS;; \*) DEFAULT_COMMANDS;; esac__
* __for VARIABLE in LIST; do COMMANDS; done__
* __while [[ CONDITION ]]; do COMMANDS; done__
* __read VARIABLE__ - read from STDIN to VARIABLE
* () can be used for:
  * __subshell__: (RES=123) && echo $RES
  * __((1+1))__: arithmetic expression
* {} can be used for:
  * __output grouping__: { echo "A"; echo "B"; echo "C"; }
  * __array building__: {1..10}
  * __parameter expansion__: ${HOME}
* __bash -x__ - debug mode
  * inside script: __set -x__ - turn on debug, __set +x__ - turn off debug

## Bash basic
* __&&__ - logical AND
* __||__ - logical OR
* __!!__ - execute last command
* __!STRING__ - execute last command starting with STRING
* __xargs__ - stdout to arguments
* output redirection:
  * __<__ - read to stdin from file
  * __>__ - write to stdout from file
  * __>>__ - append stdout to file
  * __2>__ - write stderr to file
  * __&>__ - write stderr and stdout to file
  * __2>>__ - append stderr to file
  * __&>>__ - append stderr and stdout to file

## Bash shortcuts
* __CTRL + L__ - clear terminal
* __CTRL + W__ - delete last word
* __CTRL + U__ - delete line till line start
* __CTRL + E__ - move to line end
* __CTRL + A__ - move to line start
* __CTRL + R__ - reverse history search
* __CTRL + D__ - logout
* __ALT + B__ - move to last word
* __ALT + F__ - move to next word

## String operations
* __tr__ - replace or delete characters
* __join__ - inner join two files with same field
* __split__ - split large file into smaller files with equal line count
* __uniq__ - remove duplicate consecutive lines
* __${string:0:n}__ - substring from index 0, n characters
* __${string#\*.}__ - substring from dot
* __$'string\n'__ - ANSI C string
* __awk__ (awk \[command\] \[file\]):
  * __-F__ - field separator

## Vim editor
* __0__ - move to line start
* __$__ - move to line end
* __:0__ - move to file start
* __:$__ - move to file end
* __:N__ - move to line N
* __Page Up/Down__ - move one page
* __/PATTERN__ - search for pattern
  * __n__ - next occurrence
  * __N__ - previous occurrence
* __u__ - undo
* __:!__ - external shell
  * __%__ - current file

## Special environment variables
* __RANDOM__ - random number
* __HOME__ - home directory
* __PWD__ - actual directory
* __PS1__ - teminal head appearance
* __PATH__ - directories which will be searched for executable files
* __LD\_LIBRARY\_PATH__ - directories which will be searched for dynamic libraries

## Linux special files and directories
* __/etc/sudoers__ - list of users wha can run sudo
* __/var/spool/cron/crontabs/__ - crontab for every user stored here
* __/etc/cron.d/__ - program specific crontabs
* __/etc/crontab__ - systemwide crontab with ability to specify user
* __/etc/cron.allow__ - whitelist users who can install crontab
* __/etc/group__ - list of groups
* __/etc/ld.so.conf__ - list of directories which will be searched for dynamic libraries
* __/etc/security/limits.conf__ - global process resource limits
* startup file order at login (for Bash):
  1. __/etc/profile__
  1. __~/.bash\_profile__
  1. __~/.bash\_login__
  1. __~/.bashrc__ (only this one inspected when creating new terminal and already logged in)
