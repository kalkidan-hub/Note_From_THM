[To be continued](https://tryhackme.com/room/bashscripting)
[Yet another continuation](https://tryhackme.com/room/catregex)

### Terminal Text Editors
- nano
- vim
- emac

### File Transportation

- wget - utility to download files from the web via HTTP
```zsh
wget https://the.website.com/path/to/the/file.txt
```
- SCP(Secure copy) - makes use of SSH protocol
```zsh
scp fileORdirectory/from/current/system user_name@ip_address_of_remote_system:/direcoryORfile/to/copy/the/file/to
```
the current system and the remote take exchange to do the vice.
- serving files from your host so that others 'wget' it.
python provides easy off the shelf means to do that..
```zsh
python3 -m http.server
```

### Processes
Process? yay a program that runs on your machine.
how to view it? 
```zsh
ps
```
wanna see more? do 
```zsh
ps aux
```
want to see real-time statistics
```zsh
top
```
what can be done on processes? 101
```zsh
kill PID SIGNAL
```

### Automation
##### cron jobs
- crontab is one one of the process that is started during boot, which is responsible for facilitating and managing cron jobs.
- crontab is a special file with formatting that is recognized by cron process. 

| crontabs's value | Description                               |
| ---------------- | ----------------------------------------- |
| MIN              | What minute to execute at                 |
| HOUR             | What hour to execute at                   |
| DOM              | What day of the month to execute at       |
| MON              | What month of the year to execute at      |
| DOW              | What day of the week to execute at        |
| CMD              | The actual command that will be executed. |
example, to execute the specified command every 12 hours, the wildcard('\*') indicates that we don't care about that value.
```zsh
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```
To edit this file, we can do
```zsh
crontab -e
```
