# Linux for Blue Team

## 1. Why Linux Matters in Blue Team
Linux is important in cybersecurity because many servers, security tools, cloud systems, and applications run on Linux. Blue Team analysts often need Linux knowledge to:
- investigate suspicious activity
- check logs
- review processes
- inspect files and permissions
- use command-line tools
- understand server behavior

Even if your main role is SOC analysis, Linux basics are extremely useful.

---

## 2. What is Linux?
Linux is an operating system, similar to Windows, but widely used for:
- servers
- cloud systems
- security tools
- development environments
- cybersecurity labs

Examples of Linux distributions:
- Ubuntu
- Kali Linux
- Debian
- CentOS
- Fedora

For Blue Team learning, **Ubuntu** is a good starting choice.

---

## 3. Why Blue Team Uses Linux
Blue Team may work with:
- Linux servers
- web servers
- SIEM servers
- cloud machines
- security tools running on Linux
- log files stored on Linux systems

Linux is also useful for practicing commands, reading logs, and understanding system activity.

---

## 4. Linux File System Basics
Linux organizes files in a tree-like structure starting from the root directory:

```bash
/
Some important directories:
  Directory    | Purpose                     
  `/`          | Root directory              
  `/home`      | User home directories       
  `/etc`       | Configuration files        
  `/var`       | Logs, variable data         
  `/var/log`   | System and application logs 
  `/bin`       | Essential commands          
  `/usr`       | Programs and utilities      
  `/tmp`       | Temporary files             
Important for Blue Team
The most important one for beginners is:

/var/log
because many logs are stored there.

5. Basic Linux Commands
pwd
Shows the current working directory.

Example:

pwd
ls
Lists files and folders in the current directory.

Example:

ls
ls -l
ls -la
ls -l → detailed list

ls -la → shows hidden files too

cd
Changes directory.

Example:

cd /var/log
cd ..
cd ~
cd .. → go one folder back

cd ~ → go to home directory

mkdir
Creates a new directory.

Example:

mkdir blue-team-notes
touch
Creates an empty file.

Example:

touch notes.txt
cp
Copies files or folders.

Example:

cp file1.txt file2.txt
mv
Moves or renames files.

Example:

mv old.txt new.txt
rm
Deletes files.

Example:

rm file.txt
Warning
Be careful with rm because deleted files are not easily recovered.

6. Viewing File Content
cat
Displays file content directly in the terminal.

Example:

cat auth.log
less
Lets you scroll through file content page by page.

Example:

less auth.log
This is better for large log files.

head
Shows the first lines of a file.

Example:

head auth.log
tail
Shows the last lines of a file.

Example:

tail auth.log
Useful option
tail -f auth.log
-f means “follow” the file in real time, useful when monitoring logs.

7. Searching in Files
grep
Searches for specific text in files.

Example:

grep "Failed password" auth.log
This is very useful in Blue Team for finding:

failed logins

suspicious usernames

IP addresses

error messages

attack indicators

8. File Permissions in Linux
Linux files have permissions that control who can:

read

write

execute

You may see something like:

-rw-r--r--
Permission meaning
r = read

w = write

x = execute

Three permission groups
Owner

Group

Others

9. chmod
Changes file permissions.

Example:

chmod 644 notes.txt
chmod +x script.sh
Why it matters in Blue Team
Blue Team analysts may investigate:

unauthorized permission changes

suspicious executable files

scripts made executable by attackers

10. Processes in Linux
A process is a running program or command.

Blue Team analysts may check processes to find:

suspicious commands

malware activity

unknown scripts

high resource usage

11. ps
Shows running processes.

Example:

ps
ps aux
ps aux
Shows a detailed list of processes, including:

user

process ID

CPU usage

memory usage

command

12. top
Shows running processes in real time.

Example:

top
Useful for identifying:

high CPU usage

suspicious long-running processes

system load

13. Network-Related Commands
netstat
Shows network connections, listening ports, and other networking information.

Example:

netstat -tulnp
This can help identify:

open ports

services listening on the system

suspicious connections

ss
Modern alternative to netstat.

Example:

ss -tulnp
Also used to view:

active connections

listening ports

processes using network sockets

14. User Identity Commands
whoami
Shows the current logged-in user.

Example:

whoami
id
Shows user ID and group information.

Example:

id
15. Disk and File Usage
df -h
Shows disk usage.

Example:

df -h
Useful for checking whether a system is full or if unusual storage usage exists.

du -sh
Shows the size of a file or directory.

Example:

du -sh /var/log
16. Linux Logs Important for Blue Team
Logs are one of the most important parts of Blue Team work.

Common log locations
/var/log/auth.log → authentication events on many Debian/Ubuntu systems

/var/log/syslog → general system logs

/var/log/kern.log → kernel-related logs

/var/log/apache2/ → Apache web server logs (if installed)

What Blue Team checks in logs
failed login attempts

sudo usage

service failures

suspicious commands

repeated errors

unknown IP addresses

17. Example: Failed Login Detection
A common Blue Team task is checking for failed login attempts.

Example:

grep "Failed password" /var/log/auth.log
This may help detect:

brute-force attacks

login attempts to disabled accounts

suspicious SSH access attempts

18. Example: Checking Successful Logins
Depending on system logs, you may look for accepted logins:

grep "Accepted password" /var/log/auth.log
This helps identify:

which user logged in

from which IP address

at what time

19. Why /var/log is Important
The /var/log directory contains many system and application logs. It is one of the first places Blue Team analysts may check during investigations.

Examples of useful information in logs:

login activity

service crashes

software errors

suspicious commands

security alerts

20. Linux Security-Relevant Things to Watch
Suspicious login attempts
Repeated failed SSH logins can indicate brute-force attacks.

Unknown users or new accounts
Unexpected user creation can be suspicious.

Strange processes
Unknown processes or scripts may indicate malware or abuse.

Unexpected open ports
If a system suddenly listens on a new port, that may require investigation.

Unauthorized permission changes
An attacker may change file permissions to run scripts or hide files.

21. Common Beginner Mistakes in Linux
Using rm carelessly

Not checking the current directory before deleting files

Confusing file permissions

Ignoring logs

Not using grep to search logs efficiently

22. Linux Skills Blue Team Beginners Should Build
Navigate directories

View files and logs

Search logs with grep

Understand basic permissions

Check running processes

Check open ports and connections

Read authentication logs

Use tail -f to monitor logs live

23. Quick Revision Notes
Linux is widely used in servers and security environments

/var/log is a very important directory for Blue Team

ls, cd, pwd, cat, less, tail, and grep are essential commands

grep is very useful for searching logs

ps aux shows running processes

ss -tulnp or netstat -tulnp shows listening ports and connections

chmod changes permissions

auth.log often contains login-related events

Failed SSH logins may indicate brute-force attempts

24. Interview / Viva Questions
Why is Linux important in Blue Team?

What is the purpose of /var/log?

Which command is used to search for text inside a log file?

What does tail -f do?

What is the difference between cat and less?

What does ps aux show?

What is the purpose of chmod?

Which Linux log file often contains authentication events?

Why are failed SSH login attempts important?

Which command can show open ports and active network connections?

25. Short Summary
Linux is a very important skill for Blue Team because many servers and security tools run on Linux. Blue Team analysts use Linux to navigate systems, read logs, search for suspicious events, inspect processes, and review network activity. Learning commands like ls, cd, cat, grep, tail, ps, and ss gives a strong foundation for security monitoring and investigations.
