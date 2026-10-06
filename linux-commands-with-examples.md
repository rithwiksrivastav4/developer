# Linux Commands with Examples

This guide explains common Linux commands with:
- **What the command does**
- **Why you use it**
- **Example command**
- **Example output / practical use**

---

# 1. `pwd` — Print Working Directory

## What it does
Shows the full path of the directory you are currently inside.

## Why you use it
Useful when you are not sure where you are in the Linux filesystem.

## Example

```bash
pwd
```

Example output:

```text
/home/dev/projects
```

This means your current directory is:

```text
/home/dev/projects
```

---

# 2. `ls` — List Files and Directories

## What it does
Shows files and folders inside the current directory.

## Example

```bash
ls
```

Example output:

```text
app.js
package.json
src
logs
```

This means the directory contains:
- `app.js`
- `package.json`
- `src`
- `logs`

### Detailed list

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 dev dev  1200 Oct 6 10:00 app.js
drwxr-xr-x 2 dev dev  4096 Oct 6 09:00 src
```

### Show hidden files

```bash
ls -a
```

Example:

```text
.
..
.env
.git
app.js
```

### Recommended

```bash
ls -lah
```

This shows:
- hidden files
- permissions
- owner
- group
- file size
- modified date

---

# 3. `cd` — Change Directory

## What it does
Moves you from one folder to another.

## Example

```bash
cd /var/log
```

Now:

```bash
pwd
```

may show:

```text
/var/log
```

### Go one directory back

```bash
cd ..
```

Example:

```text
/home/dev/projects
```

becomes:

```text
/home/dev
```

### Go to home directory

```bash
cd ~
```

### Return to previous directory

```bash
cd -
```

Useful when switching between two directories.

---

# 4. `mkdir` — Create Directory

## What it does
Creates a new folder.

## Example

```bash
mkdir project
```

Now:

```bash
ls
```

may show:

```text
project
```

### Create nested folders

```bash
mkdir -p project/backend/src
```

Creates:

```text
project/
└── backend/
    └── src/
