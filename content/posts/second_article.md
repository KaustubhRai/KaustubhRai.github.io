---
title: "CTF's Everything"
date: 2020-05-04T09:31:00+05:30
draft: false
toc: false
images:
tags:
  - cybersecurity
  - HTB
  - CTF
---

College students or most people, in general, are drawn to hacking as they want to feel the rush of excitement that comes from hacking something. Movies and TV shows have not been kind to hacking or how it's done. It requires patience (A LOT).

A CTF is like when a newborn chick is pushed off his nest and he/she learns how to fly and tries to survive, same as is this situation you are given a challenge in a CTF and you are expected to use your skills and find the flag and then through what you have learned you have to apply them to defend your companies against hackers or in *Layman's terms* you can call it a hacking competition.

### What is this?
**CTF** this term is somewhat held in high regards if you run in the cyber-security community. It tests your skills to outthink, outsmart, and most important *out hack* out of any given situation to you. 

A CTF is called Capture The Flag, it's like a puzzle to solve but instead of a puzzle you are given an IP address or some image or some code or some software or **literally anything** and you have to work you way around using Google as your best friend and your skills in Bash Scripting and Linux. Applying real-world hacking tools to infiltrate a computer system, find intentionally placed vulnerabilities, and exploit them to capture a *flag*[^1] . You submit this *flag* so that you get points. 

>![giphy.gif](/giphy.gif)

