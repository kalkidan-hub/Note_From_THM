s a vulnerability that takes place when an application retrieves remote resources without validating user input. An attacker can supply their own input, in the form of a URL, to control the remote resources that are retrieved by the targeted server
There are two types of SSRF vulnerabilities, 
### In Band SSRF, 
means that the server responds with the resources specified by the end user. If the attacker specifies the payload as [http://google.com](http://google.com/) to a server with an In-Band SSRF vulnerability the server would make the request and respond to the attacker with information served from google.com. 
### Blind SSRF 
takes place when the attacker supplies a URL and the server makes the request but does not send information from the specified URL back to the attacker. In the case of Blind SSRF, you would need a web server that will capture the request from the target to prove that you forced the server to make the request.` webhook.site` is one of such servers

When targeting an API for SSRF vulnerabilities, you will want to look for requests that have any of the following:  

- Include full URLs in the POST body or parameters
- Include URL paths (or partial URLs) in the POST body or parameters
- Headers that include URLs like Referer
- Allows for user input that may result in a server retrieving resources


### From THM
SSRF allows an attacker to interact with internal systems, potentially leading to data leaks, service disruption or even to remote code execution... how??