```

---

# 5. `touch` — Create Empty File

## What it does
Creates an empty file if the file does not already exist.

## Example

```bash
touch app.js
```

Check:

```bash
ls
```

Output:

```text
app.js
```

Also used to update the file's modification timestamp.

---

# 6. `cat` — Display File Content

## What it does
Prints the full contents of a file in the terminal.

## Example

Suppose `test.txt` contains:

```text
Hello Linux
Welcome Dev
```

Run:

```bash
cat test.txt
```

Output:

```text
Hello Linux
Welcome Dev
```

Useful for small files such as:
- `.env`
- configuration files
- text files

---

# 7. `less` — Read Large Files

## What it does
Opens a file page-by-page.

## Example

```bash
less application.log
```

Useful keys:

```text
q       Quit
/ERROR  Search ERROR
n       Next match
g       Go to top
G       Go to bottom
```

This is better than `cat` for very large log files.

---

# 8. `head` — Show Beginning of File

## What it does
Shows the first lines of a file.

## Example

```bash
head application.log
```

By default, it shows 10 lines.

Show first 20:

```bash
head -n 20 application.log
```

Useful when checking headers or the beginning of a log/file.

---

# 9. `tail` — Show End of File

## What it does
Shows the last lines of a file.

## Example

```bash
tail application.log
```

Shows the last 10 lines.

### Show last 100 lines

```bash
tail -n 100 application.log
```

### Monitor a live log

```bash
tail -f application.log
```

Example live output:

```text
Server started on port 3000
Database connected
GET /api/users 200
POST /api/login 200
```

Very useful during application debugging.

---

# 10. `cp` — Copy Files

## What it does
Copies files or folders.

## Example

```bash
cp app.js app-backup.js
```

Now both files exist:

```text
app.js
app-backup.js
```

### Copy a folder

```bash
cp -r project project-backup
```

---

# 11. `mv` — Move or Rename

## Rename file

```bash
mv old.txt new.txt
```

Before:

```text
old.txt
```

After:

```text
new.txt
```

## Move file

```bash
mv app.js /home/dev/project/
```

Moves `app.js` into the project directory.

---

# 12. `rm` — Remove Files

## Delete file

```bash
rm test.txt
```

## Delete directory

```bash
rm -r project
```

## Force delete

```bash
rm -rf project
```

`-r` means recursive.

`-f` means force.

> Be very careful with `rm -rf`.

---

# 13. `find` — Search Files and Directories

## Find a file

```bash
find / -name "nginx.conf"
```

Possible output:

```text
/etc/nginx/nginx.conf
```

## Find JavaScript files

```bash
find . -name "*.js"
```

Example output:

```text
./app.js
./src/server.js
./src/routes/users.js
```

## Find files larger than 100 MB

```bash
find / -type f -size +100M
```

Useful when troubleshooting disk-space problems.

---

# 14. `grep` — Search Text

Suppose `application.log` contains:

```text
INFO Server started
ERROR Database connection failed
INFO Retrying
```

Run:

```bash
grep "ERROR" application.log
```

Output:

```text
ERROR Database connection failed
```

### Ignore uppercase/lowercase

```bash
grep -i "error" application.log
```

### Search recursively

```bash
grep -r "localhost" .
```

Useful for searching code/config files.

---

# 15. `wc` — Count Lines, Words, Characters

## Count lines

```bash
wc -l application.log
```

Example:

```text
1250 application.log
```

The file has 1250 lines.

## Count words

```bash
wc -w file.txt
```

---

# 16. `sort` — Sort Data

Suppose `numbers.txt` contains:

```text
5
2
8
1
```

Run:

```bash
sort -n numbers.txt
```

Output:

```text
1
2
5
8
```

---

# 17. `uniq` — Remove Duplicate Lines

File:

```text
apple
apple
banana
banana
orange
```

Run:

```bash
uniq file.txt
```

Output:

```text
apple
banana
orange
```

Usually use:

```bash
sort file.txt | uniq
```

---

# 18. `cut` — Extract Columns

Suppose:

```text
John,25,India
Alice,30,USA
```

Run:

```bash
cut -d',' -f1 users.csv
```

Output:

```text
John
Alice
```

`-d','` means comma is the separator.

`-f1` means first field.

---

# 19. `awk` — Process Text Columns

Suppose:

```text
John 25 India
Alice 30 USA
```

Run:

```bash
awk '{print $1}' users.txt
```

Output:

```text
John
Alice
```

Print first and third columns:

```bash
awk '{print $1,$3}' users.txt
```

Output:

```text
John India
Alice USA
```

---

# 20. `sed` — Replace Text

Suppose `config.txt` contains:

```text
environment=development
```

Run:

```bash
sed 's/development/production/' config.txt
```

Output:

```text
environment=production
```

Modify the actual file:

```bash
sed -i 's/development/production/g' config.txt
```

---

# 21. `chmod` — Change Permissions

## Example

```bash
chmod +x deploy.sh
```

Makes `deploy.sh` executable.

Then:

```bash
./deploy.sh
```

### Common permissions

```bash
chmod 644 file.txt
chmod 755 script.sh
```

Meaning:

```text
644 = owner read/write, others read
755 = owner read/write/execute, others read/execute
```

---

# 22. `chown` — Change File Owner

Example:

```bash
sudo chown dev app.js
```

Change owner and group:

```bash
sudo chown dev:developers app.js
```

Recursive:

```bash
sudo chown -R dev:developers /var/www/app
```

Useful when your application has permission errors.

---

# 23. `whoami`

## What it does
Shows your current username.

```bash
whoami
```

Output:

```text
dev
```

---

# 24. `who`

Shows logged-in users.

```bash
who
```

Example:

```text
dev pts/0 2026-10-06 10:00
admin pts/1 2026-10-06 10:20
```

---

# 25. `sudo`

Runs a command with administrator/root privileges.

Example:

```bash
sudo apt update
```

Without `sudo`, you may get:

```text
Permission denied
```

---

# 26. `ps` — View Processes

```bash
ps aux
```

Example:

```text
USER   PID   CPU  MEM  COMMAND
root   101   0.1  1.0  nginx
dev    850   2.1  3.4  node server.js
```

Search Node:

```bash
ps aux | grep node
```

---

# 27. `top` — Monitor Processes

```bash
top
```

Shows live:
- CPU usage
- memory usage
- processes
- load average

Useful if server CPU is high.

---

# 28. `htop`

Interactive alternative to `top`.

```bash
htop
```

Install:

```bash
sudo apt install htop
```

---

# 29. `kill` — Stop Process

Suppose:

```bash
ps aux | grep node
```

returns PID:

```text
2345
```

Stop it:

```bash
kill 2345
```

Force stop:

```bash
kill -9 2345
```

Use `-9` only if normal termination fails.

---

# 30. `df` — Disk Space

```bash
df -h
```

Example:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1       100G   80G   20G  80%
```

