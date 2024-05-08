#### wfuzzing 
Brute force attack
```zsh
 wfuzz -d '{"email":"a@email.com","password":"FUZZ"}' -H 'Content-Type: application/json' -z file,/usr/share/wordlists/rockyou.txt -u http://127.0.0.1:8888/identity/api/auth/login --hc 405
```
password spraying
a technique to combine a long list of users with a short list of targeted passwords, hence the probability of getting a user with bad password increases.

### Sequencer
In Sequencer, we will be able to have Burp Suite send thousands of requests to the provider and perform an analysis of the tokens received in response.

### JWT_Tool
is an automated jwt attack tool
we can 
- analyse JWTs, 
- scan for weaknesses 
- forge tokens 
- brute-force signature secrets
[more on](https://github.com/ticarpi/jwt_tool/wiki)
- -h           to show more verbose help options
- -t            to specify the target URL
- -M          to specify the scan mode
    - pb         to perform a playbook audit (default tests)
    - at          to perform all tests
- -rc          to add request cookies
- -rh          to add request headers
- -rc          to add request cookies
- -pd         to add POST data

```zsh
jwt_tool -t http://target-name.com/ -rh "Authorization: Bearer JWT_Token" -M pb
```
