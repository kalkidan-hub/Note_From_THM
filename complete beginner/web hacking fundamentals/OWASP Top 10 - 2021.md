
1. [[OWASP Top 10 - 2021#1. Broken Access Control (IDOR - Insecure Direct Object Reference) | Broken Access Control]]
2. [[OWASP Top 10 - 2021#Cryptographic Failures | Cryptographic Failures]]
3. [[OWASP Top 10 - 2021#Injection | Injection]]
4. [[OWASP Top 10 - 2021#Insecure Design | Insecure Design]]
5. [[OWASP Top 10 - 2021#Security Misconfiguration | Security Misconfiguration]]
6. [[OWASP Top 10 - 2021#Vulnerable and Outdated Components | Vulnerable and Outdated Components]]
7. [[OWASP Top 10 - 2021#Identification and Authentication Failures | Identification and Authentication Failures]]
8. [[OWASP Top 10 - 2021#Software and Data Integrity Failure | Software and Data Integrity Failures]]
9. [[OWASP Top 10 - 2021#Security Logging and Monitoring Failures | Security Logging & Monitoring Failures]]
10. [[OWASP Top 10 - 2021#Server-Side Request Forgery | Server-Side Request Forgery (SSRF)]]

### 1. Broken Access Control (IDOR - Insecure Direct Object Reference)
- When a website visitors have access to the protected pages they are not meant to see.
- *why do we care?*
- Because, this might lead to the following ...
	- Being able to view sensitive information of other users  - compromising `confidentiality` 
	- Accessing and performing unauthorized activities

##### IDOR 
- occur when the programmer exposes a `Direct Object Reference`, which is an identifier that refers to specific objects within the server

### Cryptographic Failures

- A vulnerability that arises from the misuse of cryptographic algorithms for protecting sensitive information.
- *When encryption is needed?*
	- For data in transit
	- For data at res

- flat-file databases are databases stored as a single file on the computer
- `SQLite database` is the most common and simplest format of flat-file database, and it has a dedicated client for querying it from command line, `sqlite3`
###### sqlite3
- to open the database
```zsh
sqlite3 example.db
```
- to see tables
```zsh
sqlite> .tables
```
- to see the table information
```zsh
sqlite> PRAGMA table_info(<table_name>);
```

###### Week Password cracker
[site](https://crackstation.net/)


### Injection
- this flaw occurs when the application interprets user-controlled input as commands or parameters.
- Examples
	- SQL injection - when user-controlled input is passed to SQL queries, therefore an attacker can pass queries to manipulate the outcome of such queries
	- Command Injection - when user input is passed to the system commands, therefore an attacker can execute commands on the application server.

- Defense
	- using an allow list - checking if the input is in the safe list before execution
	- stripping input - if the input contains dangerous characters remove those before processing.

##### Command Injection
- Occurs when server-side code in a web application makes a call to a function that interacts with the serve's console directly. 
- Had that vulnerability identified all you need to do to exploit it is passing `$(your_command)` as an input. 
- This is taking advantage of bash feature called ==inline commands== which allows to run commands within commands.
```zsh
echo $(whoami)
```
for instance in the above command the command `whoami` is got executed. 

### Insecure Design
- Refers to vulnerabilities which are inherent to the application's architecture.
- Example ...
##### Insecure Password Resets
[Instagram](https://thezerohack.com/hack-any-instagram) once allowed users to reset their forgotten passwords by sending them a 6-digit code to their mobile number via SMS for validation, but it was found that the rate-limiting only applied to code attempts made from the same IP, which made brute forcing possible.

### Security Misconfiguration
- Includes ...
	- Poorly configured permissions on cloud services, like S3 buckets.
	- Having unnecessary features enabled, like services, pages, accounts or privileges.
	- Default accounts with unchanged passwords.
	- Error messages that are overly detailed and allow attackers to find out more about the system.
	- Not using [HTTP security headers](https://owasp.org/www-project-secure-headers/).
	- Exposure of debugging feature in production software. For instance ==Werkzeug console== is a component for python-based web applications as it provides an interface for web servers to execute the python code. It can be accessed via URL on `/console` leading to unauthorized remote code execution `RCE`


### Vulnerable and Outdated Components
- If such component is found the exploit can be made by searching the exploit file from [Explot-DB](https://www.exploit-db.com/)

### Identification and Authentication Failures
- **Brute force attacks:** If a web application uses usernames and passwords, an attacker can try to launch brute force attacks that allow them to guess the username and passwords using multiple authentication attempts. 
- **Use of weak credentials:** Web applications should set strong password policies. If applications allow users to set passwords such as "password1" or common passwords, an attacker can easily guess them and access user accounts.
- **Weak Session Cookies:** Session cookies are how the server keeps track of users. If session cookies contain predictable values, attackers can set their own session cookies and access users' accounts.
##### Re-Registration 
- as self descriptive it is, re-registration is the registration of an existing user. For instance say there's an existing user 'admin', in application with this vulnerability you can register as a " admin" and still see what's on admin. 
### Software and Data Integrity Failure
#### Integrity 
- is the capability we have to ascertain that a piece of data remains unmodified.
- to help us with maintaining the integrity of data and software we make use of `hash`, which is sent alongside with the data and used to `check` whether the data is modified or not
- to calculate a hash of a thing on Linux, one can use, 
```zsh
md5sum file_to_check
		or
sha1sum file_to_check
		or
sha256 file_to_check
```

- when out sourcing a task  the developers should be ware of the liability of this external entity. 
- for instance, 
rather than doing this ...
```html
<script src="https://code.jquery.com/jquery-3.6.1.min.js"></script>
```
one should do 
```html
<script src="https://code.jquery.com/jquery-3.6.1.min.js" integrity="sha256-o88AwQnZB+VDvE9tvIXrMQaPlFFSUTR+nldQm1LuPXQ=" crossorigin="anonymous"></script>
```

> By setting the integrity it coerce the browser check the integrity of the source before including it to the page

##### Data Integrity Failure
###### JWT(JSON Web Token) cookies

![[Pasted image 20240319112536.png]]

- JWT is consists of three parts, 
	- Header, consists of two parts, the algorithm and the type of the cookie
  ```json
  {
  "alg": "HS256",
  "typ": "JWT"
}
```
	- Payload, contains the claims - statements about the entity and additional data.
	for instance 
	```json
	{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
	- Signature - created by taking the encoded header, encoded payload, a secret and the algorithm specified in the header and signing the resulting string, and it's signed from server-side. 
- The signature validation can be bypassed by setting the `alg` of the header to `'none'`, as this will result the signature to be `""`.  
### Security Logging and Monitoring Failures
- Logs are important in event of an incident,  to trace the attackers' activities.
- The information stored in logs should include the following:

	- HTTP status codes
	- Time Stamps
	- Usernames
	- API endpoints/page locations
	- IP addresses

- what can be detected from `logs` 
	- multiple unauthorized attempts
	- requests from anomalous IP addresses
	- use of automated tools
	- common payloads

### Server-Side Request Forgery
- This type of vulnerability occurs when an attacker can coerce a web application into sending requests on their behalf to arbitrary destinations while having control of the contents of the request itself.
- usually arises when the web application needs to use third-party services.