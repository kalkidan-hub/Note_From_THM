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

