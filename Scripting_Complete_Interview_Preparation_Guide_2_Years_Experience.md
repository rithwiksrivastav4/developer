# Scripting Complete Interview Preparation Guide (2 Years Experience)

## 1. What is Scripting?

Scripting is the process of writing programs that automate repetitive
tasks.

Common scripting languages:

-   Bash/Shell
-   Python
-   PowerShell
-   JavaScript

Common uses:

-   Server automation
-   Deployment automation
-   Backup automation
-   Log processing
-   Monitoring
-   CI/CD automation

------------------------------------------------------------------------

# 2. Bash Shell Scripting

## Hello World

``` bash
#!/bin/bash

echo "Hello World"
```

## Variables

``` bash
#!/bin/bash

NAME="John"

echo "Hello $NAME"
```

## User Input

``` bash
#!/bin/bash

read -p "Enter name: " NAME

echo "Welcome $NAME"
```

## If Else

``` bash
#!/bin/bash

AGE=20

if [ $AGE -ge 18 ]
then
 echo "Adult"
else
 echo "Minor"
fi
```

## For Loop

``` bash
for i in 1 2 3 4 5
do
 echo $i
done
```

## While Loop

``` bash
count=1

while [ $count -le 5 ]
do
 echo $count
 count=$((count+1))
done
```

## Functions

``` bash
backup(){

 echo "Backup started"

}

backup
```

------------------------------------------------------------------------

# 3. Important Linux Commands

``` bash
ls
cd
pwd
mkdir
touch
cp
mv
rm
cat
grep
find
awk
sed
chmod
chown
ps
top
kill
curl
wget
ssh
scp
tar
zip
unzip
```

------------------------------------------------------------------------

# 4. Advanced Shell Scripting

Important concepts:

-   Exit codes
-   Error handling
-   Logging
-   Debugging
-   Signals
-   Environment variables
-   Arguments

## Script Arguments

``` bash
echo $1
echo $2
echo $@
```

## Check Exit Status

``` bash
echo $?
```

## Debug Script

``` bash
bash -x script.sh
```

------------------------------------------------------------------------

# 5. Automation Examples

## Disk Monitoring

``` bash
#!/bin/bash

usage=$(df -h / | awk 'NR==2 {print $5}')

echo "Disk Usage: $usage"
```

## Backup Script

``` bash
#!/bin/bash

tar -czf backup.tar.gz /var/www
```

## Log Cleanup

``` bash
find /var/log -type f -mtime +30 -delete
```

------------------------------------------------------------------------

# 6. Cron Jobs

Cron is used to schedule scripts.

Example: Run backup every day at midnight:

``` bash
0 0 * * * /home/user/backup.sh
```

Format:

    minute hour day month weekday

------------------------------------------------------------------------

# 7. Python Scripting

## File Processing

``` python
import os

files = os.listdir(".")

for file in files:
    print(file)
```

## API Automation

``` python
import requests

response = requests.get(
    "https://api.example.com/users"
)

print(response.json())
```

## Execute Commands

``` python
import subprocess

result = subprocess.run(
    ["ls"],
    capture_output=True
)

print(result.stdout)
```

------------------------------------------------------------------------

# 8. File Processing

## CSV Processing

``` python
import csv

with open("users.csv") as file:

    reader = csv.reader(file)

    for row in reader:
        print(row)
```

------------------------------------------------------------------------

# 9. Networking Scripts

Common tasks:

-   Ping monitoring
-   Port checking
-   API testing
-   Server health checks

Example:

``` bash
ping google.com
```

------------------------------------------------------------------------

# 10. DevOps Automation Scripts

Common automation:

-   Deployment scripts
-   Docker automation
-   Kubernetes automation
-   Database backups
-   Server monitoring
-   Log analysis

Docker example:

``` bash
docker build -t app .

docker run app
```

Kubernetes example:

``` bash
kubectl apply -f deployment.yaml
```

------------------------------------------------------------------------

# 11. Scripting Interview Questions

## Q1. What is scripting?

Answer:

Scripting is writing programs to automate tasks without manual
execution.

------------------------------------------------------------------------

## Q2. Difference between scripting and programming?

Scripting: - Usually used for automation - Interpreted execution

Programming: - Used for building complete applications

------------------------------------------------------------------------

## Q3. Difference between \$\* and \$@ in Bash?

\$\*: - Treats all arguments as one string

\$@: - Treats arguments separately

------------------------------------------------------------------------

## Q4. How do you debug shell scripts?

Commands:

``` bash
bash -x script.sh
```

Use:

-   Logs
-   Echo statements
-   Exit codes

------------------------------------------------------------------------

## Q5. How do you schedule scripts?

Using cron jobs.

Example:

``` bash
crontab -e
```

------------------------------------------------------------------------

## Q6. Production disk is full. How will you debug?

Commands:

``` bash
df -h

du -sh *

find /var/log -size +500M
```

------------------------------------------------------------------------

## Q7. Deployment script failed. What will you check?

Check:

-   Script logs
-   Exit status
-   Permissions
-   Environment variables
-   Server connectivity

------------------------------------------------------------------------

## Q8. How do you automate API calls?

Using:

Python:

-   requests library

Bash:

-   curl command

Example:

``` bash
curl https://api.example.com/users
```

------------------------------------------------------------------------

# 12. Scripting Best Practices

-   Add proper logging
-   Handle errors
-   Validate inputs
-   Use meaningful variable names
-   Avoid hardcoded secrets
-   Use environment variables
-   Test scripts before production

------------------------------------------------------------------------

# Command Cheat Sheet

``` bash
chmod
chown
grep
awk
sed
find
curl
ssh
scp
tar
cron
systemctl
journalctl
docker
kubectl
git
```

------------------------------------------------------------------------

# 2 Years Experience Checklist

Must know:

-   Bash scripting
-   Python scripting
-   Linux commands
-   Cron jobs
-   File processing
-   API automation
-   Error handling
-   Logging
-   DevOps automation
-   Docker scripting
-   Kubernetes scripting
-   Production troubleshooting
