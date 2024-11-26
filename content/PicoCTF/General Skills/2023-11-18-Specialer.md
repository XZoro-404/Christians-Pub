---
tags:
  - Linux-Commands
created: 2023-11-18
last_modified_at: 2024-02-04
---
# Specialer
---
### Description
---
Reception of [[Special]] has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.

Additional details will be available after launching your challenge instance.
### Hints
---

> [!hint]- Hint(s)
> 1. 

### Step(s)
---
1. Instantly it is apparent that some of my most used commands I will not be able to use like nano, cat, ls
2. I originally was using `help` to get my brain going on what kind of commands I could try to use. this lead me to thinking of the echo command
3. To list out all of the non hidden files and directories in your current directory you use the command`echo *`  or you can use `printf "%s\n" *` this gives you the directories `abra ala sim`
```bash
Specialer$ printf "%s\n" *
abra
ala
sim
Specialer$ printf "%s\n" abra/*
abra/cadabra.txt
abra/cadaniel.txt
Specialer$ printf "%s\n" ala/*
ala/kazam.txt
ala/mode.txt
Specialer$ printf "%s\n" sim/*
sim/city.txt
sim/salabim.txt
```
4. We now can try to find out a way to view these .txt files without the use of cat. One way is to use a  echo `echo $(<FILENAME)`
```shell
Specialer$ echo $(<abra/cadabra.txt)
Nothing up my sleeve!
Specialer$ echo $(<abra/cadaniel.txt)
Yes, I did it! I really did it! I'm a true wizard!
Specialer$ echo $(<ala/kazam.txt)
return 0 picoCTF{xxxxxxxxxxxxxxxxxxx}
```

### Flag
---
> [!question]- Flag
> picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_d5ef8b71}







