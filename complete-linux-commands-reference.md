# Complete Linux Commands Reference

This Markdown guide covers practical Linux commands from beginner level through developer, DevOps, networking, server administration, Docker, Git, Nginx, SSL, monitoring, troubleshooting, and automation.

> Linux contains thousands of commands and available commands vary by distribution. This guide focuses on the most useful commands for daily development, DevOps, and server administration.

---

# 1. Basic Linux Information

| Command | Why / When to use |
|---|---|
| `whoami` | Shows the currently logged-in username |
| `hostname` | Shows the machine/server hostname |
| `hostnamectl` | Shows or changes hostname and OS/system information |
| `uname` | Displays system/kernel information |
| `uname -a` | Displays complete kernel/system information |
| `uname -r` | Shows Linux kernel version |
| `date` | Displays current date and time |
| `cal` | Displays calendar |
| `uptime` | Shows how long the server has been running and load average |
| `clear` | Clears terminal screen |
| `history` | Shows previously executed commands |
| `history 20` | Shows last 20 commands |
| `man ls` | Opens manual/help page for `ls` |
| `ls --help` | Shows available options for a command |
| `which python` | Shows executable path |
| `whereis nginx` | Finds binary/source/manual locations |
| `type cd` | Shows whether command is shell builtin, alias, etc. |

```bash
whoami
hostname
uname -a
uptime
```

---

# 2. Navigation Commands

## `pwd`

Shows your current directory.

```bash
pwd
```

Example output:

```text
/home/dev/projects
```

## `ls`

Lists files and directories.

```bash
ls
ls -l
ls -a
ls -lh
ls -lah
ls -lt
ls -ltr
```

## `cd`

Change directory.

```bash
cd /var/log
cd
cd ~
cd ..
cd ../..
cd -
cd /
```

---

# 3. Directory Management

Create directory:

```bash
mkdir test
```

Create multiple directories:

```bash
mkdir dir1 dir2 dir3
```

Create nested directories:

```bash
mkdir -p project/backend/src
```

Delete empty directory:

```bash
rmdir test
```

Delete directory including files:

```bash
rm -r test
```

Force delete:

```bash
rm -rf test
```

> Be extremely careful with `rm -rf`, especially as root.

---

# 4. File Creation

Create an empty file:

```bash
touch file.txt
```

Create multiple files:

```bash
touch file1.txt file2.txt file3.txt
```

Create/write using `echo`:

```bash
echo "Hello Linux" > file.txt
```

Append:

```bash
echo "New line" >> file.txt
```

---

# 5. Reading Files

## `cat`

```bash
cat file.txt
cat file1.txt file2.txt
```

## `less`

```bash
less application.log
```

Useful controls:

```text
q       quit
/word   search
n       next result
G       bottom
g       top
```

## `more`

```bash
more file.txt
```

## `head`

```bash
head file.txt
head -n 20 file.txt
```

## `tail`

```bash
tail file.txt
tail -n 100 application.log
tail -f application.log
tail -f /var/log/nginx/error.log
```

---

# 6. Copy Files

```bash
cp file.txt backup.txt
cp file.txt /home/dev/
cp -r source destination
cp -a source destination
cp -i file1 file2
```

---

# 7. Move / Rename

```bash
mv old.txt new.txt
mv file.txt /home/dev/
mv project /opt/
```

---

# 8. Delete Files

```bash
rm file.txt
rm file1.txt file2.txt
rm -i file.txt
rm -r folder
rm -rf folder
```

---

# 9. Search Files

```bash
find / -name "nginx.conf"
find / -iname "README.md"
find /home -type d -name "node_modules"
find /home -type f -name "*.log"
find / -type f -size +100M
find . -mtime -1
find . -name "*.tmp" -delete
```

---

# 10. Search Inside Files

```bash
grep "ERROR" application.log
grep -i "error" application.log
grep -n "ERROR" application.log
grep -r "database" .
grep -E "ERROR|WARNING" application.log
grep -v "INFO" application.log
grep -i "failed" /var/log/syslog
```

---

# 11. Text Processing

## `wc`

