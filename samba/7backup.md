Assigning quotas to samba 4 users
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba installation type: building from source
* Installed packages (via `yum`): `bzip2`
* __Two servers with samba domain provisioned, same ip address, hostname, domain sid and local sid.__


Copying and configuring `samba_backup` script
----
By default, `samba_backup` script is not included in samba installed scripts. You should copy it from samba source.
```bash
cp /root/samba-4.4.5/source4/scripting/bin/samba_backup /usr/local/samba/bin/
```
After that, set backup destination folder by changing `WHERE=` line in the script:
```bash
vim /usr/local/samba/bin/samba_backup
```
Change `WHERE=` line based on your choice:
```
WHERE=/root/backups
```
Finally make that directory:
```bash
mkdir /root/backups
```


Getting backups
----
```bash
samba_backup
```
It should run without any error and create three `.bz2` file in your `backups` directory:
```bash
etc.{Timestamp}.tar.bz2
samba4_private.{Timestamp}.tar.bz2
sysvol.{Timestamp}.tar.bz2
```


Restoring backups
----
__Important note: Take care about bolder precondition. The main server and backup server should be exactly the same in ip address, hostname, domain provisioning, domain sid and local sid.__

First, ship the backup files from the main server to the backup server. Then run the following commands:
```bash
rm -rf /usr/local/samba/etc
rm -rf /usr/local/samba/private
rm -rf /usr/local/samba/var/locks/sysvol
cd /root/backups # Supposing you have copied backup files to /root/backups
tar -jxf etc.{Timestamp}.tar.bz2 -C /usr/local/samba/
tar -jxf samba4_private.{Timestamp}.tar.bz2 -C /usr/local/samba/
tar -jxf sysvol.{Timestamp}.tar.bz2 -C /usr/local/samba/var/locks/
find /usr/local/samba/private/ -type f -name '*.ldb.bak' -print0 | while read -d $'\0' f ; do mv "$f" "${f%.bak}" ; done
```


To-do
----

- [ ] Support for extended attributes


Resources
----
[samba wiki](wiki.samba.org)
