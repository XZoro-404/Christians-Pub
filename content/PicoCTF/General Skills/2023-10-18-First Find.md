---
tags:
  - find
  - Linux-Commands
created: 2023-10-18
last_modified_at: 2024-02-04
---
# First Find
---
### Description
---
Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/501/files.zip)
### Hints
---

> [!hint]- Hint(s)
> 1.  NONE

### Step(s)
---
1. **Download the zip file and unzip it** using the unzip command. Navigate to the directory where the folder was extracted.

2. **Run the find command** from the same location where the folder is extracted. Use the command `find . -name uber-secret.txt` to locate the path of the file named 'uber-secret.txt' within your current directory.

3. **Utilize the cat command** to view the contents of the file. The flag can be found inside 'uber-secret.txt'.
### Flag
---
> [!question]- Flag
> picoCTF{f1nd_15_f457_ab443fd1}







