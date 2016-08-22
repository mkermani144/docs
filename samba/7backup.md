Assigning quotas to samba 4 users
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba installation type: building from source
* Installed packages (via `yum`): `bzip2`
* __Two servers with samba domain provisioned, same ip address, hostname, domain and local sid.__


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
