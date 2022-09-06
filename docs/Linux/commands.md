# Linux Commands

## Links

[Command Cheat Sheet](https://lira.epac.to/DOCS-TECH/Hacking/KALI%20LINUX%20COMMANDS.pdf)

## Commands

```bash
updatedb
locate [file]
passwd
man [command]
[command] --help
```

[Creating a Bootable Windows USB from ISO on a Mac · GitHub](https://gist.github.com/bmatcuk/fda5ab0fb127e9fd62eaf43e845a51c3)

diskutil eraseDisk MS-DOS "WIN10" GPT /dev/disk2
diskutil unmountDisk /dev/disk2
sudo dd if=/Users/kube_k/Downloads/windows10/W10X64.OFF19.pl-PL.JUN2019.ISO | pv -s 64GB | sudo dd of=/dev/disk2 bs=1m


| command |        descripion       |
|:-------:|:-----------------------:|
| apt-get | Search for and install software packages (Debian) |
 | aptitude | Search for and install software packages (Debian) |
 | aspell | Spell Checker |
 | awk | Find and Replace text, database sort/validate/index |
| basename | Strip directory and suffix from filenames |
 | bash | GNU Bourne-Again Shell |
 | bc | Arbitrary precision calculator language |
 | bg | Send to background |
 | break | Exit from a loop |
 | builtin | Run a shell builtin |
 | bzip2 | Compress or decompress named files |
 | cal | Display a calendar |
 | case | Conditionally perform a command |
 | cat | Concatenate and print (display) the content of files |
 | cd | Change Directory |
 | cfdisk | Partition table manipulator for Linux |
 | chgrp | Change group ownership |
 | chkconfig | System services (runlevel) |
 | chmod | Change access permissions |
 | chown | Change file owner and group |
 | chroot | Run a command with a different root directory |
 | cksum | Print CRC checksum and byte counts |
 | clear | Clear terminal screen |
 | cmp | Compare two files |
 | comm | Compare two sorted files line by line |
 | command | Run a command – ignoring shell functions |
 | continue | Resume the next iteration of a loop |
 | cp | Copy one or more files to another location |
 | cron | Daemon to execute scheduled commands |
 | crontab | Schedule a command to run at a later time |
 | csplit | Split a file into context-determined pieces |
 | cut | Divide a file into several parts |
 | date | Display or change the date and time |
 | dc | Desk Calculator |
 | dd | Convert and copy a file, write disk headers, boot records |
 | ddrescue | Data recovery tool |
 | declare | Declare variables and give them attributes |
 | df | Display free disk space |
 | diff | Display the differences between two files |
 | diff3 | Show differences among three files |
 | dig | DNS lookup |
 | dir | Briefly list directory contents |
 | dircolors | Colour setup for `ls’ |
 | dirname | Convert a full pathname to just a path |
 | dirs | Display list of remembered directories |
 | dmesg | Print kernel & driver messages |
 | du | Estimate file space usage |
 | echo | Display message on screen |
 | egrep | Search files for lines that match an extended expression |
 | eject | Eject removable media |
 | enable | Enable and disable builtin shell commands |
 | env | Environment variables |
 | ethtool | Ethernet card settings |
 | eval | Evaluate several commands/arguments |
 | exec | Execute a command |
 | exit | Exit the shell |
 | expand | Convert tabs to spaces |
 | expect | Automate arbitrary applications accessed over a terminal |
 | export | Set an environment variable |
 | expr | Evaluate expressions |
 | fdformat | Low-level format a floppy disk |
 | fdisk | Partition table manipulator for Linux |
 | fg | Send job to foreground |
 | fgrep | Search files for lines that match a fixed string |
 | file | Determine file type |
 | find | Search for files that meet a desired criteria |
 | fmt | Reformat paragraph text |
 | fold | Wrap text to fit a specified width |
 | for | Expand words, and execute commands |
 | format | Format disks or tapes |
 | free | Display memory usage |
 | fsck | File system consistency check and repair |
 | ftp | File Transfer Protocol |
 | function | Define Function Macros |
 | fuser | Identify/kill the process that is accessing a file |
| gawk | Find and Replace text within files |
 | getopts | Parse positional parameters |
 | grep | Search files for lines that match a given pattern |
 | groupadd | Add a user security group |
 | groupdel | Delete a group |
 | groupmod | Modify a group |
 | groups | Print group names a user is in |
 | gzip | Compress or decompress named files |
| hash | Remember the full pathname of a name argument |
 | head | Output the first part of files |
 | help | Display help for a built-in command |
 | history | Command History |
 | hostname | Print or set system name |
 | iconv | Convert the character set of a file |
 | id | Print user and group id’s |
 | if | Conditionally perform a command |
 | ifconfig | Configure a network interface |
 | ifdown | Stop a network interface |
 | ifup | Start a network interface up |
 | import | Capture an X server screen and save the image to file |
 | install | Copy files and set attributes |
| jobs | List active jobs |
 | join | Join lines on a common field |
 | kill | Stop a process from running |
 | killall | Kill processes by name |
 | less | Display output one screen at a time |
 | let | Perform arithmetic on shell variables |
 | ln | Create a symbolic link to a file |
 | local | Create variables |
| locate | Find files |
 | logname | Print current login name |
 | logout | Exit a login shell |
 | look | Display lines beginning with a given string |
 | lpc | Line printer control program |
 | lpr | Off line print |
 | lprint | Print a file |
 | lprintd | Abort a print job |
 | lprintq | List the print queue |
 | lprm | Remove jobs from the print queue |
 | ls | List information about files |
 | lsof | List open files |
 | make | Recompile a group of programs |
 | man | Help manual |
 | mkdir | Create new folders |
 | mkfifo | Make FIFOs (named pipes) |
 | mkisofs | Create an hybrid ISO9660/JOLIET/HFS filesystem |
 | mknod | Make block or character special files |
 | mmv | Mass Move and rename files |
 | more | Display output one screen at a time |
 | mount | Mount a file system |
 | mtools | Manipulate MS-DOS files |
 | mtr | Network diagnostics (traceroute/ping) |
 | mv | Move or rename files or directories |
 | netstat | Networking information |
 | nice | Set the priority of a command or job |
 | nl | Number lines and write files |
 | nohup | Run a command immune to hangups |
 | notify-send | Send desktop notifications |
 | nslookup | Query Internet name servers interactively |
 | op | Operator access |
 | open | Open a file in its default application |
 | passwd | Modify a user password |
 | paste | Merge lines of files |
 | pathchk | Check file name portability |
 | ping | Test a network connection |
 | pkill | Stop processes from running |
 | popd | Restore the previous value of the current directory |
 | pr | Prepare files for printing |
 | printcap | Printer capability database |
 | printenv | Print environment variables |
 | printf | Format and print data |
 | ps | Process status |
 | pushd | Save and then change the current directory |
 | pwd | Print Working Directory |
 | quota | Display disk usage and limits |
 | quotacheck | Scan a file system for disk usage |
 | quotactl | Set disk quotas |
 | ram | ram disk device |
 | rcp | Copy files between two machines |
 | read | Read a line from standard input |
 | readarray | Read from stdin into an array variable |
 | readonly | Mark variables/functions as readonly |
 | reboot | Reboot the system |
 | remsync | Synchronize remote files via email |
 | rename | Rename files |
 | renice | Alter priority of running processes |
 | return | Exit a shell function |
 | rev | Reverse lines of a file |
 | rm | Remove files |
 | rmdir | Remove folders |
 | rsync | Remote file copy (Synchronize file trees) |
 | scp | Secure copy (remote file copy) |
 | screen | Multiplex terminal, run remote shells via ssh |
 | sdiff | Merge two files interactively |
 | sed | Stream Editor |
 | select | Accept keyboard input |
 | seq | Print numeric sequences |
 | set | Manipulate shell variables and functions |
 | sftp | Secure File Transfer Program |
 | shift | Shift positional parameters |
 | shopt | Shell Options |
 | shutdown | Shutdown or restart linux |
 | sleep | Delay for a specified time |
 | slocate | Find files |
 | sort | Sort text files |
 | source | Run commands from a file |
 | split | Split a file into fixed-size pieces |
 | ssh | Secure Shell client (remote login program) |
 | strace | Trace system calls and signals |
 | su | Substitute user identity |
 | sudo | Execute a command as another user |
 | sum | Print a checksum for a file |
 | suspend | Suspend execution of this shell |
 | symlink | Make a new name for a file |
 | sync | Synchronize data on disk with memory |
 | tail | Output the last part of file |
 | tar | Tape Archiver |
 | tee | Redirect output to multiple files |
 | test | Evaluate a conditional expression |
 | time | Measure Program running time |
 | times | User and system times |
 | top | List processes running on the system |
 | touch | Change file timestamps |
 | tr | Translate, squeeze, and/or delete characters |
 | traceroute | Trace Route to Host |
 | trap | Run a command when a signal is set(bourne) |
 | true | Do nothing, successfully |
 | tsort | Topological sort |
 | tty | Print filename of terminal on stdin |
 | type | Describe a command |
 | ulimit | Limit user resources |
 | umask | Users file creation mask |
 | umount | Unmount a device |
 | unalias | Remove an alias |
 | uname | Print system information |
 | unexpand | Convert spaces to tabs |
 | uniq | Uniquify files |
 | units | Convert units from one scale to another |
 | unset | Remove variable or function names |
 | unshar | Unpack shell archive scripts |
 | until | Execute commands (until error) |
 | uptime | Show uptime |
 | useradd | Create new user account |
 | usermod | Modify user account |
 | users | List users currently logged in |
 | uudecode | Decode a file created by uuencode |
 | uuencode | Encode a binary file |
 | v | Verbosely list directory contents (`ls -l -b’) |
 | vdir | Verbosely list directory contents (`ls -l -b’) |
 | vi | Text Editor |
 | vmstat | Report virtual memory statistics |
 | wait | Wait for a process to complete |
 | watch | Execute/display a program periodically |
 | wc | Print byte, word, and line counts |
 | wget | Retrieve web pages or files via HTTP, HTTPS or FTP |
 | whereis | Search the user’s $path, man pages and source files for a program |
 | which | Search the user’s $path for a program file |
 | while | Execute commands |
 | who | Print all usernames currently logged in |
 | whoami | Print the current user id and name (`id -un’) |
 | write | Send a message to another user |
 | xargs | Execute utility, passing constructed argument lists |
 | xdg-open | Open a file or URL in the user’s preferred application |
 | yes |  Print a string until interrupted |
