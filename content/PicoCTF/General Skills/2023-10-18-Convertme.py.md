---
tags:
  - python
  - decimal
  - base10
  - conversion
created: 2023-10-18
last_modified_at: 2024-02-04
---
#### Description
Run the Python script and convert the given number from decimal to binary to get the flag. [Download Python script](https://artifacts.picoctf.net/c/23/convertme.py)


> [!hint]- Hint 1
> Look up a decimal to binary number conversion app on the web or use your computer's calculator!

> [!hint]- Hint 2
> The `str_xor` function does not need to be reverse engineered for this challenge.

> [!hint]- Hint 3
> If you have Python on your computer, you can download the script normally and run it. Otherwise, use the `wget` command in the webshell.

> [!hint]- Hint 4
> To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'

> [!hint]- Hint 5
> Type everything after the dollar sign in the webshell: `$ wget` , then paste the link after the space after `wget` and press enter. This will download the script for you in the webshell so you can run it!

> [!hint]- Hint 6
> Finally, to run the script, type everything after the dollar sign and then press enter: `$ python3 convertme.py`


---

### Step 1
Download and run the python file. where you will get this in the terminal
```c
┌─[user@parrot]─[~/Downloads/PicoCTF]
└──╼ $python3 convertme.py 
If 18 is in decimal base, what is it in binary base?
Answer:
```

### Step 2
![[Pasted image 20231016040246.png]]

### Step 3
The answer is `10010` 
```plaintext
That is correct! Here's your flag: picoCTF{*****************}
```

### Flag
> [!question]- Flag
> That is correct! Here's your flag: picoCTF{*****************}







