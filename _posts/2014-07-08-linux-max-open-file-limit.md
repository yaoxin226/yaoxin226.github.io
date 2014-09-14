---
layout: global
title: Max open file limit in ubuntu 10.04
---

# Max open file limit in linux

## System level

This only changes how many file can be open totally in this system. For each user, should addtional change user level settings.

### Change runtime

Change runtime open file max

    sysctl -w fs.file-max=10240

Check current max open file

    cat /proc/sys/fs/file-max

Or:

	sysctl fs.file-max

### Change for reboot

You need to put this in /etc/sysctl.conf so after reboot the setting will remain as it is

	vi /etc/sysctl.conf
	
Append

	fs.file-max=10240
	
Save and close file. User need to log out and log back in again to make the changes take effect. Or just type the following command:

	sysctl -p

## User level

We can change the limit for each user or group

THe above procedure sets system-wide open file limits. However, you can limit httped(or any other user or group) to specific limits by editing /etc/security/limit.conf:

	vi /etc/security/limits.conf

Set httpd user soft and hard limits as follows:

	httpd soft nofile 4096
	httpd hard nofile 10240

Save and close file. To see limits take effect, need to relogin, then enter:

	sudo su httpd
	ulimit -Hn # Hard limit
	ulimit -Sn # Soft limit


## Change all the user

    * soft nofile 50000
    * hard nofile 50000
    root soft nofile 50000
    root hard nofile 50000

Add * line for reguler users. For root, add two lines for it.

## Check limit of a running process

Find pid

	ps aux | grep process-name

Check limit

	cat /proc/<pid>/limits


## See more

[linux-increase-the-maximum-number-of-open-files](http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/)

[increase-open-files-limit/](https://rtcamp.com/tutorials/linux/increase-open-files-limit/)