```bash
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

## `sort`

```bash
sort file.txt
sort -n numbers.txt
sort -r file.txt
```

## `uniq`

```bash
sort file.txt | uniq
sort file.txt | uniq -c
```

## `cut`

```bash
cut -d',' -f1 file.csv
```

## `awk`

```bash
awk '{print $1}' file.txt
awk -F',' '{print $1,$3}' file.csv
ps aux | awk '{print $1,$2,$11}'
```

## `sed`

```bash
sed 's/old/new/' file.txt
sed 's/old/new/g' file.txt
sed -i 's/old/new/g' file.txt
sed -i '5d' file.txt
```

---

# 12. File Permissions

```bash
ls -l
```

Permission symbols:

```text
r = read
w = write
x = execute
```

Groups:

```text
owner
group
others
```

## `chmod`

```bash
chmod +x script.sh
chmod 644 file.txt
chmod 755 folder
chmod 777 file
```

Permission values:

```text
4 = read
2 = write
1 = execute

7 = rwx
6 = rw-
5 = r-x
4 = r--
```

> Avoid `777` unless absolutely necessary.

---

# 13. Ownership

## `chown`

```bash
sudo chown dev file.txt
sudo chown dev:developers file.txt
sudo chown -R dev:developers /var/www/app
```

## `chgrp`

```bash
chgrp developers file.txt
```

---

# 14. Users

```bash
whoami
who
w
cat /etc/passwd
sudo useradd dev
sudo adduser dev
sudo passwd dev
sudo userdel dev
sudo userdel -r dev
```

---

# 15. Groups

```bash
groups
sudo groupadd developers
sudo usermod -aG developers dev
groups dev
```

---

# 16. Root / sudo

```bash
sudo command
sudo apt update
sudo -i
su username
su -
```

---

# 17. Process Management

```bash
ps
ps aux
ps aux | grep nginx
ps -ef
top
htop
```

Install `htop` on Ubuntu/Debian:

```bash
sudo apt install htop
```

---

# 18. Kill Processes

```bash
kill 1234
kill -9 1234
pkill nginx
killall node
```

---

# 19. Background Processes

```bash
node server.js &
jobs
fg
bg
nohup node server.js &
nohup node server.js > app.log 2>&1 &
```

---

# 20. Disk Usage

## `df`

```bash
df
df -h
df -h /
```

## `du`

```bash
du -sh folder
du -sh .
du -sh *
du -sh * | sort -h
du -h /var | sort -rh | head -20
```

---

# 21. Memory

```bash
free
free -h
```

---

# 22. CPU Information

```bash
lscpu
cat /proc/cpuinfo
nproc
```

---

# 23. Hardware

```bash
sudo dmidecode --type memory
lsblk
lspci
lsusb
```

---

# 24. Network Commands

```bash
ip addr
ip a
ip -4 addr
ip link
ip route
route -n
```

---

# 25. Ping

```bash
ping google.com
ping -c 4 google.com
```

---

# 26. DNS

## `nslookup`

```bash
nslookup google.com
```

## `dig`

```bash
dig google.com
dig google.com A
dig google.com CNAME
dig google.com MX
dig @8.8.8.8 google.com
dig +short google.com
```

---

# 27. Open Ports

```bash
ss -tulpn
ss -tlnp
ss -tulpn | grep :443
ss -tulpn | grep :80
```

Older equivalent:

```bash
netstat -tulpn
```

Install if needed:

```bash
sudo apt install net-tools
```

---

# 28. Find Process Using Port

```bash
sudo lsof -i :3000
sudo lsof -i :443
sudo ss -lptn 'sport = :443'
```

---

# 29. Test HTTP APIs

## `curl`

```bash
curl http://localhost:3000
curl -I https://example.com
curl -v https://example.com
curl -L https://example.com
curl -X POST http://localhost:3000/api/login
```

JSON POST:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-d '{"username":"admin","password":"123"}' \
http://localhost:3000/api/login
```

Authorization:

```bash
curl -H "Authorization: Bearer TOKEN" \
https://api.example.com/users
```

---

# 30. Download Files

## `wget`

```bash
wget https://example.com/file.zip
wget -O app.zip https://example.com/file.zip
wget -c https://example.com/large.zip
```

---

# 31. Package Management — Ubuntu/Debian

```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx
sudo apt purge nginx
apt search nginx
sudo apt autoremove
```

---

# 32. RHEL / CentOS / Rocky / AlmaLinux

