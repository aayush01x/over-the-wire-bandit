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
