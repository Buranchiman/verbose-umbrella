# verbose-umbrella
Tips and commands for b2br

Q: Why Debian?
A: It's easier to install and configure than CentOS (and i haven't use CentOS befoe)

Q: What is virtual machine?
A: A Virtual Machine (VM) is a compute resource that uses software instead of a physical computer to run programs and deploy 
apps. Each virtual machine runs its own operating system and functions separately from the other VMs, even when they are all
running on the same host. For example, you can run a virtual MacOS machine on a physical PC. 

Q: What it's purpose?
A: VMs may be deployed to accommodate different levels of processing power needs, to run software that requires a different
operating system, or to test applications in a safe, sandboxed environment. 

Q: How does it works?
A: VM working through "Virtualization" technology. Virtualization uses software to simulate virtual hardware that allows 
VMs to run on a single host machine.

Q: Diff between aptitude and apt?
A: Aptitude is a high-level package manager while APT is lower-level package manager which can be used by other 
higher-level package managers
(read more: https://www.tecmint.com/difference-between-apt-and-aptitude/)

Q: What is AppArmor?
A: AppArmor ("Application Armor") is a Linux kernel security module that allows the system administrator to restrict programs'
capabilities with per-program profiles.
(read more: https://en.wikipedia.org/wiki/AppArmor)


5) sudo service ssh status            5 <- ssh status, yep
6) sudo ufw status                    6 <- ufw status

3) getent group sudo                  3 <- sudo group users
4) getent group user42                4 <- user42 group users

/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
| You have to create a new user here.        |
| $ sudo adduser username                    | <- creating new user (yes (no))
| $ sudo chage -l username                   | <- Verify password expire info for new user
| $ sudo adduser username sudo               |
| $ sudo adduser username user42             | <- assign new user to sudo and user42 groups
\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/


Check password policy :
 9) vim /etc/login.defs               9 <- password expire policy
 10) vim /etc/pam.d/common-password  10 <- password policy

create group : sudo groupadd groupname
delete group : sudo groupdel groupname

How to change hostname?
[$sudo vim /etc/hostname]

Display partition : lsblk

11.1. What is LVM?
LVM is a tool for logical volume management which includes allocating disks, striping, mirroring and resizing logical volumes.
With LVM, a hard drive or set of hard drives is allocated to one or more physical volumes. LVM physical volumes can be placed on other block devices which might span two or more disks.
The physical volumes are combined into logical volumes, with the exception of the /boot partition. The /boot partition cannot be on a logical volume group because the boot loader cannot read it. If the root (/) partition is on a logical volume, create a separate /boot partition which is not a part of a volume group

Figure 11.1. Logical Volumes

The volume groups can be divided into logical volumes, which are assigned mount points, such as /home and / and file system types, such as ext2 or ext3. When "partitions" reach their full capacity, free space from the volume group can be added to the logical volume to increase the size of the partition. When a new hard drive is added to the system, it can be added to the volume group, and partitions that are logical volumes can be increased in size.

Uncomplicated Firewall (UFW) is a program for managing a netfilter firewall designed to be easy to use.
How to add and remove port 8080 in UFW?
[$ sudo ufw allow 8080] <- allow
[$ sudo ufw status] <- check
[$ sudo ufw deny 8080] <- deny (yes yes)

check the crontab : sudo crontab -e
How to run script every 30 seconds?
[$ sudo crontab -e]
Remove or commit previous cron "schedule" and add next lines in crontab file
|*************************************************|
| */1 * * * * /path/to/monitoring.sh              |
| */1 * * * * sleep 30s && /path/to/monitoring.sh |
|*************************************************|
To stop script running on boot you just need to remove or commit
|********************************|
| @reboot /path/to/monitoring.sh |
|********************************|
line in crontab file.
