### John who?
John the Ripper is a free and open-source password-cracking tool. It can crack passwords stored in various formats, including hashes, passwords, and encrypted private keys. It can be used to test passwords' security and recover lost passwords.

#### where John come in
- on the ground of ==dictionary attack==, an attack that is performed by hashing words from a given, usually long, dictionary and comparing it with the given hash.
### Cracking with John
```zsh
john --format=[format] --wordlist=[path to wordlist] [path to file]
```

To see all the formats out there
```zsh
john --list=formats
```

### Cracking /etc/shadow hashes

```zsh
root:!:19786:0:99999:7:::
```
sample entry of `/etc/shadow`
each section separated by `:` - called ==GECOS== represent this in order
- username
- password hash (! indicates there's no password for that user)
- last password change
- minimum password age
- maximum password age
- password warning period
- account expiration date
- reserved field

```zsh
sshd:x:114:65534::/run/sshd:/usr/sbin/nologin
```
sample entry from `/etc/passwd` file
each section separated by `:` represent this in order
- username
- password placeholder - `x` , `note` that the password is stored in `/etc/shadow` file, which is not accessed unless being `sudoer` therefore protected
- user ID
- group ID
- user information
- home directory
- login shell

#### Unshadow

```zsh
unshadow [path to passwd] [path to shadow]
```


- the `unshadowing` process presents the `/etc/passwd` file with the `x` part restored, obviously from `/etc/shadow`

### Single crack mode
In this mode, John uses only the information provided in the username, to try and work out possible passwords heuristically, by slightly changing the letters and numbers contained within the username -- called ==Word Mangling==

```zsh
john --single --format=[format] [path to file]
```

### Custom Rules
The good thing about `John` is that you can define your own sets of rules, which John will use to dynamically create passwords. This is especially useful when you know more information about the password structure of whatever your target is.

*How?*
- By editing the `/etc/john/john.conf` file, 
- add a `[List.Rules:[name of your rule]]` and state your rules below
*How to write those rules?*
[learn Regex](https://cheatography.com/davechild/cheat-sheets/regular-expressions/)

### Cracking Password Protected Zip File

#### Zip2John 
- first thing first, let `john` understand the thing...

```zsh
zip2john [options] [zip file] > [output file]
```

Then the usual cracking...

### Cracking Password Protected RAR Archives

#### Rar2John

```zsh
rar2john [rar file] > [output file] 
```

### Cracking SSH Keys with John
#### SSH2John
```zsh
ssh2john [id_rsa private key file] > [output file]
```


### [Further](https://www.openwall.com/john/)
