---
layout: page
title: Stable Shell
author:
  name: Aissa Ben yahya
  time: 2022-02-10 16:28 +0100
categories: [Hacking, Tools]
---
We all likes to play CTFs, I do too. But sometimes we do a reverse shell using `netcat`. The shell we get back most of time is not stable. Thus, we need to make it stable. Down below you will find the instructions to make a stable shell.

### Spawning a TTY shell
---
```python
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
After spawning a tty shell, click `Ctrl+z` and execute the command below:

```bash
stty raw -echo
```
Now bring back the session by executing 
```bash
fg
```
and then
```bash
export TERM=xterm
```

