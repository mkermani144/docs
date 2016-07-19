Managing users in samba 4 ADDC
====


#### Preconditions
* Samba version: 4.4.5
* Host OS: Windows 7
* Domain name: department.net
* An installed Microsoft RSAT program on windows host


Adding Organizational units
----
It is suggested that you create some organizational units (OUs) and add users in the OUs instead of adding users at the base of directory tree. OUs are made available to contain other type of resources, such as users, groups, printers, etc. In addition, OUs can be nested.

In order to add an OU:

1. Search for __Active directory Users and Computers__ in start menu and open it.
2. Supposing you want to create an OU as a direct child of your domain in directory tree, rigth click on your domain in the directory tree you see (e.g. department.iut) and under __new__ click __Organizational Unit__. 
3. Choose a name for OU. In addition, it is recommended to __uncheck__ "Protect container from accidental deletion".
4. Click OK.
You will see OU in the directory tree.


Removing password complexity requirements (Optional)
----
There are some password complexity requirements such as length and expiration time of the password. You can disable these complexity requirements. To do so:
```bash
samba-tool domain passwordsettings set --complexity=off
samba-tool domain passwordsettings set --history-length=0
samba-tool domain passwordsettings set --min-pwd-age=0
samba-tool domain passwordsettings set --max-pwd-age=0
samba-tool domain passwordsettings set --max-pwd-length=0
```