Meaning:
- Total: 100 GB
- Used: 80 GB
- Free: 20 GB

Very important for server troubleshooting.

---

# 31. `du` — Directory Size

```bash
du -sh /var/log
```

Output:

```text
3.2G /var/log
```

Find large folders:

```bash
du -sh * | sort -h
```

---

# 32. `free` — RAM Usage

```bash
free -h
```

Example:

```text
              total   used   free
Mem:           16Gi    8Gi    3Gi
Swap:           4Gi    1Gi    3Gi
```

Useful when applications are slow or crashing due to memory.

---

# 33. `lscpu`

Shows CPU information.

```bash
lscpu
```

Example:

```text
CPU(s):              8
Model name:          Intel Xeon
Architecture:        x86_64
```

---

# 34. `lsblk`

Shows disks and partitions.

```bash
lsblk
```

Example:

```text
NAME   SIZE TYPE MOUNTPOINT
sda    500G disk
├─sda1 100G part /
└─sda2 400G part /data
```

---

# 35. `ip a` — IP Addresses

```bash
ip a
```

Example:

```text
inet 192.168.1.100/24
```

This means the server IP is:

```text
192.168.1.100
```

---

# 36. `ip route` — Routing Table

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

This shows the default gateway.

---

# 37. `ping` — Connectivity Test

```bash
ping -c 4 google.com
```

Example:

```text
64 bytes from 142.250.x.x: time=20 ms
```

If successful, network connectivity is working.

---

# 38. `nslookup` — DNS Lookup

```bash
nslookup example.com
```

Example:

```text
Name: example.com
Address: 93.184.216.34
```

Shows what IP a domain resolves to.

---

# 39. `dig` — Advanced DNS Lookup

```bash
dig example.com
```

Short result:

```bash
dig +short example.com
```

Output:

```text
93.184.216.34
```

Check MX:

```bash
dig example.com MX
```

---

# 40. `ss` — Check Ports

```bash
sudo ss -tulpn
```

Example:

```text
LISTEN 0 511 0.0.0.0:443 users:(("nginx",pid=1234))
LISTEN 0 128 0.0.0.0:3000 users:(("node",pid=5678))
```

This tells you:
- Nginx is listening on port 443
- Node is listening on port 3000

Check port 443:

```bash
sudo ss -tulpn | grep :443
```

---

# 41. `lsof` — Find Process Using Port

```bash
sudo lsof -i :3000
```

Example:

```text
COMMAND PID USER FD TYPE DEVICE NODE NAME
node   5678 dev  21u IPv4 ... TCP *:3000 (LISTEN)
```

This tells you Node PID 5678 uses port 3000.

---

# 42. `curl` — Test Website/API

## GET request

```bash
curl http://localhost:3000
```

Output:

```text
API is running
```

## Headers

```bash
curl -I https://example.com
```

Example:

```text
HTTP/2 200
content-type: text/html
```

## Debug connection

```bash
curl -v https://example.com
```

Useful for:
- APIs
- SSL
- Nginx
- HTTP errors
- backend connectivity

---

# 43. `wget` — Download Files

```bash
wget https://example.com/app.zip
```

Output may show:

```text
Saving to: app.zip
100% downloaded
```

---

# 44. `apt` — Ubuntu/Debian Package Manager

Update package information:

```bash
sudo apt update
```

Install Nginx:

```bash
sudo apt install nginx
```

Remove Nginx:

```bash
sudo apt remove nginx
```

Upgrade packages:

