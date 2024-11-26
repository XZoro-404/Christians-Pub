---
tags:
  - grep
  - Linux-Commands
created: 2023-10-18
last_modified_at: 2024-02-04
---
#### Description

Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/495d43ee4a2b9f345a4307d053b4d88d/file)? This would be really tedious to look through manually, something tells me there is a better way.

> [!hint]- Hint
> grep [tutorial](https://ryanstutorials.net/linuxtutorial/grep.php)


---

### Step 1
1. Using egrep (grep with regular expression 'grep -E') we can look for the string 'pico' using the following command `egrep 'pico.* file'`


### Flag
> [!question]- Flag
> picoCTF{grep_is_good_to_find_things_dba08a45}







