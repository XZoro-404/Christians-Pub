---
tags:
  - python
created: 2023-10-18
last_modified_at: 2024-02-04
---
# Serpentine
---
### Description
---
Find the flag in the Python script!
[Download Python script](https://artifacts.picoctf.net/c/36/serpentine.py)
### Hints
---

> [!hint]- Hint(s)
> 1. Try running the script and see what happens
> 2. In the webshell, try examining the script with a text editor like `nano`
> 3. To exit `nano`, press Ctrl and x and follow the on-screen prompts.
> 4. The `str_xor` function does not need to be reverse engineered for this challenge.

### Step(s)
---
By utilizing the nano text editor, you can examine the file and observe that selecting the 'Print flag' option on line 69 will only display a string instead of the actual flag. Upon closer inspection at line 20, a function named `print_flag` is identified, responsible for printing the flag. To achieve the desired outcome, modify the file to invoke the `print_flag()` function on line 69. After making this change, running the file again and selecting option 'b' will now correctly output the flag.
### Flag
---
> [!question]- Flag
> picoCTF{7h3_r04d_l355_7r4v3l3d_aa2340b2}