```bash
sudo apt upgrade
```

---

# 45. `dnf` — RHEL/Rocky/AlmaLinux Package Manager

```bash
sudo dnf install nginx
sudo dnf update
sudo dnf remove nginx
```

---

# 46. `systemctl` — Manage Services

Check Nginx:

```bash
systemctl status nginx
```

Example:

```text
Active: active (running)
```

Start:

```bash
sudo systemctl start nginx
```

Stop:

```bash
sudo systemctl stop nginx
```

Restart:

```bash
sudo systemctl restart nginx
```

Reload:

```bash
sudo systemctl reload nginx
```

Enable after reboot:

```bash
sudo systemctl enable nginx
```

---

# 47. `journalctl` — Service Logs

Nginx logs:

```bash
journalctl -u nginx
```

Last 100 lines:

```bash
journalctl -u nginx -n 100
```

Live logs:

```bash
journalctl -u nginx -f
```

Very useful when a Linux service fails to start.

---

# 48. Nginx Commands

Check version:

```bash
nginx -v
```

Test configuration:

```bash
sudo nginx -t
```

Successful result:

```text
syntax is ok
test is successful
```

Reload configuration:

```bash
sudo systemctl reload nginx
```

Check errors:

```bash
tail -f /var/log/nginx/error.log
```

---

# 49. SSH — Connect to Remote Server

```bash
ssh dev@192.168.1.100
```

Using a custom port:

```bash
ssh -p 2222 dev@192.168.1.100
```

Using a key:

```bash
ssh -i server.pem ubuntu@server-ip
```

Debug SSH:

```bash
ssh -vvv dev@server
```

---

# 50. `scp` — Copy Files Between Servers

Local to server:

```bash
scp app.zip dev@server:/home/dev/
```

Server to local:

```bash
scp dev@server:/home/dev/app.log .
```

Copy folder:

```bash
scp -r project dev@server:/var/www/
```

---

# 51. `rsync` — Sync Files

```bash
rsync -av project/ dev@server:/var/www/project/
```

Useful for:
- deployments
- backups
- transferring only changed files

With progress:

```bash
rsync -av --progress project/ backup/
```

---

# 52. `tar` — Archive Files

Create:

```bash
tar -czvf backup.tar.gz project/
```

Extract:

```bash
tar -xzvf backup.tar.gz
```

Useful for server backups.

---

# 53. `zip` / `unzip`

Create:

```bash
zip -r project.zip project/
```

Extract:

```bash
unzip project.zip
```

---

# 54. Environment Variables

Set variable:

```bash
export NODE_ENV=production
```

Check:

```bash
echo $NODE_ENV
```

Output:

```text
production
```

---

# 55. Pipes `|`

A pipe sends one command's output into another command.

Example:

```bash
ps aux | grep node
```

`ps aux` returns all processes.

`grep node` keeps only Node processes.

---

# 56. Output Redirection

Overwrite file:

```bash
echo "hello" > file.txt
```

Append:

```bash
echo "world" >> file.txt
```

Save command output:

```bash
ls -lah > files.txt
```

Save errors:

```bash
node app.js 2> errors.log
```

Save everything:

```bash
node app.js > app.log 2>&1
```

---

# 57. Command Chaining

Run command 2 only if command 1 succeeds:

```bash
npm install && npm start
```

Example:
1. dependencies install successfully
2. application starts

Run second if first fails:

```bash
npm start || echo "Application failed"
```

---

# 58. Bash Variables

```bash
name="Dev"
echo "$name"
```

Output:

```text
Dev
```

Store command output:

```bash
today=$(date)
echo "$today"
```

---

# 59. Bash Script Example

Create:

```bash
nano deploy.sh
```

Content:

```bash
#!/bin/bash

cd /var/www/myapp

git pull
npm install
npm run build

pm2 restart myapp

sudo nginx -t && sudo systemctl reload nginx

echo "Deployment completed"
```

Give permission:

```bash
chmod +x deploy.sh
```

Run:

```bash
./deploy.sh
```

---

# 60. Git Commands

Clone:

```bash
git clone https://github.com/company/project.git
```

Check:

```bash
git status
```

Add:

```bash
git add .
```

