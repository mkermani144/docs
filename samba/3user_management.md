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
samba-tool domain passwordsettings set --min-pwd-length=0
```


Adding users
----
There are two methods of adding users in the directory: via __Active Directory Users and Computers__ or via __cli__.

#### Adding users via Active Directory Users and Computers
1. Open Active Directory Users and Computers.
2. Right click on the container you want to add users in (e.g. students) and under __new__ click __User__.
3. Fill in the input fields and click __Next__.
4. Choose a password for user, check/uncheck the checkboxes if needed and click __Next__.
5. Click __Finish__.
You will see the user is added in specified container.

__This method is useful if you want to create a small number of users.__

#### Adding users via cli
In this method, `samba-tool` is used to create users:
```bash
samba-tool user create <username> <password> --given-name=<first-name> \
           --surname=<last-name> --userou=<OU dn> --use-username-as-cn
```
There are a lot of more options other than `given-name`, `surname`, `userou` and `use-username-as-cn`. For example, the `uid` option can be useful in assigning quotas to the users.

An example of the command would be:
```bash
samba-tool user create FooBar123 **321raBooF --given-name="Foo" \
           --surname="Bar" --userou="ou=boys, ou=students" --use-username-as-cn
```
Which creates a user in boys OU under students ou with FooBar123 as username and cn, Foo as firstname and Bar as lastname.

__This method is useful if you want to create a bunch of thousands of users. For instanse, you can easily make a script that contains thousands of lines like above command and each line belongs to creating one user.__


Resources
----
https://lists.samba.org/archive/samba/2013-August/174949.html
