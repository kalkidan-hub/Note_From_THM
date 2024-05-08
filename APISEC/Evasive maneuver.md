### String terminator
Null bytes and other combinations of symbols are often interpreted as string terminators used to end a string. If these symbols are not filtered out, they could terminate the API security control filters that may be in place.
When you are able to successfully send a null byte it is interpreted by many back-end programming languages as a` signifier to stop processing.`
terminators you can use:

%00
0x00
//
;
%
!
?
[]
%5B%5D
%09
%0a
%0b
%0c
%0e
### Case switching
Case switching is the literal switching of the case of the letters within the URL path or payload
### Encoding payloads
Encoded payloads can often trick WAFs while still being processed by the target application or database.
`wfuzz` can be used to accomplish this
```zsh
wfuzz -z file,wordlist/api/common.txt,base64 [http://hapihacker.com/FUZZ](http://hapihacker.com/FUZZ)
```
