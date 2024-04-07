### Service Exploitation

>[!Scenario]
>We have a service running as a root and the root user for the service has no password assigned.  The service has a _User Defined function_ feature.  The service is _MySQL_


_approach..._
1. find for available exploit. [here](https://www.exploit-db.com/exploits/1518)
2. follow the procedure described on the exploit 
3. gain the root shell. 

>[! Takeaway]
> `UDFs` --) is essentially a set of instructions you create to perform a specific task within a program. Think of it as a mini-program you can write to avoid repeating the same code over and over.
> If we are allowed to log in as a `root` and create a service, let that service be moving the `/bin/bash` file with `SUID` permission to our accessible environment. Wollaa

_What is it about `/bin/bash` , tho?_

 - it is a symbolic link that points to the actual Bash executable on your system.


### Weak File Permission
#### Readable /etc/shadow

>[! Scenario]
> found a readable /etc/shadow file, where the password of users is stored, including of root. 

_What can we do to exploit this?_

- well, use copy the file to somewhere else and use `john` to crack it.


### Weak File Permissions - Writable /etc/shadow

>[! scenario] 
>The `/etc/shadow` file is not readable, but it's `world-writable` - anybody could write on it.

_Exploitation,..._
- well write on it
- replace the hashed pass of the root user with the new password hashed.  
- or create a new user with root privilege and sing in with it

### Writable /etc/passwd
_Exploitation_
- replace the `X` of password field of root user and save the system from checking from `/etc/shadow` 

### `Sudo` - Shell Escape Sequence 

To list list of programs that the `sudo` allows their user to run with elevated privilege  

```zsh
sudo -l
```

_Why do we care about these programs?_
There's something for us [here]([https://gtfobins.github.io](https://gtfobins.github.io/))

### `sudo` - Environment variables

the output of `sudo -l` also contains inherited environment variables,  

These variables might contain list of directories where shared libraries are searched for first

> while opening the 