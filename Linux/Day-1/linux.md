# content

# Linux Basics Notes for DevOps Engineers

## 1. Introduction to Linux & Linux Distributions

Linux is an open-source operating system used to manage hardware and software resources. It is widely used in servers, cloud platforms, DevOps environments, and container technologies like Docker and Kubernetes.

Most web applications, cloud servers, and enterprise systems run on Linux because it is stable, secure, and free.

### Popular Linux Distributions

**Ubuntu**

* Beginner-friendly
* Uses APT package manager
* Common in cloud and DevOps environments

**CentOS**

* Enterprise-focused distribution
* Similar to Red Hat Enterprise Linux (RHEL)

**Rocky Linux**

* Replacement for CentOS
* Stable and enterprise-ready

**Red Hat Enterprise Linux (RHEL)**

* Commercial Linux distribution
* Widely used in enterprises

**Debian**

* Stable and reliable
* Base distribution for Ubuntu

### Why Linux is Important for DevOps

* Most cloud servers run Linux
* Docker containers use Linux
* Kubernetes nodes run Linux
* CI/CD pipelines often execute on Linux servers
* Automation scripts are usually written for Linux systems

---

# 2. Linux File System Hierarchy

Linux stores everything as files, including devices and directories.

### Important Directories

| Directory | Purpose                        |
| --------- | ------------------------------ |
| /         | Root directory                 |
| /home     | User home directories          |
| /root     | Home directory of root user    |
| /etc      | Configuration files            |
| /var      | Logs and variable data         |
| /tmp      | Temporary files                |
| /bin      | Essential user commands        |
| /sbin     | System administration commands |
| /usr      | User programs and utilities    |
| /opt      | Optional software packages     |
| /dev      | Device files                   |
| /proc     | Process information            |
| /mnt      | Temporary mount points         |

### Example

/home/azureuser/project/app.py

* home → user directory
* azureuser → username
* project → project folder
* app.py → file

---

# 3. Basic Linux Commands

### ls (List Files)

Show files and folders.

```bash
ls
```

Detailed output:

```bash
ls -l
```

Show hidden files:

```bash
ls -la
```

### cd (Change Directory)

Move between directories.

```bash
cd /home/azureuser
```

Go back one directory:

```bash
cd ..
```

Go to home directory:

```bash
cd ~
```

### mkdir (Create Directory)

```bash
mkdir project
```

Create multiple directories:

```bash
mkdir dev test prod
```

### cp (Copy Files)

```bash
cp file1.txt backup.txt
```

Copy directory:

```bash
cp -r project backup_project
```

### mv (Move/Rename Files)

Rename file:

```bash
mv old.txt new.txt
```

Move file:

```bash
mv file.txt /tmp
```

### rm (Remove Files)

Delete file:

```bash
rm file.txt
```

Delete directory:

```bash
rm -r project
```

Force delete:

```bash
rm -rf project
```

Be careful with rm -rf because it permanently deletes files.

---

# 4. File Permissions & Ownership

Linux uses permissions to control who can access files.

### Permission Types

* Read (r)
* Write (w)
* Execute (x)

Example:

```bash
ls -l
```

Output:

```bash
-rwxr-xr--
```

### Meaning

Owner:

```bash
rwx
```

Group:

```bash
r-x
```

Others:

```bash
r--
```

### chmod Command

Give execute permission:

```bash
chmod +x script.sh
```

Remove write permission:

```bash
chmod -w file.txt
```

Numeric Method:

```bash
chmod 755 script.sh
```

Meaning:

* 7 = rwx
* 5 = r-x
* 5 = r-x

### chown Command

Change ownership:

```bash
sudo chown azureuser file.txt
```

Change owner and group:

```bash
sudo chown azureuser:developers file.txt
```

---

# 5. Text Editors: vi and nano

Text editors are used to create and modify files.

## Nano Editor

Easy for beginners.

Create file:

```bash
nano test.txt
```

Useful Keys:

* Ctrl + O → Save
* Enter → Confirm
* Ctrl + X → Exit

## Vi/Vim Editor

Most commonly used in servers.

Open file:

```bash
vi test.txt
```

Modes:

### Insert Mode

Press:

```bash
i
```

Now start typing.

### Save and Exit

Press:

```bash
Esc
```

Then:

```bash
:wq
```

### Exit Without Saving

```bash
:q!
```

---

# 6. User & Group Management

Linux allows multiple users on a system.

### Create User

```bash
sudo useradd john
```

Create user with home directory:

```bash
sudo useradd -m john
```

Set password:

```bash
sudo passwd john
```

### View Users

```bash
cat /etc/passwd
```

### Delete User

```bash
sudo userdel john
```

Delete with home directory:

```bash
sudo userdel -r john
```

### Create Group

```bash
sudo groupadd developers
```

### Add User to Group

```bash
sudo usermod -aG developers john
```

### View Groups

```bash
groups john
```

Why groups are useful:

* Manage permissions easily
* Assign access to teams
* Improve security

---

# 7. Package Management

Package managers install and manage software.

## APT (Ubuntu/Debian)

Update package list:

```bash
sudo apt update
```

Upgrade packages:

```bash
sudo apt upgrade
```

Install package:

```bash
sudo apt install nginx
```

Remove package:

```bash
sudo apt remove nginx
```

## YUM (CentOS 7)

Install package:

```bash
sudo yum install nginx
```

Update packages:

```bash
sudo yum update
```

## DNF (Rocky Linux, Fedora, RHEL 8+)

Install package:

```bash
sudo dnf install nginx
```

Update packages:

```bash
sudo dnf update
```

---

# 8. Process Management

A process is a running program.

### View Running Processes

```bash
ps
```

Detailed process list:

```bash
ps -ef
```

### top Command

Monitor CPU and memory usage.

```bash
top
```

### Kill Process

Find process:

```bash
ps -ef
```

Kill process:

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

Example:

```bash
kill -9 1234
```

### Background Jobs

Run process in background:

```bash
sleep 100 &
```

View jobs:

```bash
jobs
```

Bring process to foreground:

```bash
fg
```

---

# 9. Disk Management

Disk management helps monitor storage usage.

### df Command

Show filesystem usage:

```bash
df -h
```

Example output:

```bash
Filesystem Size Used Avail Use%
```

### du Command

Check directory size:

```bash
du -sh /home
```

### mount Command

View mounted disks:

```bash
mount
```

Mount disk:

```bash
sudo mount /dev/sdb1 /mnt
```

### fdisk Command

View disk partitions:

```bash
sudo fdisk -l
```

Manage partitions:

```bash
sudo fdisk /dev/sdb
```

---

# Quick Revision

### File Commands

```bash
ls
cd
mkdir
cp
mv
rm
```

### Permissions

```bash
chmod
chown
```

### Editors

```bash
vi
nano
```

### User Management

```bash
useradd
usermod
groupadd
passwd
```

### Package Management

```bash
apt
yum
dnf
```

### Process Management

```bash
ps
top
kill
jobs
```

### Disk Management

```bash
df
du
mount
fdisk
```

