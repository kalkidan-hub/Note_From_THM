### Jargon
>[!Note]
>*plaintext* - plain(unencrypted) data
*encoding* - form of data representation, it's like translation of a data, no key is needed to do so
*hash* - output of a hash function
*brute force* - attacking cryptography by trying all different possible values
*cryptoanalysis* - attacking cryptography by finding weakness in the underlying math.

### hash function

- no key is involved
- irreversible 
- fixed size
- small change in original data causes large change
#### Hash collision 
when two different inputs give the same output.
> *why this occurs?* 
> It's due to ==Pigeonhole effect== , remember the hash output has the same size, while we could have more than 2^(hash_length) inputs, which implies at least two of them must have the same hash.


### What can we do with Hashing?
Two main purposes they serve...
- verifying integrity 
- verifying password

#### Story of rockyou.txt

**RockYou** was a company that developed widgets for [MySpace](https://en.wikipedia.org/wiki/MySpace "MySpace") and implemented applications for various social networks and Facebook.
In December 2009, the company experienced a data breach resulting in the exposure of over 32 million user accounts. The company used an unencrypted database to store user account data, including [plaintext](https://en.wikipedia.org/wiki/Plaintext "Plaintext") passwords (as opposed to [password hashes](https://en.wikipedia.org/wiki/Cryptographic_hash_function#Password_verification "Cryptographic hash function")) for its service, as well as passwords to connected accounts at partner sites (including Facebook, Myspace, and webmail services).
[Further](https://en.wikipedia.org/wiki/RockYou)

Storing the hash of the password, is like not storing the password, and if your data leaked then an attacker would have to crack each password to find out what the password was.

#### Rainbow table
- is a lookup table of hashes to plaintext, for quick find out of the password from hash.
- ==salt== is used to protect hashed passwords from rainbow search
- Salt is unique for each user and added to start or end of the password before it's hashed, making the hash superly different for each user.

### Password hashes format
Unix style
```format
$format$rounds$salt$hash
```
Windows password are hashed using `NTLM (New Technology LAN Management)`  variant of md4.
On Linux, password hashes are stored in `/etc/shadow`. This file is normally only readable by root. They used to be stored in `/etc/passwd,` and were readable by everyone.
On Windows, password hashes are  stored in the `SAM(Security Account Manager)`

[here](https://hashcat.net/wiki/doku.php?id=example_hashes) is the link to see various hash formats and password prefixes.

### Password Cracking

#### Identification
```zsh
hash-identifier
```
[online tool](https://www.tunnelsup.com/hash-analyzer/)

#### Cracker
```zsh
hashcat [option] hash_file
```

```zsh
john hash_file -format=[hash_format] -wordlist=[wordlist_to_perform_cracking_to]
```

[For rainbow attack](https://crackstation.net/)
[another one](https://dehash.sh/)

### Hashing for integrity checking
- `HMAC` is a method of using a cryptographic hashing function to verify the authenticity and integrity of data
- They use a secret key, and a hashing algorithm in order to produce a hash.