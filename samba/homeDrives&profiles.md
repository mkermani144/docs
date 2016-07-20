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
