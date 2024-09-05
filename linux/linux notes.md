# Linux Commands Cheat Sheet

## Basic Commands

| Command      | Description                                 | Example                    |
|--------------|---------------------------------------------|----------------------------|
| `ls`         | List directory contents                     | `ls -l`                     |
| `cd`         | Change directory                            | `cd /home/user/Documents`   |
| `pwd`        | Print working directory                     | `pwd`                       |
| `touch`      | Create an empty file                        | `touch myfile.txt`          |
| `mkdir`      | Create a directory                          | `mkdir myfolder`            |
| `cp`         | Copy files or directories                   | `cp file.txt /home/user/`   |
| `mv`         | Move or rename files or directories         | `mv oldname.txt newname.txt`|
| `rm`         | Remove files or directories                 | `rm myfile.txt`             |
| `cat`        | Display the contents of a file              | `cat myfile.txt`            |
| `echo`       | Display a message or append text to a file  | `echo "Hello" > file.txt`   |
| `man`        | Display the manual of a command             | `man ls`                    |

## File Permissions

Linux file permissions are represented by a set of numbers or symbols that define what actions users can perform on a file or directory.

| Permission Number | Permission Type | Explanation                      |
|-------------------|-----------------|----------------------------------|
| `0`               | No permission   | Cannot read, write, or execute   |
| `1`               | Execute         | Can run the file as a program    |
| `2`               | Write           | Can edit the file                |
| `4`               | Read            | Can view the file's contents     |

These numbers can be combined to form different permission levels:

| Permission Number | Meaning            | Example                       |
|-------------------|--------------------|-------------------------------|
| `7`               | Read, Write, Execute | Full permissions (rwx)        |
| `6`               | Read, Write         | Can read and write (rw-)       |
| `5`               | Read, Execute       | Can read and execute (r-x)     |
| `4`               | Read only           | Can only read (r--)            |
| `0`               | No permission       | No access (---)                |

You set permissions with the `chmod` command:

| Command           | Description                                | Example                            |
|-------------------|--------------------------------------------|------------------------------------|
| `chmod 755 file.txt` | Set permissions (owner: read/write/execute, group: read/execute, others: read/execute) | `chmod 755 script.sh` |

## User and Group Management

| Command       | Description                                | Example                              |
|---------------|--------------------------------------------|--------------------------------------|
| `adduser`     | Create a new user                          | `sudo adduser newuser`               |
| `deluser`     | Delete a user                              | `sudo deluser username`              |
| `groupadd`    | Create a new group                         | `sudo groupadd newgroup`             |
| `usermod`     | Modify user details (e.g., change user group) | `sudo usermod -aG newgroup username` |
| `gpasswd`     | Add a user to a group                      | `sudo gpasswd -a username groupname` |
| `groups`      | Show groups a user belongs to              | `groups username`                    |

## Ownership and Group Changes

| Command           | Description                               | Example                                |
|-------------------|-------------------------------------------|----------------------------------------|
| `chown`           | Change file owner                         | `sudo chown newuser file.txt`          |
| `chown`           | Change file owner and group               | `sudo chown newuser:newgroup file.txt` |
| `chgrp`           | Change group ownership of a file          | `sudo chgrp newgroup file.txt`         |
| `ls -l`           | List files with ownership and permissions | `ls -l`                                |

## File System and Disk Commands

| Command       | Description                                | Example                        |
|---------------|--------------------------------------------|--------------------------------|
| `df`          | Display disk space usage                   | `df -h`                        |
| `du`          | Show disk usage of files and directories   | `du -sh /home/user`            |
| `mount`       | Mount a filesystem                         | `sudo mount /dev/sdb1 /mnt`    |
| `umount`      | Unmount a filesystem                       | `sudo umount /mnt`             |

## Networking and File Transfer

| Command       | Description                                | Example                        |
|---------------|--------------------------------------------|--------------------------------|
| `ping`        | Check connectivity to a server             | `ping google.com`              |
| `ssh`         | Connect to a remote server via SSH         | `ssh user@server.com`          |
| `scp`         | Securely copy files between hosts          | `scp file.txt user@server:/path`|
| `wget`        | Download files from the web                | `wget http://example.com/file.txt` |
| `curl`        | Transfer data from or to a server          | `curl http://example.com`      |

## Process Management

| Command       | Description                                | Example                        |
|---------------|--------------------------------------------|--------------------------------|
| `ps`          | Display currently running processes        | `ps aux`                       |
| `top`         | Display real-time system processes         | `top`                          |
| `kill`        | Terminate a process                        | `kill 1234`                    |
