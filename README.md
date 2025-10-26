                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       


## 🎯 About
This document contains my complete walkthrough of the [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) wargame. Bandit is designed for beginners to learn Linux commands and basic security concepts through practical challenges.

**My Goal:** Master Linux command-line fundamentals and develop problem-solving skills for cybersecurity challenges.


## 🚀 My Learning Journey
- **Started:** Learning basic Linux commands 
- **Progress:** Levels 0-12 completed
- **resources:** Linux basics for hackers(book), HTB Linux Fundamentals, linuxjourney.
- **useful links:** [hackthebox Linux Fundamentals](https://academy.hackthebox.com/module/details/18)
                    [linuxjourney](https://labex.io/linuxjourney)
                    [Bash cheatsheet](https://quickref.me/bash)


# Levels 0-5: File System Fundamentals

## level 0

**Goal:** Basic SSH connection 

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

## level 0 -> 1

**Concept:** Basic file reading

```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
...
The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
**password:** ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## level 1 -> 2

**Concept:** Special filename handling

```bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
**password:** 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## level 2 -> 3

**Concept:** Filenames with spaces

```bash
bandit2@bandit:~$ ls
--spaces in this filename--
bandit2@bandit:~$ cat ./'--spaces in this filename--'
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
**password:** MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## level 3 -> 4

**Concept:** Hidden files
```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ./...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

**password:** 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## level 4 -> 5

**Concept:** File type identification

```bash
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls -a
.  ..  -file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ file ./-file**
./-file00: Non-ISO extended-ASCII text, with no line terminators, with overstriking
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
**password:** 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## level 5 -> 6

**Concept:** Advanced file searching

```bash
bandit5@bandit:~$ ls 
inhere
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ find -type f -size 1033c ! -executable
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
**password:** HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

# Levels 6-9: System Exploration & Text Processing

## level 6 -> 7

**Concept:** System-wide file search

```bash
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
**password:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## level 7 -> 8

**Concept:** Pattern matching with grep

```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ cat data.txt | grep "millionth"
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
**password:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## level 8 -> 9

**Concept:** Finding unique lines

```bash
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ wc -l data.txt
1001 data.txt
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
**password:** 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## level 9 -> 10

**Concept:** Binary file analysis

```bash
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ strings data.txt | grep "=="
========== theg
========== password
========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
**password:** FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

# Levels 10-12: Encoding & Basic Cryptography

## level 10 -> 11

**Concept:** Base64 decoding

```bash
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
**password:** dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## level 11 -> 12

**Concept:** ROT13 character rotation

```bash
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
**password:** 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## level 12 -> 13

**Concept:** Multiple compression layers & hexdump reversal

```bash
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ cd /tmp
bandit12@bandit:/tmp$ mkdir hxd
bandit12@bandit:/tmp$ cp ~/data.txt hxd
bandit12@bandit:/tmp$ cd hxd
bandit12@bandit:/tmp/hxd$ ls
data.txt
bandit12@bandit:/tmp/hxd$ file data.txt
data.txt: ASCII text
bandit12@bandit:/tmp/hxd$ xxd -r data.txt > hexdump
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump
bandit12@bandit:/tmp/hxd$ file hexdump 
hexdump: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 564
bandit12@bandit:/tmp/hxd$ mv hexdump hexdump.gz
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump.gz
bandit12@bandit:/tmp/hxd$ gzip -d hexdump.gz 
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump
bandit12@bandit:/tmp/hxd$ file hexdump 
hexdump: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/hxd$ mv hexdump hexdump.bz2
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump.bz2
bandit12@bandit:/tmp/hxd$ bzip2 -d hexdump.bz2 
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump
bandit12@bandit:/tmp/hxd$ file hexdump 
hexdump: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/hxd$ mv hexdump hexdump.gz
bandit12@bandit:/tmp/hxd$ gzip -d hexdump.gz 
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump
bandit12@bandit:/tmp/hxd$ file hexdump 
hexdump: POSIX tar archive (GNU)
bandit12@bandit:/tmp/hxd$ mv hexdump hexdump.tar
bandit12@bandit:/tmp/hxd$ ls
data.txt  hexdump.tar
bandit12@bandit:/tmp/hxd$ tar -xvf hexdump.tar 
data5.bin
bandit12@bandit:/tmp/hxd$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/hxd$ tar -xvf data5.bin 
data6.bin
bandit12@bandit:/tmp/hxd$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/hxd$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/hxd$ bzip2 -d data6.bz2 
bandit12@bandit:/tmp/hxd$ ls
data5.bin  data6  data.txt  hexdump.tar
bandit12@bandit:/tmp/hxd$ file data6
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/hxd$ tar -xvf data6
data8.bin
bandit12@bandit:/tmp/hxd$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/hxd$ mv data8.bin data8.gz
bandit12@bandit:/tmp/hxd$ gzip -d data8.gz
bandit12@bandit:/tmp/hxd$ ls
data5.bin  data6  data8  data.txt  hexdump.tar
bandit12@bandit:/tmp/hxd$ file data8
data8: ASCII text
bandit12@bandit:/tmp/hxd$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```
**password:** FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

# Levels 13-16: Networking & Remote Connections

## level 13 -> 14

**Concept:** SSH key authentication

```bash
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ cat sshkey.private
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```
copied the sshkey.private in my local machin to change it's privileg to **-rw-------** 

```bash 
$ chmod 600 sshkey.private
$ ll
-rw------- 1 fennec fennec 1679 Oct 21 18:54 sshkey.private
$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
**password:** MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## level 14 -> 15

**Concept:** Network communication with nc (netcat)

```bash
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
**password:** 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
