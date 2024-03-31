###  understanding 
- usually involves going from a lower permission to a higher permission. It's the exploitation of a vulnerability, design flaw or configuration oversight in an operating system or application to gain unauthorized access to resources that are usually restricted from the users.
#### why it's important
-  Reset passwords  
-  Bypass access controls to compromise protected data
-  Edit software configurations
-  Enable persistence, so you can access the machine again later.
-  Change privilege of users
-  Get that cheeky root flag ;)

### Direction of privilege flow
#### Horizontal
- taking over a different user who is on the same privilege level as you. 
- the travel is `sideways`

#### Vertical
- an attempt to gain higher privileges or access
- travel `up` on the tree

### How to detect/enumerate privesc vulnerabilities
[LinEnum](https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh)

> LinEnum is a simple bash script that performs common commands related to privilege escalation, saving time and allowing more effort to be put toward getting root.

#### the output

_Kernel_ Kernel information is shown here. There is most likely a kernel exploit available for this machine.

_Can we read/write sensitive files:_ The world-writable files are shown below. These are the files that any authenticated user can read and write to. By looking at the permissions of these sensitive files, we can see where there is misconfiguration that allows users who shouldn't usually be able to, to be able to write to sensitive files.

_SUID Files:_ The output for SUID files is shown here. There are a few interesting items that we will definitely look into as a way to escalate privileges. SUID (Set owner User ID up on execution) is a special type of file permissions given to a file. It allows the file to run with permissions of whoever the owner is. If this is root, it runs with root permissions. It can allow us to escalate privileges. 

_Crontab_ _Contents**:**_ The scheduled cron jobs are shown below. Cron is used to schedule commands at a specific time. These scheduled commands or tasks are known as “cron jobs”. Related to this is the crontab command which creates a crontab file containing commands and instructions for the cron daemon to execute. There is certainly enough information to warrant attempting to exploit Cronjobs here.
### Abusing SUID/GUID

#### SUID (Set owner User ID) 
- a special type of file permission given to a file, ==It allows the file to run with permission of whoever the owner is==
#### GUID (Group User ID)
- a permission to a file that help it to run with the permission of it's owner group
### Exploiting writeable etc/passwd 
- It's simple really, if we have a writable `/etc/passwd` file, we can write a new line entry according to the above formula and create a new user! We add the password hash of our choice, and set the UID, GID and shell to root. Allowing us to log in as our own root user!
