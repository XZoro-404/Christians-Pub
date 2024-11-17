---
tags:
  - python
  - decode
  - base64
created: 2023-10-27
last_modified_at: 2024-02-04
---
# repetitions
---
### Description
---
Can you make sense of this file?
Download the file [here](https://artifacts.picoctf.net/c/477/enc_flag).
### Hints
---

> [!hint]- Hint(s)
> 1.  Multiple decoding is always good.
> 2. https://gchq.github.io/CyberChef/

### Step(s)
---
1. When looking at the file you are greeted with an encoded string broken across multiple lines
2. You can use cyberchefs magic operation which will show you it is most likely base64 encoded. With this you can use the operation 'From Base64' as many times as it takes to get the flag
3. I also created a python script that you can run on the command line but you need to make sure that the string is all in one line and on the first line
```python
import base64

def decode_base64_file(file_path, iterations):
    with open(file_path, "r") as file:
        encoded_string = file.readline().strip()

    for _ in range(iterations):
        decoded_bytes = base64.b64decode(encoded_string)
        encoded_string = decoded_bytes.decode('utf-8')

    return encoded_string

def main():
    file_name = input("File to decode: ")
    iterations = int(input("How many times would you like to decode the string: "))

    try:
        decoded_string = decode_base64_file(file_name, iterations)
        print("Decoded string:", decoded_string)
    except FileNotFoundError:
        print("Error: File not found.")
    except Exception as e:
        print("An error occurred:", str(e))

if __name__ == "__main__":
    main()

```

### Flag
---
> [!question]- Flag
> picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_de523f49}







