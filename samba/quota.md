Assigning quotas to samba 4 users
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba installation type: building from source
* Installed packages (via `yum`): `quota`
* Samba share hard drive path: /hard



Finding UID of users
----
In order to add quotas for each user, you should first know his/her UID. You can define UID of users when you are creating users via `--uid-number=<uid>`. Otherwise, samba will assign the users a UID itself.

In order to find UID of a user, you can use `wbinfo`:
```bash
wbinfo -i <username>
```
For example, if you run `wbinfo -i FooBar123` you will see something like this:
```
DEPARTMENT\foobar123:*:3000012:100:Foo Bar:/home/DEPARTMENT/foobar123:/bin/false
```
`3000012` is UID of `FooBar123`.


Resources
----
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-disk-quotas.html

http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html