```bash
sudo dnf install nginx
sudo dnf update
sudo dnf remove nginx
sudo yum install nginx
```

---

# 33. Services — systemctl

```bash
systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
sudo systemctl enable nginx
sudo systemctl disable nginx
sudo systemctl enable --now nginx
systemctl --type=service --state=running
```

---

# 34. Logs — journalctl

```bash
journalctl
journalctl -u nginx
journalctl -u nginx -f
journalctl -u nginx -n 100
journalctl -b
journalctl -p err
```

---

# 35. Nginx

```bash
nginx -v
sudo nginx -t
sudo systemctl restart nginx
sudo systemctl reload nginx
systemctl status nginx
```

Important paths:

```text
/etc/nginx/nginx.conf
/etc/nginx/sites-available/
/etc/nginx/sites-enabled/
/var/log/nginx/access.log
/var/log/nginx/error.log
```

Monitor errors:

```bash
tail -f /var/log/nginx/error.log
```

---

# 36. Apache

```bash
systemctl status apache2
sudo systemctl restart apache2
apachectl configtest
```

RHEL-based systems commonly use:

```bash
httpd
```

---

# 37. SSH

```bash
ssh user@192.168.1.10
ssh -p 2222 user@server
ssh -i key.pem ubuntu@server
ssh -v user@server
ssh -vvv user@server
```

---

# 38. SSH Keys

```bash
ssh-keygen
ssh-keygen -t ed25519
ssh-copy-id user@server
```

Important locations:

```text
~/.ssh/
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
~/.ssh/authorized_keys
```

---

# 39. SCP

```bash
scp file.txt user@server:/home/user/
scp user@server:/home/user/file.txt .
scp -r project user@server:/opt/
scp -i key.pem file.txt ubuntu@server:/home/ubuntu/
```

---

# 40. rsync

```bash
rsync -av source/ destination/
rsync -av project/ user@server:/var/www/project/
rsync -av --progress source/ destination/
rsync -av --delete source/ destination/
```

> Be careful with `--delete`.

---

# 41. Compress Files

## `tar`

```bash
tar -cvf backup.tar folder/
tar -xvf backup.tar
tar -czvf backup.tar.gz folder/
tar -xzvf backup.tar.gz
```

## `zip`

```bash
zip file.zip file.txt
zip -r project.zip project/
unzip project.zip
```

---

# 42. gzip

```bash
gzip file.txt
gunzip file.txt.gz
```

---

# 43. Environment Variables

```bash
env
echo $PATH
export NODE_ENV=production
echo $NODE_ENV
source ~/.bashrc
```

Persistent Bash settings are commonly stored in:

```text
~/.bashrc
```

---

# 44. Pipes

```bash
ps aux | grep nginx
cat application.log | grep ERROR
grep ERROR application.log
```

---

# 45. Redirect Output

```bash
command > output.txt
command >> output.txt
command 2> errors.txt
command > output.txt 2>&1
command > /dev/null 2>&1
```

---

# 46. Command Chaining

Run second command only if first succeeds:

```bash
npm install && npm start
```

Run regardless:

```bash
command1 ; command2
```

Run second if first fails:

```bash
command1 || command2
```

Example:

```bash
nginx -t && systemctl reload nginx
```

---

# 47. Bash Variables

```bash
name="Dev"
echo $name
date_now=$(date)
echo "$date_now"
```

---

# 48. Bash Script

Example deployment script:

```bash
#!/bin/bash

echo "Starting application"

cd /var/www/app

git pull

npm install

npm run build

sudo systemctl restart nginx

echo "Deployment completed"
```

Make executable:

```bash
chmod +x script.sh
```

Run:

```bash
./script.sh
```

---

# 49. Editors

## Nano

```bash
nano file.txt
```

Controls:

```text
Ctrl + O    Save
Ctrl + X    Exit
```

## Vim

```bash
vim file.txt
```

Controls:

```text
i       Insert mode
:w      Save
:q      Quit
:wq     Save and quit
:q!     Force quit
```

---

# 50. Git Commands

```bash
git init
git clone repository-url
git status
git add .
git commit -m "fix API issue"
git pull
git push
git branch
git branch feature/login
git checkout feature/login
git switch feature/login
git switch -c feature/login
git log
git log --oneline
git diff
git stash
git stash pop
```

