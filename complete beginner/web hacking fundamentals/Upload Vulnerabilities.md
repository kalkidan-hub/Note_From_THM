Purpose ...
- Overwriting existing files on a server
- Uploading and Executing Shells on a server  
    
- Bypassing Client-Side filtering
- Bypassing various kinds of Server-Side filtering
- Fooling content type validation checks

### RCE (Remote Code Execution) 

- allow us to execute code arbitrarily on the web server. 
- There are two basic ways to achieve RCE
	- webshells
	- reverse/bind shells

### Filtering
- Client-side -- the filtering process running on the user's browser 
- server-side -- the filtration run on the server computer 

#### Kinds of filtering
- extension validation
- file type filtering
	- MIME(Multiple-purpose Internet Mail Extension) validation 
	- Magic Number validation, magic number of a file is a string of bytes at the very beginning of the file content which identifies the content

- file length filtering
- file name filtering
- file content filtering

### Bypassing client-side filtering 

Four ways ...
- Turn off `javascript` in the browser
- Intercept and modify the incoming page
- Intercept and modify the file upload
- send the file directly to the upload path -- `curl` can be used in here
```zsh
curl -X POST -F "submit:<value>" -F "<file-parameter>:@<path-to-file>" <site>
```

### Bypassing server-side filtering : Magic Number
magic numbers are used as a more accurate identifier of files. The magic number of a file is a string of hex digits, and is always the very first thing in a file.
Modifying this magic number of the forbidden file, to the allowed one might let the file bypass the server-side filtering.

### Methodology for uploading vulnerability
1. The first thing we would do is take a look at the website as a whole. Using browser extensions such as the aforementioned Wappalyzer (or by hand) we would look for indicators of what languages and frameworks the web application might have been built with. Be aware that Wappalyzer is not always 100% accurate. A good start to enumerating this manually would be by making a request to the website and intercepting the response with Burpsuite. Headers such as `server` or `x-powered-by` can be used to gain information about the server. We would also be looking for vectors of attack, like, for example, an upload page.  
    
2. Having found an upload page, we would then aim to inspect it further. Looking at the source code for client-side scripts to determine if there are any client-side filters to bypass would be a good thing to start with, as this is completely in our control.
3. We would then attempt a completely innocent file upload. From here we would look to see how our file is accessed. In other words, can we access it directly in an uploads folder? Is it embedded in a page somewhere? What's the naming scheme of the website? This is where tools such as Gobuster might come in if the location is not immediately obvious. This step is extremely important as it not only improves our knowledge of the virtual landscape we're attacking, it also gives us a baseline "accepted" file which we can base further testing on.
    - An important Gobuster switch here is the `-x` switch, which can be used to look for files with specific extensions. For example, if you added `-x php,txt,html` to your Gobuster command, the tool would append `.php`, `.txt`, and `.html` to each word in the selected wordlist, one at a time. This can be very useful if you've managed to upload a payload and the server is changing the name of uploaded files.
4. Having ascertained how and where our uploaded files can be accessed, we would then attempt a malicious file upload, bypassing any client-side filters we found in step two. We would expect our upload to be stopped by a server side filter, but the error message that it gives us can be extremely useful in determining our next steps.

