---
title: "Bandit, OverTheWire Wargames"
date: 2022-07-31T16:29:43+05:30
draft: false
tags: 
    - cybersecurity
    - OverTheWire
    - Bandit
---


My final semester of U.G completed and I wanted to write a blog that helped newcomers to the Infosec field. One of the many ways of going about and understanding things that can help you in CyberSecurity is OverTheWire Wargames.

{{<image src="/OTW_logo.png" alt="OTW_logo" position="center">}}

This war-game Bandit, is targeted to the absolute beginners and teaches the basics of most of the Linux commands and security concepts. And also forms a base to be able to play other wargames by [OverTheWire](https://overthewire.org/). 

Each wargame by OverTheWire has different levels of difficulty and has multiple levels in each wargame. 
Bandit has 33 Levels to solve and it teaches about :
- SSH
- File Structure, Commands, Permissions in Linux
- Bash Scripting
- Git 

    *(I might have missed some of the other stuff in mentioning here)*

The objective of each level is to find a password for the next level and there are some kind of hints or commands that could help you, on the page of that particular level on the OTW Bandit website. 

We use SSH to login in each level be it SSH password or an SSH Key. 

`ssh bandit<username>@bandit.labs.overthewire.org -p 2220` and if ssh key then `ssh -i <ssh key file> bandit<username>@localhost` and then the password you got.

> Level 0 

SSH commands to connect to host 

> Level 1

Read the file present on the current directory and use that as a password for next level. 

> Level 2

Read a file named "-" `cat ./-`

> Level 3

Read the file using `cat ./.hidden`

> Level 4

Above commands and putting file name of each file to check each one of them. 

> Level 5

`ls -laR` the command for viewing permission for each and every file, hidden too. within every directory.

> Level 6 

`ls -laR | grep “bandit7 bandit6”` for searching if there’s a file present like that, after finding the file name, using `find -name <file name>` command to find its path

> Level 7

`grep <keyword>` the keyword in the file

> Level 8

Command to Sort the file and read the unique character in one command 

> Level 9

Command to print only human readable characters and grep the keyword, `cat <filename> | strings | grep <keyword>`

> Level 10

Decode the file, `base64 -d <filename>`

> Level 11

decode the file, rot13 is the encryption. `tr` is the command that translates. `tr 'A-Za-z' 'N-ZA-Mn-za-m'`

> Level 12

Copy the file in tmp directory and continue since no permission to create new files in main directory. `file` command to see what type of file it is and decompress it accordingly to what file type it is. Copy the existing file and create new file with the extension to decompress. 
- hex - xxd, 
- tar: tar -xvf, 
- gzip - .gz, 
- bzip2 - .bz2, 
- POSIX tar - .tar

> Level 13

`ssh -i <ssh key> username@localhost`, localhost since we are working in the same machine.

> Level 14

from the previous level hint, we can read the the password from *“etc/bandit_pass/bandit14”* from this logged in user. 

Store that password in *tmp* directory `nano /tmp/passwd.txt` and netact it to localhost from port 30000, `nc localhost 30000 < /tmp/passwd.txt`

> Level 15

same technique, but now we have to SSL encrypt our connection unlike netcat raw connection. so we use openssl tool. `openssl s_client -connect localhost:30001` and provide the password of this level at the end.

> Level 16

Same as previous level but we are given a range of ports to check which one is up and has SSL. `nmap localhost -A -p 31000-32000`. After getting the port, provide the password through openssl same way as previous level.

make a file in tmp directory and save the ssh key there and change its permission to only read for user. `chmod 400 <file path>`. ssh to bandit17 level using the key.

> Level 17

difference between 2 files, `diff file1 file2`.

> Level 18

.bashrc file is modified to logout instantly when logged in using ssh. There’s a hint that password is stored in *readme* in /home and we can pass another command in the same ssh command when logging in. 

`ssh <username>@<host> -p 2220 ‘cat readme’`

> Level 19

scanning the home directory for files and permission (`ls -la`) gives a binary setuid file that has permissions to run as bandit20 and is turned on. passwords are stored in /etc/bandit_pass directory. so we run the file as a command and simply read the password for its level.

`./bandit20-do cat /etc/bandit_pass/bandit20`

> Level 20

Same as level 19, a setuid binary file but it requires a port number as input. From the hint given we setup a netcat listener in the shell and open another shell and log in as same user and pass the port we gave in the netcat listerner as the input in the setuid file. as per the hint we give the password for level 20 in the netcat shell and if correct then it gives the password for the next level.

> Level 21

Level has a cron job running so we read the file and after examining it we get it runs a script file after every reboot and every minute. After reading the script file, it changes the permissions and redirects the output to */tmp* directory . After reading that file from */tmp* we get the password. 

> Level 22

Same as Level 21, we read the cron file then the script file. The script file has 2 variables. The first variable is the username and the second variable is a md5 value. After running the script the password level 22 get stored in */tmp* directory. We run the second variable separately by passing the username of the next level and we get a new md5 value. we pass that md5 value in the */tmp* directory and read it and we get the next password. 

`echo I am user bandit23 | md5sum | cut -d ' ' -f 1` > (md5 value)

`cat /tmp/(md5 value)`

> Level 23

Read the cron file and the script file. Create a directory in */tmp* and in that directory make a script file. It should read the password for the next level and pass it to the created directory in */tmp* in a new file

`#!/bin/bash`

`cat /etc/bandit_pass/bandit24 >> /tmp/<new directory>/level24`

> Level 24

A daemon is listening on port 30002 and it asks for the password of the current level and a 4 digit PIN. We create a directory in */tmp* and create a script file that uses for loop for numbers 0000-9999 to check which is the right one.

>>#!/bin/bash

>>passwd="(level 24 password)"

>>for i in {0000..9999}

>>do

>>echo $passwd' '$i >> output.txt

>>done

give the script file 777 permissions and run it with nc 

`cat output.txt | nc localhost 30002`

> Level 25

ssh key on home directory but exits as soon as logged in with bandit26. After checking the /etc/passwd file it redirects to /usr/bin/showtext. After reading that file, `~more` command is triggered and it exits when the text case is large. So minimized the shell and try with the ssh key. Can use vim here and show the password for level26 using these commands

`:e /etc/bandit_pass/bandit26`

> Level 26

Will log out once if found the text case is large so minimize the terminal and log in with the password. Go to vim by pressing `v`  and `:set shell = /bin/bash` and then next `:shell` in vim to enter a normal shell. There’s a setuid binary file with special permissions for bandit27. After running the file it runs as shell with bandit27 with an input in the command so 

`./bandit27-do cat /etc/bandit_pass/bandit27`

> Level 27

Hint tells us that we need to git clone and the password is in the repo. Make a directory in */tmp* and give it 777 permissions and git clone the link the hint has. 

> Level 28

Same procedure as the previous level, *mkdir>permissions>git clone>cat README*.

The password text is hidden. So we review the git log by, `git log` to see the commit message and to see what was changed either `git show <commit number>` / `git log -p`. 

Credentials in plain text were removed but it still got stored in the commit log.

> Level 29

Same procedure, level 27. After reading the README it gives a hint that no passwords on production, means there are other branches and we can view all branches in a repo by `git branch -a`. The dev branch might have non production code and might have the password, so `git checkout dev` and `cat README`.

> Level 30

Same procedure, *file>permissions>git clone>cat README*. Gits Logs has nothing too, Git saves some things from its history by giving them a tag if it deems it important. `git tag` . `git show <tag name>`

> Level 31

Same procedure. This time the README gives hint that we need to create and push a file and the file’s content. Simple Git commands here. 

> Level 32

Every command get converted into uppercase here. We need to use escape character to bypass this uppercase shell. Like `/bin/bash` is used to invoke shell, `$0` can also be used. 

> Level 33

*NOT EXISTS YET*





