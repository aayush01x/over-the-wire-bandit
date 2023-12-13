# over-the-wire-bandit
Documentaion for the Bandit OverTheWire Levels

## Level 0

Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```
## Level 0 → Level 1

Using cat command to read file 'readme' in the home directory.
```bash
$ cat readme
```
**Password** : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
## Level 1 → Level 2

Connecting to the host:
```bash
$ ssh bandit1@bandit.labs.overthewire.org -p 2220
```
Reading file '-' located in the home directory using two methods : 
```bash
$ cat < -
```
```bash
$ cat ./-
```
**Password** : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
## Level 2 → Level 3

Connecting to the host:
```bash
$ ssh bandit2@bandit.labs.overthewire.org -p 2220
```
Reading file 'spaces in this filename' located in the home directory by enclosing file name in `''`: 
```bash
$ cat 'spaces in this filename'
```
**Password** : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
## Level 3 → Level 4

Connecting to the host:
```bash
$ ssh bandit3@bandit.labs.overthewire.org -p 2220
```
Changing directory to 'inhere':
```bash
$ cd inhere
```
Viewing hidden files using `ls -a` and reading hidden file with `cat` :
```bash
$ ls -a
$ cat '.hidden'
```
**Password** : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
## Level 4 → Level 5
```bash
$ ssh bandit4@bandit.labs.overthewire.org -p 2220
```
One way is to check through each file `-filexx` (where `xx` is index) till we get a human-readable file.
```bash
$ cd inhere
$ cat < -filexx
```
Better, faster way is to check each file type using `file` command
```bash
$ file ./inhere/*
```
This gives following output which indicates -file07 is human-readable file.
```
./inhere/-file00: data
./inhere/-file01: data
./inhere/-file02: data
./inhere/-file03: data
./inhere/-file04: data
./inhere/-file05: data
./inhere/-file06: data
./inhere/-file07: ASCII text
./inhere/-file08: data
./inhere/-file09: data
```
It can be now read using `cat`:
```bash
$ cat ./inhere/-file07
```
**Password** : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
## Level 5 → Level 6
```bash
$ ssh bandit5@bandit.labs.overthewire.org -p 2220
```
```bash
$ cd inhere
$ find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII
```
`-type f` is used to look at only files

`-!-executable` is used to find non-executable files

`-size 1033c` adds filter for files with size 1033bytes

`-exec file '{}' \; | grep ASCII` is to execute the find command and then apply grep ASCII on it to search for Human Readable files.

This gives the path of the file which follows the gien conditions. It shows that type of file is ASCII text, with very long lines. 

```./maybehere07/.file2: ASCII text, with very long lines (1000)```

```bash
$ cat ./maybehere07/.file2
```
**Password** : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Level 6 → Level 7
```bash
$ ssh bandit6@bandit.labs.overthewire.org -p 2220
```

```bash
$ find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
`-find /` searches for files over the whole system.

`2>/dev/null` is used to clear the output for folders on which access is denied

Output: 
`
/var/lib/dpkg/info/bandit7.password
`
```bash
$ cat /var/lib/dpkg/info/bandit7.password
```
**Password**: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

## Level 7 → Level 8
```bash
$ ssh bandit7@bandit.labs.overthewire.org -p 2220
```
```bash
$ cat data.txt | grep millionth
```
`cat` reads the file `data.txt` and using `grep millionth`, it outputs the line which has millionth keyword in it. 

Output: `millionth	TESKZC0XvTetK0S9xNwm25STk5iWrBvP`

**Password**: TESKZC0XvTetK0S9xNwm25STk5iWrBvP

## Level 8 → Level 9
```bash
$ ssh bandit8@bandit.labs.overthewire.org -p 2220
```
```bash
$ sort data.txt | uniq -u
```
Because `uniq -u` checks only for consecutive lines. So, data.txt is sorted first and then `uniq -u` is applied to find the unique line.

**Password**: EN632PlfYiZbn3PhVK3XOGSlNInNE00t
## Level 9 → Level 10
```bash
$ ssh bandit9@bandit.labs.overthewire.org -p 2220
```
```bash
$ strings data.txt | grep ==
```
`strings` searches for human readable strings in the file `data.txt` and using `grep`, output shows the lines with `==` as a substring . We can look through the output to get required answer.

Output: 
```
x]T========== theG)"
========== passwordk^
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
**Password**: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

## bandit10 → bandit11


```bash
$ cat data.txt
```

```bash
$ cat data.txt | base64 -d
```

## Level11 → Level12

Using `cat` to read the file

```bash
$ cat data.txt
```

```bash
$ cat data.txt | tr "A-Za-z" "N-ZA-Mn-za-m"
```

## Level12 →  Level13

Using `xxd` with option -r to convert hexdump to data file

```bash
$ xxd -r data.txt > file
```
Using file option to find the archive type , renaming the original file with the respective archive extension and respectively used tar,gzip,bzip2 to decompress the file.

```bash
$ file [filename]

$ mv [filename1] [filename2].[archiveType]

$ tar -xf [filename].tar

$ gzip -d [filename].gz 

$ bzip2 -d [filename].bz
```


## Level13 →  Level14

Retrieved ssh private keys and saved it under .ssh/id_rsa and Changed the file permission to 600

```bash
$ chmod 600 id_rsa
```


```bash
$ ssh -i id_rsa Level14@Level.labs.overthewire.org -p 2220
```


## Level14 → Level15

Using `nc` to connect to port 30000 using host as "localhost"

```bash
$ nc localhost 30000
```

## Level15 → Level16

Using `openssl` connect to "localhost" at port 30001

```bash
$ openssl s_client -connect localhost:30001
```