---

# 51. Node.js Commands

```bash
node -v
npm -v
npm install
npm install express
npm install -D nodemon
npm start
npm run build
npm run dev
```

---

# 52. PM2

```bash
sudo npm install -g pm2
pm2 start server.js
pm2 start server.js --name api
pm2 list
pm2 logs
pm2 logs api
pm2 restart api
pm2 stop api
pm2 delete api
pm2 save
pm2 startup
```

---

# 53. Docker

```bash
docker --version
docker ps
docker ps -a
docker images
docker pull nginx
docker run nginx
docker run -d nginx
docker run -d -p 8080:80 nginx
docker stop container_id
docker start container_id
docker restart container_id
docker rm container_id
docker rmi image_id
docker logs container_id
docker logs -f container_id
docker exec -it container_id bash
docker exec -it container_id sh
```

---

# 54. Docker Build

```bash
docker build -t myapp .
docker build -t myapp:1.0 .
docker run -d -p 3000:3000 myapp:1.0
```

---

# 55. Docker Compose

```bash
docker compose up
docker compose up -d
docker compose down
docker compose up -d --build
docker compose logs
docker compose logs -f
```

---

# 56. Firewall — UFW

```bash
sudo ufw status
sudo ufw enable
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
sudo ufw allow 3000
sudo ufw delete allow 3000
```

---

# 57. Firewall — firewalld

```bash
sudo firewall-cmd --state
sudo firewall-cmd --permanent --add-port=443/tcp
sudo firewall-cmd --reload
sudo firewall-cmd --list-all
```

---

# 58. SSL / OpenSSL

```bash
openssl s_client -connect example.com:443
openssl s_client -connect example.com:443 -servername example.com
```

Certificate dates:

```bash
openssl s_client \
-connect example.com:443 \
-servername example.com 2>/dev/null |
openssl x509 -noout -dates
```

Certificate details:

```bash
openssl x509 -in certificate.crt -text -noout
```

Private key check:

```bash
openssl rsa -in private.key -check
```

---

# 59. Cron Jobs

Edit:

```bash
crontab -e
```

List:

```bash
crontab -l
```

Daily at 2 AM:

```cron
0 2 * * * /home/dev/backup.sh
```

Cron structure:

```text
minute hour day month weekday
```

Every 5 minutes:

```cron
*/5 * * * *
```

---

# 60. Mounting Disks

```bash
lsblk
df -h
sudo mount /dev/sdb1 /mnt/data
sudo umount /mnt/data
```

Persistent mount configuration:

```text
/etc/fstab
```

---

# 61. System Information

```bash
cat /etc/os-release
uname -r
lscpu
free -h
df -h
lsblk
```

---

# 62. Linux Load

```bash
uptime
nproc
```

Load average commonly shows approximately:

```text
1 minute
5 minutes
15 minutes
```

---

# 63. Monitor Resources

```bash
top
htop
iostat
iftop
vmstat
vmstat 2
```

---

# 64. Ports / Network Debugging

```bash
ss -lntp | grep 3000
lsof -i :3000
curl http://localhost:3000
curl http://server-ip:3000
```

---

# 65. DNS Debugging

```bash
dig example.com
nslookup example.com
cat /etc/resolv.conf
dig @8.8.8.8 example.com
```

---

# 66. Network Path Debugging

```bash
traceroute google.com
tracepath google.com
```

Install traceroute:

```bash
sudo apt install traceroute
```

---

# 67. Test TCP Port

```bash
nc -zv server 443
nc -zv 192.168.1.100 1433
nc -zv server 3000-3010
```

---

# 68. Database Connectivity

PostgreSQL:

```bash
psql -h localhost -U postgres
psql -h localhost -U postgres -d mydb
```

MySQL:

```bash
mysql -u root -p
mysql -h db-server -u root -p
```

SQL Server:

```bash
sqlcmd -S server -U username -P password
```

---

# 69. PostgreSQL Service

```bash
systemctl status postgresql
sudo systemctl restart postgresql
sudo -u postgres psql
```

Inside PostgreSQL:

```sql
\l
\dt
\q
```

---

# 70. Check Large Files

```bash
sudo find / -type f -printf '%s %p\n' 2>/dev/null |
sort -nr |
head -20
```

