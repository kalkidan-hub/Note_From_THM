#### Load Balancers 
To handle the overwhelmingly growing request traffic the requests are better distributed, right? That's exactly what load balancers do. Using different algorithm to ensure that the jobs are distributed evenly, **round-robin** is one of them, they let multiple servers handle requests.

#### CDN(Content Delivery Network)
Here's the drill, disperse static files of your website - like javascript, css, images, videos - across the universe, I mean all over the world. Therefore someone making request to your website can access it from the nearby server. You are only left with serving the ones with series issues, one who wants dynamic data.

#### Databases
When websites are dealing with user's data they usually look out for the way to store the data, that's where database comes into play. Webservers communicate with database to store and recall data.

#### WAF(Web Application Firewall)

Security tool that's put between the user and web application

It analyses an http request and responses looking for common attack techniques, DDos, sql injection, or any other. If sign is shown it drops the request.



