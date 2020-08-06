# Linux commands cheatsheet

This file contains basic list of Linux commands, utilities, special files and directories, special environment variables, scripting syntax and editor controls. Purpose of this sheet is to provide basic overview of existing principles and available solutions. For in-depth manual on how to use specific command or utility use Linux manual pages (accessible by issuing __man COMMAND__) or issue the command with __--help__ option (vast majority of commands support this).

Feel free to contribute :) 

## User
* __useradd__ 	- create user
* __userdel__ 	- delete user
* __usermod__ 	- change user configuration
* __su__     	- switch user

## Process
* __pgrep__ 	- process grep
* __kill__ 	- process kill (by PID)
* __pkill__ 	- process kill (by name)
* __pstree__ 	- process tree
* __nice__ 	- start process with specific niceness value
* __renice__ 	- change running process niceness value (priority)
* __ulimit__ 	- set process resource limit for current shell
* __crontab__ 	- user's crontab utility
* __systemctl__ - systemd cli

## Filesystem
* __df__ 	- disk free space
* __du__ 	- disk usage
* __fdisk__ 	- low-level disk operations (use with caution!)
* __mkfs__ 	- format disk partition
* __fsck__ 	- check and repair filesystem
* __man hier__ 	- manual for linux filesystem hierarchy

## Network
* __dig__ 	- dns lookup
* __netstat__ 	- show network info
* __ethtool__ 	- ethernet device utility
* __nmap__ 	- map network infrastructure

## Security
* __chage__ 	- password aging

## Files and directories
* File types (as printed by ls):
  * __s__ - socket
  * __l__ - link
  * __d__ - directory
  * __b__ - block (communicates by blocks, e.g. disk)
  * __c__ - character (communicates by character, e.g. keyboard)
* __touch__ 	- create empty file
* __mkdir__ 	- create empty directory
* __rm__ 	- delete file or directory
* __grep__ 	- search for file content
* __find__ 	- search for file name in filesystem
* __tree__ 	- show filesystem tree
* __ldd__ 	- show which dynamic libraries the executable binary file uses

## Backup, compress, archive
* __rsync__ 		- remote sync (remote backup)
* __tar__ 		- create archive
* __gzip/gunzip__ 	- compress/uncompress

## Kernel and drivers
* __lsmod__ 	- list loaded modules
* __lnsmod__ 	- install module
* __rmmod__ 	- remove module
* __modprobe__ 	- load module and any dependency
* __dmesg__ 	- print boot log

## Bash scripting
* function syntax:
  * __FUNCTIONN\_NAME () { COMMANDS; }__ 
    * do not specify parameters, call without ()
    * return value is considered function exit code, function cannot return values
    * by default, all variables are global (even if specified inside the function)
      * local variables are specified with __local__ keyword
    * arguments are passed with separating space, without ()
    * arguments are accesed by __$1, $2, .., $n__, __$0__ is function name
      * __$#__ represents number of arguments
* if statement syntax:
  * __if [[ CONDITION ]]; then COMMANDS; elif [[ CONDITION ]]; then COMMANDS; else COMMANDS; fi__
* case statement syntax:
  * __case EXPRESSION in PATTERN_1) COMMANDS;; \*) DEFAULT_COMMANDS;; esac__
* for loop syntax:
  * __for VARIABLE in LIST; do COMMANDS; done__
* while loop syntax:
  * __while [[ CONDITION ]]; do COMMANDS; done__
* read from stdin syntax:
  * __read VARIABLE__
    * multiple _VARIABLES_ can be specified
* () can be used for:
  * __subshell__ 	- (RES=123) && echo $RES
  * __((1+1))__  	- arithmetic expression
* {} can be used for:
  * __output grouping__		- { echo "A"; echo "B"; echo "C"; }
  * __array building__		- {1..10}
  * __parameter expansion__ 	- ${HOME}
* debug mode
  * __bash -x__ 	- global debug mode for entire script
  * inside script: 
    * __set -x__ 	- turn on debug
    * __set +x__ 	- turn off debug

## Bash basic
* __&&__ 	- logical AND
* __||__ 	- logical OR
* __!!__ 	- execute last command
* __!STRING__ 	- execute last command starting with STRING
* __xargs__ 	- stdout to arguments
* output redirection:
  * __<__ 	- read to stdin from file
  * __>__ 	- write to stdout from file
  * __>>__ 	- append stdout to file
  * __2>__ 	- write stderr to file
  * __&>__ 	- write stderr and stdout to file
  * __2>>__ 	- append stderr to file
  * __&>>__ 	- append stderr and stdout to file

## Bash shortcuts
* __CTRL + L__ 	- clear terminal
* __CTRL + W__ 	- delete last word
* __CTRL + U__ 	- delete line till line start
* __CTRL + E__ 	- move to line end
* __CTRL + A__ 	- move to line start
* __CTRL + R__ 	- reverse history search
* __CTRL + D__ 	- logout
* __ALT + B__ 	- move to last word
* __ALT + F__ 	- move to next word

## String operations
* __tr__ 		- replace or delete characters
* __join__ 		- inner join two files with same field
* __split__ 		- split large file into smaller files with equal line count
* __uniq__ 		- remove duplicate consecutive lines
* __${string:0:n}__ 	- substring from index 0, n characters
* __${string#\*.}__ 	- substring from dot
* __$'string\n'__ 	- ANSI C string
* __awk__ (awk \[command\] \[file\]):
  * __-F__ 	- field separator

## Vim editor
* __0__ 		- move to line start
* __$__ 		- move to line end
* __:0__ 		- move to file start
* __:$__ 		- move to file end
* __:N__ 		- move to line N
* __Page Up/Down__ 	- move one page
* __/PATTERN__ 		- search for pattern
  * __n__ 	- next occurrence
  * __N__ 	- previous occurrence
* __u__ 		- undo
* __:!__ 		- external shell
  * __%__ 	- current file

## Special environment variables
* __RANDOM__ 		- random number
* __HOME__ 		- home directory
* __PWD__ 		- actual directory
* __PS1__ 		- teminal head appearance
* __PATH__ 		- directories which will be searched for executable files
* __LD\_LIBRARY\_PATH__ - directories which will be searched for dynamic libraries

## Linux special files and directories
* __/etc/sudoers__ 		- list of users wha can run sudo
* __/var/spool/cron/crontabs/__ - crontab for every user stored here
* __/etc/cron.d/__ 		- program specific crontabs
* __/etc/crontab__ 		- systemwide crontab with ability to specify user
* __/etc/cron.allow__ 		- whitelist users who can install crontab
* __/etc/group__ 		- list of groups
* __/etc/ld.so.conf__ 		- list of directories which will be searched for dynamic libraries
* __/etc/security/limits.conf__ - global process resource limits
* startup file order at login (for Bash):
  1. __/etc/profile__
  1. __~/.bash\_profile__
  1. __~/.bash\_login__
  1. __~/.bashrc__ (only this one inspected when creating new terminal and already logged in)
