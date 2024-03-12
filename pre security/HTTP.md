(Hyper Text Transfer Protocol)
Is a set of rules used for communicating with web servers for the transmission of web page data.

#### URL

Is an instruction on how to access a resource on the internet.

*how would the request and response looks like?*
##### request

![[Pasted image 20240309104721.png |800]]

##### response

![[Pasted image 20240309104907.png |1500]]


> [!NOTE] Note
> The request always ends with a blank line telling the web server that the request has finished



The state of the connection is close, because http is stateless protocol, meaning each request-response cycle is independent.

#### HTTP methods
- GET - to get information from a web server
- POST - to submit data to the web server, potentially to create new entry
- PUT - to submit data to a web server to update information
- DELETE - to remove information/record from a web server.

#### HTTP Status Code

==http response's first line===

- 100-199(Response)  The first part of the request is accepted
- 200 - 299(Success) The request is successful
- 300 - 399 (Redirect) The request is redirected to another resource
- 400 - 499 (Client Errors) The request is erroneous from the client side
- 500 - 599 (Server Errors) The server run to a problem while processing the request

#### Cookies

*What are cookies?*

A piece of data(token) that is saved/stored on your local machine after receiving a response that contains a "set-cookie" header, and in which you include in "cookie" header of the subsequent requests you will make to remind the server who you are.
