# Conntent
Linux Administration Notes
1. File Permissions & Ownership (chmod, chown)

Linux controls who can access files and directories through permissions and ownership.

Permission Types
Permission	Meaning	Value
r	Read	4
w	Write	2
x	Execute	1

Example:

-rw-r--r--
Owner: Read + Write
Group: Read
Others: Read
chmod (Change Permissions)

Grant permissions using numeric values:

chmod 755 script.sh
chmod 644 file.txt
chmod +x script.sh

Common Permissions:

Permission	Meaning
777	Full access for everyone
755	Owner full access, others read & execute
644	Owner read/write, others read only
chown (Change Ownership)

Change file owner:

sudo chown user file.txt

Change owner and group:

sudo chown user:group file.txt

Real-world use case:

sudo chown -R www-data:www-data /var/www/html

Used when configuring NGINX or Apache web servers.

2. Process Management (ps, top, kill, jobs)

Processes are running instances of programs.

View Running Processes
ps -ef

Shows all running processes.

Real-Time Monitoring
top

Displays:

CPU usage
Memory usage
Running processes

Enhanced version:

htop
Kill a Process
kill PID

Force kill:

kill -9 PID
Background Jobs

Run process in background:

sleep 100 &

View jobs:

jobs

Bring job to foreground:

fg
3. Disk Management (df, du, mount, fdisk)

Disk management helps monitor storage usage and manage disks.

Check Filesystem Usage
df -h

Shows:

Total disk size
Used space
Free space
Check Directory Size
du -sh /var/log

Find largest directories:

sudo du -sh /* | sort -hr
View Mounted Filesystems
mount
List Disks
lsblk

or

sudo fdisk -l
Create Partition
sudo fdisk /dev/sdb

Used when attaching new storage volumes.

4. Networking Commands (ifconfig, netstat, ping, curl, wget)

Networking commands help troubleshoot connectivity issues.

View Network Configuration
ifconfig

Modern alternative:

ip addr
Check Open Ports
netstat -tulnp

Modern alternative:

ss -tulnp
Test Connectivity
ping google.com

Test DNS:

ping 8.8.8.8
Test Websites and APIs
curl https://google.com

Check headers:

curl -I https://google.com
Download Files
wget https://example.com/file.zip
5. Cron Jobs & Task Scheduling

Cron automates recurring tasks.

View Existing Cron Jobs
crontab -l
Create Cron Job
crontab -e

Example:

* * * * * echo "Hello" >> /tmp/test.log

Runs every minute.

Cron Format
* * * * *
│ │ │ │ │
│ │ │ │ └ Day of Week
│ │ │ └ Month
│ │ └ Day
│ └ Hour
└ Minute

Real-world use cases:

Backups
Log cleanup
Health checks
Monitoring scripts
6. Log Management & Monitoring (/var/log)

Logs help troubleshoot applications and servers.

Common Log Files
/var/log/syslog
/var/log/auth.log
/var/log/kern.log
View Logs
cat /var/log/syslog
Monitor Logs in Real Time
tail -f /var/log/syslog
Search Logs
grep error /var/log/syslog

Real-world use cases:

Login failures
Application crashes
Service restarts
7. Shell Environment & Environment Variables

Environment variables store configuration values used by applications.

View Variables
env

or

printenv
Display Variable
echo $HOME
Create Variable
export PROJECT=devops
Permanent Variables

Edit:

vi ~/.bashrc

Add:

export PROJECT=devops

Apply changes:

source ~/.bashrc

Common Variables:

PATH
HOME
USER
JAVA_HOME
8. SSH Configuration & Key-Based Authentication

SSH provides secure remote access to Linux servers.

Connect to Server
ssh user@server-ip
Generate SSH Keys
ssh-keygen

Creates:

id_rsa
id_rsa.pub
Copy Public Key
ssh-copy-id user@server-ip
SSH Configuration File
/etc/ssh/sshd_config

Important Settings:

PermitRootLogin no
PasswordAuthentication no

Restart SSH:

sudo systemctl restart ssh

Benefits:

More secure than passwords
Prevents brute-force attacks
9. Firewalls & iptables Basics

Firewalls control network access to servers.

UFW (Ubuntu Firewall)

Check status:

sudo ufw status

Allow SSH:

sudo ufw allow 22

Allow HTTP:

sudo ufw allow 80

Enable Firewall:

sudo ufw enable
iptables

View rules:

sudo iptables -L

Block a port:

sudo iptables -A INPUT -p tcp --dport 8080 -j DROP

Use cases:

Restrict access
Block unwanted traffic
Secure servers
10. systemd & Service Management

systemd manages Linux services.

Check Service Status
sudo systemctl status ssh
Start Service
sudo systemctl start nginx
Stop Service
sudo systemctl stop nginx
Restart Service
sudo systemctl restart nginx
Enable Service at Boot
sudo systemctl enable nginx
List Running Services
systemctl list-units --type=service

Common Services:

ssh
nginx
apache2
docker
11. Performance Tuning & Troubleshooting

Performance tuning ensures servers run efficiently.

CPU Monitoring
top

or

htop
Memory Usage
free -h
Disk Usage
df -h
Running Processes
ps -ef
Open Network Connections
ss -tulnp
Troubleshooting Workflow
top
free -h
df -h
systemctl status service-name
tail -f /var/log/syslog

Common issues:

High CPU
Memory exhaustion
Disk full
Service failure
12. Linux Security Hardening Basics

Security hardening reduces attack surfaces on Linux servers.

Disable Root Login

Edit:

sudo vi /etc/ssh/sshd_config

Set:

PermitRootLogin no
Disable Password Authentication
PasswordAuthentication no

Use SSH keys instead.

Keep System Updated
sudo apt update
sudo apt upgrade -y
Remove Unused Packages
sudo apt autoremove
Check Open Ports
sudo ss -tulnp
Monitor Failed Logins
sudo grep "Failed password" /var/log/auth.log
Principle of Least Privilege
Use regular users
Grant sudo only when required
Avoid running applications as root
Quick Revision Commands
# Permissions
chmod 755 file
chown user:group file

# Processes
ps -ef
top
kill -9 PID

# Disk
df -h
du -sh
mount
fdisk -l

# Networking
ifconfig
ping google.com
curl URL
wget URL

# Cron
crontab -e

# Logs
tail -f /var/log/syslog

# Environment Variables
env
export VAR=value

# SSH
ssh-keygen
ssh-copy-id

# Firewall
ufw status
iptables -L

# Services
systemctl status nginx

# Performance
top
free -h
df -h

# Security
ss -tulnp
grep "Failed password" /var/log/auth.log
