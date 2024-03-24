- is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing
- it  captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server.
#### key features
- `proxy` - enables interception and modification of requests and responses while interacting with web application
- `repeater` allows for capturing modifying and resending the same request multiple times.
- `intruder` allows for spraying endpoints with requests
- `decoder` serves for data transformation
- `comparer` enables the comparison of two pieces of data
- `sequencer` employed when assessing the randomness of tokens

#### The Dashboard
1. Tasks - allows us to define background tasks that the Burp Suite will perform while using the application, the default being "Live Passive Crawl" which automatically logs the pages visited
2. Event log - provides information about the actions performed by Burp Suite
3. Issue Activity - displays the vulnerabilities identified by the automated scanner
4. Advisory - more detailed information about the identified vulnerabilities.

#### Burp Proxy
- is an interceptor. It enables the capture of requests and responses between the user and target web server.
- This intercepted traffic could be ...
	- manipulated
	- sent to another tool for further processing
	- allowed to continue

>[!Note] Key Points
> * *Intercepting requests* - the requests are held back from reaching the target server, further processing could be made from here
> 
> * *Taking control* - this gives the tester to gain complete control over web traffic
> 
> * *WebSocket support* - to capture and logs WebSocket communication
> 
> * *Logs and History* - for retrospective analysis


#### Site Map & Issue Definitions of Target
- `Site Map` is a sub-tab of `Target` that allows us to map out the web applications we are targeting in a tree structure. Every page that we visit while the proxy is active will be displayed on the site map. This feature enables us to automatically generate a site map by simply browsing the web application.
- The `Issue definitions` section provides an extensive list of web vulnerabilities, complete with descriptions and references. This resource can be valuable for referencing vulnerabilities in reports or assisting in describing a particular vulnerability that may have been identified during manual testing.

#### Scoping
- another important feature of Burp Suite in which you define your interest areas, thereby helps you to focus only on that scope.





