Assigning quotas to samba 4 users
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba installation type: building from source
* Installed packages (via `yum`): `quota`
* Samba share hard drive mount point: /hard


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


Assigning quotas to users
----
Assinging quotas to users is very easy:
1. First, add `usrquota` and `grpquota` in your `fstab` file:

 ```
 /root/hard.ext4		/hard			ext4	defaults,usrquota,grpquota,barrier=1	0 0
 ```
2. Run `quotacheck` on your hard mount point:

 ```
 quotacheck -cug /hard
 ```
This will create two files, `aquota.user` and `aquota.group`, in your hard mount point.
3. Assign quotas to the users:
 ```
 setquota <uid> <soft-limit> <hard-limit> 0 0 <mnt-pnt>
 ```
 For example, you can give `FooBar123` 10M of quota by running the following command:
 ```
 setquota 3000012 10M 10M 0 0 /hard
 ```
(You can get more info about soft and hard limits in resource pages.)
4. Enable quotas:
 ```
 quotaon -av
 ```
5. You can run `repquota -a` to get a report about assigned quotas.



Resources
----
https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-disk-quotas.html

http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html
