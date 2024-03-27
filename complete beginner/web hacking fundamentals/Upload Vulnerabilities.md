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
