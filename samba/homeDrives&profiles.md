Adding user home drives and profiles
====


Preconditions
----
* Samba version: 4.4.5
* Hard drive filesystem path: `/root/hard.ext4`
* Hard drive filesystem type: `ext4`
* Home drives container directory path: `/hard`
* Share name: home
* Server host name: dept


Making a virtual filesystem for tests (Optional)
----
If you are starting a test server and don't have a real hard drive, you can easily make a virtual filesystem for your test:
```bash
dd if=/dev/zero of=/root/hard.ext4 bs=512 count=204800 # Make a file of size 100Mb to be our filesystem
mkfs -t ext4 -q /root/hard.ext4 -F # Make ext4 filesystem
```


Automounting using `fstab`
----
You should add your filesystem to your `fstab` so that it is mounted on boot. To do so, add the following line to your `/etc/fstab`:
```fstab
/root/hard.ext4    /hard    ext4    defaults,barrier=1    0 0
```
_Note: If you are using another type of filesystem other than `ext4`, samba recommends that you add other options to your `fstab` file. See the documentation for more details._


Adding share
----
Add the following lines to your `/usr/local/samba/etc/smb.conf`:
```bash
[home] # Note: Don't use homes as the name of share.
	path = /hard/
	read only = No
```
In one of your domain member machines, open `Run` and typein the server IP address or host name (e.g. department.net). You should see a folder named home.


Setting share and filesystem permissions
----
1. Right click on Computer in start menu and select __Manage__.
2. Right click on __Computer Management (Local)__ (The base of the tree on left) and select __Connect to another computer ...__.
3. Typein IP address or host name of the server. (e.g. dept)
4. Select __System Tools__ in the tree on left, then double click on __Shared Folders__ on right.
5. Double click on __Shares__.
6. Right click on your share (e.g. home) and select __Properties__.
7. Go to __Share Permissions__ tab.
8. Change share permissions to:

 Object | Permission to allow
 ------ | :----------:
 Authenticated Users | Full Control
 Domain Admins | Full Control
 SYSTEM | Full Controll
9. Go to __Security__ tab.
10. Click __Advanced__, then click __Change Permissions__ and finally uncheck "Include ingeritable permissions from the object's parent" option. Click OK.
11. In security tab, click __Edit__ and change permissions to following:

 Object | Permissions to allow
 ------ | :--------------:
 Administraotr | Full Control
 Authenticated Users | Read & Execute, List Folder Contents, Read
 CREATOR OWNER | Full Control
 Domain Admins | Full Control
 System | Full Control
12. Click __Advanced__, then click __Change Permissions__.
13. Select "Authenticated Users" and click __Edit__.
14. Change "Apply to" value to __This folder only__.
15. Close all windows with OK.


Assigning users home folders and home drives
----
1. Open Active Directory Users and Computers.
2. Select the users you want to assign home drives, right click on them and select __Properties__.
3. Switch to __profile__ tab. 
4. Switch from Local path to __Connect__ in "Home folder" section and typein the path to the home drive followed by __%username%__. For example, `\\dept\home\%username%`.
5. Click OK.
You should now see the home folder is created under the share folder. In addition, when a user logins, the home drive should be added.


Resources
----
[Samba website](http://www.samba.org)
