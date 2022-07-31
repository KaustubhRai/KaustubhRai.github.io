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
- File Structure, Commands , Permissions in Linux
- Bash Scripting
- Git
    *(I might have missed some of the other stuff in mentioning here)*

The objective of each level is to find a password for the next level. 

We use SSH to login in each level be it SSH password or an SSH Key. 
`ssh bandit<username>@bandit.labs.overthewire.org -p 2220` and if ssh key then `ssh -i <ssh key> bandit<username>@localhost`