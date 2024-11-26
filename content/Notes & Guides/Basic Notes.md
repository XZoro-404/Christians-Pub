---
created: 2024-02-02
last_modified_at: 2024-02-04
---
[Fixing Display Settings to 4K for ParrotOS](https://sysadmin102.com/2023/06/parrot-os-scaling-the-desktop-with-xorg-x11-without-changing-the-resolution/)

alt+c in nano will show the line numbers

https://gtfobins.github.io/#vi

### Bashrc
---
To refresh .bashrc to enable any new changes use the following
```bash
. ~/.bashrc

```
or 
```bash
source ~/.bashrc

```

to add a command that will mkdir and cd into add the following into .bashrc
```bash
# ~/.bashrc
function mkcd {
  if [ ! -n "$1" ]; then
    echo "Enter a directory name"
  elif [ -d $1 ]; then
    echo "\`$1' already exists"
  else
    mkdir $1 && cd $1
  fi
}
```

`cat -n` will add line numbers to cat