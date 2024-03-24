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
