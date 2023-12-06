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