Simpler:

```bash
sudo du -ah / | sort -rh | head -20
sudo du -ah /var | sort -rh | head -20
```

---

# 71. Check Large Directories

```bash
sudo du -xhd1 / | sort -h
sudo du -xhd1 /var | sort -h
sudo du -xhd1 /var/lib | sort -h
```

---

# 72. Check Deleted Files Still Using Disk

```bash
sudo lsof +L1
```

Useful when `df -h` shows a full disk but `du` does not explain the usage.

---

# 73. Linux Logs

Common log locations:

```text
/var/log/syslog
/var/log/messages
/var/log/auth.log
/var/log/nginx/
```

View live:

```bash
tail -f /var/log/syslog
```

---

# 74. Last Login

```bash
last
sudo lastb
who
grep sshd /var/log/auth.log
```

---

# 75. Linux Security Commands

```bash
systemctl status ssh
systemctl status sshd
sudo ss -tulpn
cat /etc/passwd
getent group sudo
getent group wheel
```

---

# 76. `systemctl` Troubleshooting Pattern

```bash
systemctl status myapp
journalctl -u myapp -n 100
journalctl -u myapp -f
sudo systemctl restart myapp
systemctl status myapp
```

---

# 77. Deployment Troubleshooting Pattern

```bash
cd /var/www/app
git status
git pull
npm install
npm run build
pm2 restart api
pm2 logs api
ss -tulpn | grep 3000
curl http://localhost:3000
sudo nginx -t
sudo systemctl reload nginx
```

---

# 78. Useful Keyboard Shortcuts

| Shortcut | Purpose |
|---|---|
| `Ctrl + C` | Stop current command |
| `Ctrl + Z` | Suspend process |
| `Ctrl + D` | Exit shell/input |
| `Ctrl + L` | Clear terminal |
| `Ctrl + A` | Beginning of line |
| `Ctrl + E` | End of line |
| `Ctrl + U` | Delete before cursor |
| `Ctrl + K` | Delete after cursor |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete |
| `↑` | Previous command |
| `↓` | Next command |

---

# 79. Special Linux Paths

| Directory | Purpose |
|---|---|
| `/` | Root |
| `/home` | User home directories |
| `/root` | Root user's home |
| `/etc` | Configuration |
| `/var` | Logs, application data |
| `/var/log` | Logs |
| `/var/www` | Common web application location |
| `/opt` | Optional applications |
| `/usr` | Installed applications/libraries |
| `/bin` | Essential commands |
| `/sbin` | Administration commands |
| `/tmp` | Temporary files |
| `/dev` | Devices |
| `/proc` | Process/kernel information |
| `/sys` | Kernel/device information |
| `/mnt` | Temporary mounts |
| `/media` | Removable media |

---

# 80. Commands to Memorize First

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
htop
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
tar
systemctl
journalctl
apt
git
docker
docker compose
pm2
nginx -t
openssl
crontab
```

---

# 81. Essential Server Troubleshooting Commands

```bash
# CPU/processes
top

# RAM
free -h

# Disk
df -h

# Directory size
du -sh *

# Running services
systemctl --type=service --state=running

# Service logs
journalctl -u SERVICE -f

# Listening ports
sudo ss -tulpn

# Find process using a port
sudo lsof -i :PORT

# Test API/web server
curl -v http://localhost:PORT

# Search logs
grep -i "error" application.log
```

Typical server investigation:

```bash
uptime
free -h
df -h
top
sudo ss -tulpn
systemctl status nginx
sudo nginx -t
tail -100 /var/log/nginx/error.log
curl -I https://your-domain.com
journalctl -u nginx -n 100
```

---

# Final Notes

This reference covers the commands most commonly used for:

- Linux server administration
- File and directory management
- User and permission management
- Networking and DNS
- Port and process troubleshooting
- Nginx and Apache
- SSL/TLS
- SSH and SCP
- Git
- Node.js
- PM2
- Docker and Docker Compose
- PostgreSQL, MySQL, and SQL Server connectivity
- System monitoring
- Log investigation
- Disk-space troubleshooting
- Bash scripting
- Cron jobs
- DevOps deployment troubleshooting

Keep this Markdown file as a quick reference while working on Linux servers.
