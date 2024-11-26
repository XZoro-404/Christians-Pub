---
tags: 
created: 2023-10-18
last_modified_at: 2024-02-04
---
#### Description

Our flag printing service has started glitching!`$ nc saturn.picoctf.net 49700`

> [!hint]- Hint
>

---

### Step 1
When you netcat to the server you get the following
```python
g2_pilot_tester-picoctf@webshell:~$ nc saturn.picoctf.net 49700
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
^C 
```
From this we can just use the Python interpreter to give us the correct char values
```python
g2_pilot_tester-picoctf@webshell:~$ python
Python 3.10.6 (main, Aug 10 2022, 11:40:04) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
'picoCTF{gl17ch_m3_n07_********}'
>>>
```




### Flag
> [!question]- Flag
> picoCTF{gl17ch_m3_n07_a4392d2e}







