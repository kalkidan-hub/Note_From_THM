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


### 




