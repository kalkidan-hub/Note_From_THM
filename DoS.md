```mermaid
sequenceDiagram
users_endpoint -->> emails_list : feeds
emails_list -->> request_program : provides email lists
request_program -->> site : sends incessant request to the site per interval
site -->> user : denies service

```