Commit:

```bash
git commit -m "Fix login bug"
```

Pull:

```bash
git pull
```

Push:

```bash
git push
```

Create branch:

```bash
git switch -c feature/login
```

View commits:

```bash
git log --oneline
```

---

# 61. Node.js / npm

Check versions:

```bash
node -v
npm -v
```

Install dependencies:

```bash
npm install
```

Start application:

```bash
npm start
```

Development:

```bash
npm run dev
```

Build frontend:

```bash
npm run build
```

---

# 62. PM2

Start application:

```bash
pm2 start server.js --name api
```

List:

```bash
pm2 list
```

Example:

```text
api    online
```

Logs:

```bash
pm2 logs api
```

Restart:

```bash
pm2 restart api
```

Stop:

```bash
pm2 stop api
```

Persist:

```bash
pm2 save
pm2 startup
```

---

# 63. Docker

List running containers:

```bash
docker ps
```

Example:

```text
CONTAINER ID IMAGE   PORTS
123456       nginx   0.0.0.0:8080->80/tcp
```

Run Nginx:

```bash
docker run -d -p 8080:80 nginx
```

Visit:

```text
http://server-ip:8080
```

Logs:

```bash
docker logs container_id
```

Enter container:

```bash
docker exec -it container_id bash
```

Stop:

```bash
docker stop container_id
```

Remove:

```bash
docker rm container_id
```

---

# 64. Docker Build

```bash
docker build -t myapp:1.0 .
```

Run:

```bash
docker run -d -p 3000:3000 myapp:1.0
```

---

# 65. Docker Compose

Start:

```bash
docker compose up -d
```

Check:

```bash
docker compose ps
```

Logs:

```bash
docker compose logs -f
```

Stop:

```bash
docker compose down
```

Rebuild:

```bash
docker compose up -d --build
```

---

# 66. Firewall — UFW

Check:

```bash
sudo ufw status
```

Allow SSH:

```bash
sudo ufw allow 22
```

Allow HTTP:

```bash
sudo ufw allow 80
```

Allow HTTPS:

```bash
sudo ufw allow 443
```

Enable:

```bash
sudo ufw enable
```

---

# 67. OpenSSL

Check HTTPS certificate:

```bash
openssl s_client -connect example.com:443 -servername example.com
```

Check expiry:

```bash
openssl s_client -connect example.com:443 -servername example.com 2>/dev/null |
openssl x509 -noout -dates
```

Example:

```text
notBefore=Oct 1 00:00:00 2026 GMT
notAfter=Dec 30 23:59:59 2026 GMT
```

---

# 68. Cron Jobs

Edit:

```bash
crontab -e
```

Run backup every day at 2 AM:

```cron
0 2 * * * /home/dev/backup.sh
```

Run every 5 minutes:

```cron
*/5 * * * * /home/dev/check.sh
```

List:

```bash
crontab -l
```

---

# 69. Mount Disk

View:

```bash
lsblk
```

Mount:

```bash
sudo mount /dev/sdb1 /mnt/data
```

Unmount:

```bash
sudo umount /mnt/data
```

---

# 70. `uptime`

```bash
uptime
```

Example:

```text
17:30:00 up 10 days, 3:20, 2 users, load average: 0.40, 0.35, 0.30
```

Shows:
- server uptime
- users
- system load

---

# 71. `vmstat`

```bash
vmstat 2
```

Shows CPU, memory and processes every 2 seconds.

Useful for performance troubleshooting.

---

# 72. `traceroute`

```bash
traceroute google.com
```

Shows the network path from your server to the destination.

Useful when:
- connection is slow
- packets are blocked
- network routing is wrong

---

# 73. `nc` / Netcat

Test if port 443 is reachable:

```bash
nc -zv example.com 443
```

Success:

```text
Connection to example.com 443 port [tcp/https] succeeded!
```

Test SQL Server:

```bash
nc -zv database-server 1433
```

---

# 74. PostgreSQL

Connect:

```bash
psql -h localhost -U postgres -d mydb
```

List databases:

```sql
\l
```

List tables:

```sql
\dt
```

Exit:

```sql
\q
```

---

# 75. MySQL

