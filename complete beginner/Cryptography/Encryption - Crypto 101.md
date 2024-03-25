### Why Cryptography?
- protect confidentiality
- ensure integrity
- ensure authenticity

#### PCI-DSS (Payment Card Industry - Data Security Standard)
-  is an [information security](https://en.wikipedia.org/wiki/Information_security "Information security") standard used to handle [credit cards](https://en.wikipedia.org/wiki/Credit_card "Credit card") from major [card brands](https://en.wikipedia.org/wiki/Card_scheme "Card scheme"). Its use is mandated by the card brands [Wikipedia](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard)

### RSA
#### p, q, m, n, e, d and c
- p & q large prime numbers 
- n = p * q
- (n,e) - the public key
- (n, d) - the private key
- m - message
- c - cipher text

### Certificates
- a prove of who you are
- have a chain of trust

### SSH Authentication
To generate pairs of keys we use a program `ssh-keygen` 

To log into the system using key authentication, use this format,
```zsh
ssh -i keyNameGoesHere user@host
```

### Diffie Hellman key exchange

[The always best explanation](https://youtu.be/NmM9HA2MQGI?si=oAN5qWXX8dxWhuWs)
1. ![[Pasted image 20240325115753.png | 500]] Alice and Bob producing their private key
2. ![[Pasted image 20240325115943.png | 500]] Alice and Bob producing Public Key of their own
3. ![[Pasted image 20240325120137.png | 500]] Alice and Bob exchanging the produced public key of theirs
4. ![[Pasted image 20240325120219.png | 600]] Alice and Bob discovering the shared secret without any other party discovering it...

### PGP, GPG and AES

#### PGP(Pretty Good Privacy) 
-  It’s a software that implements encryption for encrypting files, performing digital signing and more.
#### GPG (GnuPG) 
- Open source implementation of PGP from the GNU project.

#### AES - Rijndael (Advanced Encryption Standard) 
- A block cipher symmetric data encrypting algorithm
- [Wanna know how it works](https://www.youtube.com/watch?v=O4xNJsjtN6E)