Each challenge is usually oriented around a single concept.  By solving challenges, you (hopefully!) learn about a new concept, vulnerability, tool, class of attack, etc.
A CTF can be performed individually or in a team(it's hard finding security nerds).

### CTF Styles

There are three common types of CTFs: Jeopardy, Attack-Defence, and mixed.

Most CTFs are “jeopardy style", meaning that there are a handful of categories, and each of the (typically standalone) challenges falls into one of those categories.

The categories vary from CTF to CTF, but typically include:

* RE (Reverse Engineering):  get a binary and reverse engineer it to find a flag.
* PWN:  get a binary and a link to a program running on a remote server.  Cause a buffer overflow, etc. to bypass normal functionality and get the program to read the flag to you.
* Crypto:  crypto means cryptography!  Get an encrypted flag and figure out how to decrypt it (includes both classical and modern ciphers).
* Web:  web-based challenges where you are directed to a website, and you have to find and exploit a vulnerability (SQL injection, XSS, etc.) to get a flag.
* Forensics/Steganography:  given a file, image, audio, or other files, find a hidden message and get the flag.
* Other:  this is a bit of a grab bag.  Includes random puzzles, electronics-based things, OSINT[^2], anything that doesn’t fit into the other categories.

> ![giphy1.gif](/giphy1.gif)

The next task in the chain can be opened only after someone or a team solve the previous task.

Attack-defence is another interesting kind of CTF, can not be done by a single individual it needs a team. Here every team has its's own network(or only one host) with vulnerable services. Your team has time for patching their own services and protecting it while also attacking other servers. You should protect your own services for defense points and hack opponents for attack points. 

Mixed competitions may vary possible formats. It may be something like wargame with special time for task-based elements 

## Logistics and How to Find CTFs

**Wait! Now before you go any further.**

It’s definitely more fun to play with friends or even internet strangers. Playing with other people means that you can help each other, and you can also support each other when you make progress, get a new tool working, or find a flag… or when you don’t.  Especially when you’re new, CTFs can feel like repeatedly banging your head against the wall (there’s so much to learn in this field!). Having others to play alongside can definitely help lift that emotional burden when things aren’t going well, and give you people to celebrate with when you make a breakthrough.

>![giphy2.gif](/giphy2.gif)

There are online groups that are open to beginners. A shortlist includes :
* [_OpenToAll_](https://opentoallctf.github.io/)
* [_Women Hackers_](https://www.womenhackerz.com/)
* [_CTF Circle_](https://twitter.com/CTF_Circle)

You can try Slack/Discord for local security meet-up groups to see if there’s any interest in teaming up. The same goes for university groups, if you’re a student as often there are other people also looking for teammates.

### Where to find CTFs?

There are in-person CTF's throughout the year, plus many at conferences. But also online CTFs, they run for 1-3 days, some go for a week. [_CTF Time_](https://ctftime.org/event/list/upcoming) provides you with a list of upcoming events. Some CTFs and CTF platforms are available online, year-round.
* [OverTheWire "Bandit"](https://overthewire.org/wargames/bandit/) if you want to learn Linux commands through a beginner-friendly game.  It has a number of other great ‘wargames’ as well like Natas, Narnia, Maze. Each wargame has some levels, you pass one level to continue to the other.

* [HTB](https://www.hackthebox.eu/), the most popular platform which includes both “Jeopardy” style challenges and network pen testing VMs for you to attack. You have to *hack* this site just to make an account on this platform (hint: find the login portal). After you do that, try solving the retired machines to gain confidence and then move on to the active ones. 

![pic2.jpg](/pic2.jpg)

All these machines are the easy ones, they are all retired boxes. One thing to keep in mind is while hacking these machines, you have to first connect to them using OpenVPN (I did not know this and it gave me a lot of headaches). Just visit the Starting Point page to understand everything on the platform.

* [picoCTF](https://picoctf.com/) is technically an event in the fall, but the challenges remain open year-round.  This is probably my top recommendation for a beginner Jeopardy-style CTF.

Other multi-category platforms (paid and free) include [Root Me](https://www.root-me.org/?lang=en), [Escalate](https://escalate.today/), [Pen Tester Lab](https://pentesterlab.com/), [24/7 CTF](https://247ctf.com/), [Hacker101](https://ctf.hacker101.com/), and [CTFLearn](https://ctflearn.com/).  There are many more… if you’re a beginner, leverage these to get access to many different types of challenges in each category to determine what you like, and build up a knowledge base (Hacker101 has a few Android challenges).

Now before even trying to attend a CTF or hack a machine, you must know a basic programming language or know your way around a Linux machine. Learning Linux could be hard for some people, [Learn Linux](https://tryhackme.com/room/zthlinux) is a guided room designed to teach you all the Linux basic fundamentals that you need to start.

## And now the Resource List for each category!

#### RE

In industry, RE skills are used for vulnerability research.  You might be given a software program and asked to find vulnerabilities (without having source code).  Similarly, malware research involves a lot of reverse engineering.  It’s a bit more niche than its inclusion in CTFs would lead you to believe, but still a challenging/fun category.
>![giphy3.gif](/giphy3.gif)

It is daunting to get started in reverse engineering, if you have little or no experience in low-level programming languages like assembly. As you get started, try to find something in the code to orient yourself… a call to a standard library function (read, scanf, printf, etc.), comments, strings, etc.
  * **Learning by doing:** [Microcorruption](https://microcorruption.com/login) a game where you try to reverse engineer (fictitious) Bluetooth locks of increasing difficulty.  It’s all in-browser (which means no-tool setup) and has a tutorial level that introduces you to some of the assembly and environment.
  * **Learning by reading:**  Hacking: The Art of Exploitation and then Practical Binary Analysis.  Hacking: The Art of Exploitation takes you from a very basic level through C, assembly, program memory, exploits, and much more.
  * **Learning by watching:**  Live Overflow has a great series on [binary exploitation](https://www.youtube.com/playlist?list=PLhixgUqwRTjxglIswKp9mpkfPNfHkzyeN).  

#### PWN

You’ll be given a program to RE, and a server and port to connect to.  The server is running that same program and has a file that contains the flag (usually called flag.txt).  These challenges are a way to learn about secure coding (typically in C), as some sort of vulnerability will let you redirect the program flow to do something different (give you a flag).  This category is probably what people think of when they think of (stereotypical) hacking.

>![giphy4.webp](/giphy4.webp)

The learning curve is a bit steep as these challenges are more multi-disciplinary. 
  * **Learning by doing:** [Pwnable.kr](https://pwnable.kr/), [pwnable.xyz](https://pwnable.xyz/challenges/) and [pwnable.tw](https://pwnable.tw/) are all geared towards beginners.
  * **Learning by reading:**  Same as RE.
  * **Learning by watching:**  Same as RE. 

#### Crptography 

Encrypting (and decrypting) data in order to allow for its secure transmission and storage.
Most challenges revolve around either decrypting a ciphertext using a classical cipher (Caesar, Vignere, etc.) or finding a flaw in the implementation of a modern cipher.

While jobs in cryptography are pretty niche (NSA?), knowing how cryptography works can be very beneficial to those developing software, or playing defense, as exploiting human error (in implementation) is far more likely than exploiting a flaw in a proven cryptographic system. That’s why you should “never roll your own crypto.”  : )

>![giphy4.gif](/giphy4.gif)

  * **Learning by doing:**  If you have the patience to learn to program while also learning cryptography, visit [CryptoPals](https://cryptopals.com/). It’s a step-by-step set of exercises that “demonstrate attacks on real-world crypto.”  Think [Project Euler](https://projecteuler.net/), but for cryptography.

  * **Learning by reading:**  The Code Book, it’s a cat-and-mouse type story about cryptography through the ages, it’s not super technical but really fun. A more technical introduction, check out Crypto 101, a free PDF book.  Then, if you still want more, check out No Starch Press’ Serious Cryptography.

  * **Learning by watching:** [Christof Paar’s Introduction to Cryptography videos](https://www.youtube.com/channel/UC1usFRN4LCMcfIV7UjHNuQg/videos), there’s also a [Coursera Cryptography Series](https://www.coursera.org/learn/crypto/) offered by Standford.

 #### Web

 This covers any sort of web-based vulnerabilities and exploits.  This includes different forms of injection, cross-site scripting (XSS), cross-site request forgery (CSRF), insecure direct object references (IDOR), and so on.

 In terms of the InfoSec industry, web hacking could get you a job in AppSec (application security) or web-based pen-testing.  It might also be useful to those who want to do bug bounty, as several bounty programs focus on web targets.   If you’re a web developer, then developing web hacking skills could help you create a more secure code in your job.

  * **Learning by doing:**  OWASP has a number of intentionally vulnerable projects.  One of which is [JuiceShop](https://owasp.org/www-project-juice-shop/), an intentionally vulnerable website that teaches you about many common web vulnerabilities.  You can download the image from their website, and run it locally (or deploy it somewhere like Heroku).

  * **Learning by reading:**  [Web Application Hacker’s Handbook](https://www.amazon.com/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470)

  * **Learning by watching:** This [introductory course on web hacking](https://www.youtube.com/playlist?list=PLhixgUqwRTjx2BmNF5-GddyqZcizwLLGP) they cover (in varying extents) HTML/CSS/JS, the HTTP protocol, cross-site scripting and cross-site request forgery. Once you get past those, this has [more advanced browser exploitation](https://www.youtube.com/playlist?list=PLhixgUqwRTjwufDsT1ntgOY9yjZgg5H_t). 

#### Forensics / Stego

Steganography (not to be confused with stenography) is the art of concealing a message (or file, image, etc.) within another message (or file, image, etc.).  In CTFs, this category often contains other digital forensics challenges, and might be called either “Stego” or “Forensics”.

In industry, stego and forensics skills can have a wide range of applications including digital forensics, incident response, data loss protection, and malware detection.

This [image](https://drive.google.com/file/d/1Ew4Jq6xavP1gF_i8e2ZQVwuivLKQzlOt/view?usp=sharing) has a flag in it.

P.S - I wasn't able to solve this problem in an in-person CTF if anyone of you is able to, share it :stuck_out_tongue_closed_eyes: .

  * **Learning by doing:**  A multi-category site like PicoCTF and Hack The Box and try some stego challenges.

  * **Learning by reading:**  [Trail of Bits](https://trailofbits.github.io/ctf/forensics/) has a fantastic CTF guide that will cover some basic stego concepts.

  * **Learning by watching:**  Welp I’m lacking ideas here.  : (   Send me a link if you know of a good beginner stego/forensics series online!

    > ![giphy5.gif](/giphy5.gif)

### TL;DR and thoughts

1. CTFs are competitions that teach you hacking skills through different types of challenges.
2. Jeopardy-style CTFs are the most common and typically cover five major categories:  RE, Pwn, Crypto, Web, and Stego.
3. If you don’t know what category/categories interest you, try a bit of everything and then deep dive into your favorite areas.
4. CTFs are more fun when you do them with friends!

Don’t be discouraged if (when) you get stuck.  Everyone starts somewhere, and even if you don’t solve a challenge, you can still learn something valuable and gain enough knowledge that the next challenge is a bit easier.  Infosec is a huge field that draws upon many different skills, and there’s a lot to learn. I'm just a UNI student and I've got a long road ahead. And as always, Google ftw.

Happy CTFing!

  >![giphy6.gif](/giphy6.gif)

[^1]: flag - a string of code that proves you discovered the flaw.
[^2]: OSINT - the art of googling to find something useful about something or somebody