Connect:

```bash
mysql -u root -p
```

Remote:

```bash
mysql -h database-server -u admin -p
```

---

# 76. SQL Server

```bash
sqlcmd -S database-server -U username -P password
```

Use this to test SQL Server connectivity from Linux.

---

# 77. Find Largest Files

```bash
sudo du -ah /var | sort -rh | head -20
```

Example:

```text
10G /var/lib/docker
5G  /var/log
2G  /var/www
```

This quickly shows where disk space is being used.

---

# 78. Deleted Files Still Using Disk

```bash
sudo lsof +L1
```

Useful situation:

```bash
df -h
```

shows disk full, but:

```bash
du -sh /
```

does not show enough data.

A running process may still have a deleted file open.

---

# 79. Login History

```bash
last
```

Example:

```text
dev pts/0 192.168.1.20 Tue Oct 6 10:00
```

Failed login attempts:

```bash
sudo lastb
```

---

# 80. Common Server Troubleshooting Example

Suppose your website is not opening.

## Step 1 — Check server

```bash
uptime
```

## Step 2 — Check RAM

```bash
free -h
```

## Step 3 — Check disk

```bash
df -h
```

## Step 4 — Check application

```bash
pm2 list
```

## Step 5 — Check application logs

```bash
pm2 logs api
```

## Step 6 — Check port

```bash
sudo ss -tulpn | grep :3000
```

## Step 7 — Test backend locally

```bash
curl http://localhost:3000
```

## Step 8 — Check Nginx

```bash
systemctl status nginx
```

## Step 9 — Validate Nginx config

```bash
sudo nginx -t
```

## Step 10 — Check Nginx error log

```bash
tail -100 /var/log/nginx/error.log
```

## Step 11 — Check HTTPS

```bash
curl -v https://your-domain.com
```

This workflow helps identify whether the problem is:
- application
- port
- firewall
- Nginx
- SSL
- DNS
- disk
- RAM
- server process

---

# 81. Commands You Should Memorize

```bash
pwd
ls -lah
cd
mkdir
touch
cp
mv
rm
cat
less
head
tail
tail -f
grep
find
chmod
chown
sudo
ps aux
top
kill
df -h
du -sh
free -h
lsblk
ip a
ip route
ping
curl
wget
dig
nslookup
ss -tulpn
lsof -i
ssh
scp
rsync
systemctl
journalctl
git
npm
pm2
docker
docker compose
nginx -t
openssl
crontab
```

---

# 82. Quick Real-World Examples

## Check which process is using port 443

```bash
sudo ss -tulpn | grep :443
```

## Check which process uses port 3000

```bash
sudo lsof -i :3000
```

## Check if backend is running

```bash
curl http://localhost:3000
```

## Check Nginx config

```bash
sudo nginx -t
```

## Restart Nginx

```bash
sudo systemctl restart nginx
```

## Watch Nginx errors live

```bash
tail -f /var/log/nginx/error.log
```

## Check Node application

```bash
pm2 list
```

## Watch Node logs

```bash
pm2 logs
```

## Check disk

```bash
df -h
```

## Find biggest directories

```bash
sudo du -xhd1 / | sort -h
```

## Check RAM

```bash
free -h
```

## Check IP

```bash
ip a
```

## Check DNS

```bash
dig your-domain.com
```

## Check SSL certificate

```bash
openssl s_client -connect your-domain.com:443 -servername your-domain.com
```

## Test remote port

```bash
nc -zv server-ip 443
```

---

# Final Note

The fastest way to learn Linux is to understand commands by purpose:

```text
FILES       → ls, cp, mv, rm, find
TEXT        → cat, grep, awk, sed
PERMISSIONS → chmod, chown
PROCESSES   → ps, top, kill
MEMORY      → free
DISK        → df, du, lsblk
NETWORK     → ip, ping, ss, curl, dig
SERVICES    → systemctl, journalctl
REMOTE      → ssh, scp, rsync
WEB SERVER  → nginx
NODE        → npm, pm2
CONTAINERS  → docker
SECURITY    → ufw, openssl
SCHEDULING  → cron
```

Use this file as a practical Linux + DevOps reference.
