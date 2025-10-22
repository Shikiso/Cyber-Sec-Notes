# System
- `ss` - Used to show the network sockets statistics
- `ps` - Show running processes (can use `ps <user>` to show users processes)
	- `ps aux` - Show system services
- `kill <pid>` - Kill running process
- `systemctl <option> <service>` - To control system servers. Options:
	- Start
	- Stop
	- Enable
	- Disable
- `&` - To background a command (`echo "hello" &`, can also use Ctrl+z)
- `fg` - Bring background service back
### Cron/Crontab
Crontab can be opened using `crontab -e` (has issues with kitty)
Responsible for managing processes executed.
`crontabs` is the file that holds the commands and when to execute them.
`crontabs` requires 6 values, MIN, HOUR, DOM, MON, DOW, CMD.

| Value | Description                               |
| ----- | ----------------------------------------- |
| MIN   | What minute to execute at                 |
| HOUR  | What hour to execute at                   |
| DOM   | What day of the month to execute at       |
| MON   | What month of the year to execute at      |
| DOW   | What day of the week to execute at        |
| CMD   | The actual command that will be executed. |
For example if you wish to backup the `/home/cmnatic/Documents` every 12 hours:
`0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/`
# Files/Directories
- `wget` - Download files via HTTP 
	- `wget https://site.com/file.txt`
- `scp` - Transfer files using SSH
- Copy file from your system to a remote system
	- `scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`
- Copy file from remote system to your system
	- `scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt`
- `python3 -m http.server` - Host web server on your machine to download files from