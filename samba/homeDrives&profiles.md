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
