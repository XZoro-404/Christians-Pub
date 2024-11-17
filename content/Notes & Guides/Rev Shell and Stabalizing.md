---
created: 2024-02-02
last_modified_at: 2024-02-04
---
[https://tryhackme.com/room/introtoshells](https://tryhackme.com/room/introtoshells) 

[https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#linux-staged-reverse-tcp](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#linux-staged-reverse-tcp) 

  

Technique 1: Python

The first technique we'll be discussing is applicable only to Linux boxes, as they will nearly always have Python installed by default. This is a three stage process:

1. The first thing to do is use python -c 'import pty;pty.spawn("/bin/bash")', which uses Python to spawn a better featured bash shell; note that some targets may need the version of Python specified. If this is the case, replace python with python2 or python3 as required. At this point our shell will look a bit prettier, but we still won't be able to use tab autocomplete or the arrow keys, and Ctrl + C will still kill the shell.
    
2. Step two is: export TERM=xterm -- this will give us access to term commands such as clear.
    
3. Finally (and most importantly) we will background the shell using Ctrl + Z. Back in our own terminal we use stty raw -echo; fg. This does two things: first, it turns off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and Ctrl + C to kill processes). It then foregrounds the shell, thus completing the process.
    

The full technique can be seen here:

![](https://lh7-us.googleusercontent.com/dpMmKAQDmG5ytIfXXOvHI_NrucFkKQb0_QAVmP3iJjZAaChlepXlw7Ajb6qyeBYAW3FjiMoRu4qrGBqTih0Ah1PXU3uGmDbUokxQYm5a3LeoZIx95CUTn_aoAVKxRitQl1flsX4T6WX1TFyuWNUY4vY)

Note that if the shell dies, any input in your own terminal will not be visible (as a result of having disabled terminal echo). To fix this, type reset and press enter.

---

Technique 2: rlwrap

rlwrap is a program which, in simple terms, gives us access to history, tab autocompletion and the arrow keys immediately upon receiving a shell; however, some manual stabilisation must still be utilised if you want to be able to use Ctrl + C inside the shell. rlwrap is not installed by default on Kali, so first install it with sudo apt install rlwrap.

To use rlwrap, we invoke a slightly different listener:

rlwrap nc -lvnp <port>

Prepending our netcat listener with "rlwrap" gives us a much more fully featured shell. This technique is particularly useful when dealing with Windows shells, which are otherwise notoriously difficult to stabilise. When dealing with a Linux target, it's possible to completely stabilise, by using the same trick as in step three of the previous technique: background the shell with Ctrl + Z, then use stty raw -echo; fg to stabilise and re-enter the shell.
