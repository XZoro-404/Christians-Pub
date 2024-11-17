---
created: 2024-02-02
last_modified_at: 2024-02-04
---
[https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh](https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh) 

LinEnum is a simple bash script that performs common commands related to privilege escalation

## How do I get LinEnum (any file) on the target machine?

There are two ways to get LinEnum on the target machine. The first way, is to go to the directory that you have your local copy of LinEnum stored in, and start a Python web server using **"python3 -m http.server 8000"** [1]. Then using **"wget"** on the target machine, and your local IP, you can grab the file from your local machine [2]. Then make the file executable using the command **"chmod +x FILENAME.sh"**.

![](https://github.com/TheRealPoloMints/Blog/blob/master/Security%20Challenge%20Walkthroughs/Common%20Linux%20Privesc/Resources/1.png?raw=true) [1]

![](https://github.com/TheRealPoloMints/Blog/blob/master/Security%20Challenge%20Walkthroughs/Common%20Linux%20Privesc/Resources/2.png?raw=true) [2]

### Other Methods

In case you're unable to transport the file, you can also, if you have sufficient permissions, copy the raw LinEnum code from your local machine [1] and paste it into a new file on the target, using Vi or Nano [2]. Once you've done this, you can save the file with the **".sh"** extension. Then make the file executable using the command **"chmod +x FILENAME.sh"**. You now have now made your own executable copy of the LinEnum script on the target machine!

![](https://github.com/TheRealPoloMints/Blog/blob/master/Security%20Challenge%20Walkthroughs/Common%20Linux%20Privesc/Resources/3.png?raw=true) [1]

![](https://github.com/TheRealPoloMints/Blog/blob/master/Security%20Challenge%20Walkthroughs/Common%20Linux%20Privesc/Resources/4.png?raw=true) [2]

