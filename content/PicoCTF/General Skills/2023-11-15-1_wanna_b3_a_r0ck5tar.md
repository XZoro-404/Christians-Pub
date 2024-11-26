---
header_type: 
header_img: 
title: 
tags:
  - python
  - rockstar
categories: 
created: 2023-11-15
last_modified_at: 2024-02-04
---
# 1_wanna_b3_a_r0ck5tar
---
### Description
---
I wrote you another [song](https://jupiter.challenges.picoctf.org/static/b99c57e4274172bf3c93534b6d59632d/lyrics.txt). Put the flag in the picoCTF{} flag format
### Hints
---

> [!hint]- Hint(s)
> 1.  The Rockstar language has changed since this problem was released! Use this Wayback Machine URL to use an older version of Rockstar, [here](https://web.archive.org/web/20190522020843/https://codewithrockstar.com/online).

### Step(s)
---
1. First using the Webshell we should download the file using wget 
```bash
wget https://jupiter.challenges.picoctf.org/static/b99c57e4274172bf3c93534b6d59632d/lyrics.txt
```

2. Next install rockstar-py which is a python package that can convert rockstar code to python code. `pip install rockstar-py`
3. Using the following command will convert the rockstar script`rockstar-py -i lyrics.txt -o output.py`
4. Output:
```python
Rocknroll = True
Silence = False
a_guitar = 10
Tommy = 44
Music = 170
the_music = input()
if the_music == a_guitar:
    print("Keep on rocking!")
    the_rhythm = input()
    if the_rhythm - Music == False:
        Tommy = 66
        print(Tommy!)
        Music = 79
        Jamming = 78
        print(Music!)
        print(Jamming!)
        Tommy = 74
        print(Tommy!)
        They are dazzled audiences
        print(it!)
        Rock = 86
        print(it!)
        Tommy = 73
        print(it!)
        break
        print("Bring on the rock!")
        Else print("That ain't it, Chief")
        break
```
5. This will not run correctly without some fixes to the code. Mostly the '!' in the print statements and line 19 needs to be commented out.
```ruby
g2_pilot_tester-picoctf@webshell:~/rooms/1_wanna_b3_a_r0ck5tar$ python output.py 
  File "/home/g2_pilot_tester-picoctf/rooms/1_wanna_b3_a_r0ck5tar/output.py", line 12
    print(Tommy!)
               ^
SyntaxError: invalid syntax
```

6. The integers are also wrong so in order to fix them you must know how they are declared
```none
A poetic number literal begins with a variable name, followed by the keyword is, or the aliases was or were. As long as the next symbol is not a Literal Word, the rest of the line is treated as a decimal number in which the values of consecutive digits are given by the lengths of the subsequent barewords, up until the end of the line. To allow the digit zero, and to compensate for a lack of suitably rock’n’roll 1- and 2-letter words, word lengths are parsed modulo 10. A period (.) character denotes a decimal place. Other than the first period, any non-alphabetical characters are ignored.

Tommy was a lovestruck ladykiller initialises Tommy with the value 100
Sweet Lucy was a dancer - initialises Sweet Lucy with the value 16
A killer is on the loose - initialises a killer with the value 235.
My dreams were ice. A life unfulfilled; wakin' everybody up, taking booze and pills - initialises my dreams with the value 3.1415926535
Tommy was without initialises Tommy with the value 7 because without is a Reserved Keyword, but not a Literal Word.
Note that poetic literals can include Reserved Keywords, as with taking in this example.
The semi-colon, comma, apostrophe and any other non-alphabetical characters are ignored.
```

7. New Code
```python
Rocknroll = True
Silence = False
a_guitar = 136
Tommy = 44
Music = 1970
the_music = input()
if the_music == a_guitar:
    print("Keep on rocking!")
    the_rhythm = input()
    if the_rhythm - Music == False:
        Tommy = 66
        print(Tommy)
        Music = 79
        Jamming = 78
        print(Music)
        print(Jamming)
        Tommy = 74
        print(Tommy)
        #They are dazzled audiences
        print(it)
        Rock = 86
        print(it)
        Tommy = 73
        print(it)
        #break
        print("Bring on the rock!")
    Else: print("That ain't it, Chief")
        #break
```

8. From this we can now run our code with the first input being 136 and the second input being 1970. With these inputs we get the output of: 
	Keep on rocking!
	66
	79
	78
	74
	79
	86
	73

9. We can now translate this into ascii which will give us: xxxxxxx <- {Obscured because it is the key}

### Flag
---
> [!question]- Flag
> picoCTF{BONJOVI}
