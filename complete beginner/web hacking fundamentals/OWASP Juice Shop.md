Zooming in to ...
1. Injection
2. Broken Authentication
3. Sensitive Data Exposure
4. Broken Access Control
5. Cross-Site Scripting XSS

Injection
=
|                   |                                                                                                                                                                                                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SQL Injection     | SQL Injection is when an attacker enters a malicious or malformed query to either retrieve or tamper data from a database. And in some cases, log into accounts.                                                                                                   |
| Command Injection | Command Injection is when web applications take input or user-controlled data and run them as system commands. An attacker may tamper with this data to execute their own system commands. This can be seen in applications that perform misconfigured ping tests. |
| Email Injection   | Email injection is a security vulnerability that allows malicious users to send email messages without prior authorization by the email server. These occur when the attacker adds extra data to fields, which are not interpreted by the server correctly.        |
#### SQL Injection
*How sql query works to validate users?*
```sql
SELECT * 
FROM users 
WHERE username = 'provided_username' AND password = 'provided_password';
```
*what can we inject to put this in our advantage?*
> What if we make our username ` ' OR true`

```sql
SELECT * 
FROM users 
WHERE username = '' OR True' 
AND password = 'provided_password';
```
 it becomes
 
 > See the username part assumes it got nothing since the `'` is closed and the rest part got executed, but might cause syntax error, since sql doesn't have a keyword `True` 

*so what can we do about it?*
> other way of representing `True` would work
> ` 1 = 1` or  ` 10 > 0`   ,is good.

*but still the `AND` part become our impedance, since whatever it says has priority, therefore the password still gonna be considered, .. emmm *

> can we just not care about what comes next? yeah, let's comment all the rest out.
> `--` the commenting means in sql.

```sql
SELECT * 
FROM users 
WHERE username = '' OR 1=1 --' 
AND password = 'provided_password';
```
Therefore our final potion would be `' OR 1=1 --`

Broken Authentication
=
#### Weak Password in high privileged accounts.
- Burp Suite's intruder feature can be used here to launch `brute force` attack
#### Forgotten password pages
- clues about the person or his/her behavior can be used to bypass the security related question.

Sensitive Data Exposure 
=
- link on the page might reveal some sensitive directory. 
- revealing what's wrong in the system might open-up an attack door. 
#### Poison Null Byte

> Consider this scenario, the web system grants you to download files only with certain extensions(say only .pdf). And now you wanted to download a (.jpg) file.  What can we do about it?


> If only there's a way that the system doesn't know the file is actually a `.jpg` type. 

*Any idea to do that?*

> How about just adding a `.jpg` extension to the file of interest

*Ah, yeah but we don't actually change the behavior of the file, *

> In that case we shall let the system's knowledge of a file stay the original one.. 
> How about we do some `null` poison, like ...

```perl
http://example.com/ftp/package.pdf%2500.jpg
```

>[!Note] 
> - by .`.jpg` we bypass the extension restriction 
> - by %2500 we inserting `null byte` so the inner system thinks that this is EOF, nothing is beyond therefore it ignores the .jpg extension.


Broken Access Control 
=
It comes of two types...

| **Horizontal** Privilege Escalation | Occurs when a user can perform an action or access data of another user with the **same** level of permissions. |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Vertical** Privilege Escalation   | Occurs when a user can perform an action or access data of another user with a higher level of permissions.     |

Cross Site Scripting 
=

- Is a vulnerability that allows attackers to run javascript in web applications
- There are three major types...
	- DOM(special) - uses the HTML environment to execute malicious javascript, and it commonly uses `<script></script>` HTML tag
	- Persistent(server-side) - that is run when the server loads the page containing the malicious script. These usually occurs when the server does't properly sanitize the user data when it's uploaded to the page.
	- Reflected (client-side) - this mal-script is run on the client-side end of the web application

