An API’s authentication process is meant to validate that users are who they claim to be
### Broken Object Level Authorization (BOLA) 
This vulnerability is manifested when , UserA will be able to request UserB’s (along with many other) resources.
When hunting for BOLA there are three ingredients needed for successful exploitation.

1. Resource ID: a resource identifier will be the value used to specify a unique resource. This could be as simple as a number, but will often be more complicated.
2. Requests that access resources. In order to test if you can access another user's resource, you will need to know the requests that are necessary to obtain resources that your account should not be authorized to access.
3. Missing or flawed access controls. In order to exploit this weakness, the API provider must not have access controls in place. This may seem obvious, but just because resource IDs are predictable, does not mean there is an authorization vulnerability present.
### Broken Function Level Authorization (BFLA)
BFLA is all about performing unauthorized actions.
For BFLA we will be hunting for very similar requests to BOLA.

1. Resource ID: a resource identifier will be the value used to specify a unique resource. 
2. Requests that perform authorized actions. In order to test if you can access another update, delete, or otherwise alter other the resources of other users.
3. Missing or flawed access controls. In order to exploit this weakness, the API provider must not have access controls in place.