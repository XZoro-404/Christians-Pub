---
tags:
  - SSH
  - Linux-Commands
  - Cat
created: 2023-10-18
last_modified_at: 2024-02-04
---
The objective in this CTF is to [[ssh]] into the user 'ctf-player' with the password '6d448c9c' and find 3 files containing parts of the flag. 

Upon SSH'ing into the user you can ls to view all of the files in the current directory this is where you find the first part of the flag
```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
```
We then can cat the instructions file to get a hint on where the next part of the flag is which we find to be in the root directory '/' and in here we have a similar result from the first directory
```
ctf-player@pico-chall$ ls /
2of3.flag.txt  dev   instructions-to-3of3.txt  media  proc  sbin  tmp
bin            etc   lib                       mnt    root  srv   usr
boot           home  lib64                     opt    run   sys   var
ctf-player@pico-chall$ cat /2of3.flag.txt 
0ut_0f_\/\/4t3r_
```
then from here we get the hint that the last part of the flag is in the users home directory which can be found using '~/' 
```
ctf-player@pico-chall$ ls ~
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat ~/3of3.flag.txt 
5190b070}
```
Now from here you can just copy all parts of the flag and paste them in as the solution but I prefer to combine them on the machine so I just have to copy once. You can first cat all of the files then redirect the output of them to a new file using '>' But this will result in all of the outputs being on a different line in the new file. This is where the tr command comes into play. The [[tr]] command is the 'translate' command and can replace, delete, or squeeze characters. In our case we want to delete all of the `\n` characters using the '-d' switch so our final command will look like this
```
ctf-player@pico-chall$ cat 1of3.flag.txt /2of3.flag.txt 3of3.flag.txt | tr -d '\n' > flag.txt
ctf-player@pico-chall$ cat flag.txt 
picoCTF{xxsh_0ut_0f_\/\/4t3r_5190b070}
```

> [!question]- Flag
> `picoCTF{xxsh_0ut_0f_\/\/4t3r_5190b070}`

