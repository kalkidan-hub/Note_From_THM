### Passive Recon
- google dorking
- git dorking
- [trufflehog](https://trufflesecurity.com/trufflehog)
- [shodan](https://www.shodan.io)
- [wayback machine](https://web.archive.org)

### Active Recon
- nmap 
  ```zsh
  nmap -sV --script=http-enum <target> -p 80,443,8000,8080
```
- OWASP amass
- dirsearch/ `gobuster`
  ```zsh
  gobuster dir -u target-name.com:8000 -w /home/hapihacker/api/wordlists/common_apis_160
```

- `kiterunner`
  ```zsh
kr scan HTTP://127.0.0.1 -w ~/api/wordlists/data/kiterunner/routes-large.kite
```
- DevTools
- Postman


 