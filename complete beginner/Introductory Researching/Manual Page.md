
>[!Note] Man page is a document about various commands, utilities and system calls that allow users to obtain detailed information.


```c
man man
```


![[Pasted image 20240311222148.png]]

#### Headings

Although they may vary from vendor to vendor the common headings included into a man page are as follows. 
- Name
- Synopsis - shows how the command is used
- Description - describes the command as to what it does and how to use it
- Examples - some use cases of how to use the command 
- Diagnostics(Exit Values) - lists status or error messages returned by the command 
- Files - lists supplementary files used by UNIX to run this specific command
- Limits - limitation of the utility
- Portability - lists other systems where the utility is available
- See Also -  list of related pages
- History - when first appeared 
- Warnings - important advice for users
- Notes - important information

#### Sections

The entire Linux manual collection of pages are traditionally divided into numbered sections:

- **Section 1** : Shell commands and applications
- **Section 2** : Basic kernel services – system calls and error codes
- **Section 3** : Library information for programmers
- **Section 4** : Network services – if TCP/IP or NFS is installed Device drivers and network protocols
- **Section 5** : Standard file formats – for example: shows what a __tar__ archive looks like.
- **Section 6** : Games
- **Section 7** : Miscellaneous files and documents
- **Section 8** : System administration and maintenance commands
- **Section 9** : Obscure kernel specs and interfaces

Example:
```c
man 5 passwd
```

reveals PASSWD(5)  man page. 

You don't know what man section the command or utility you are looking for has, here is a better guide, ```
```
whatis
```

![[Pasted image 20240312100619.png]]
