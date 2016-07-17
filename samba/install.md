Installing samba 4
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba tarball path: /root/samba


Downloading samba
----
You can download latest stable release of samba (currently 4.4.5) from [samba website](https://www.samba.org/).


Installing dependencies
----
Install all of the dependencies via the following command:
```
yum install perl gcc attr libacl-devel libblkid-devel \
gnutls-devel readline-devel python-devel gdb pkgconfig \
krb5-workstation zlib-devel setroubleshoot-server libaio-devel \
setroubleshoot-plugins policycoreutils-python \
libsemanage-python perl-ExtUtils-MakeMaker perl-Parse-Yapp \
perl-Test-Base popt-devel libxml2-devel libattr-devel \
keyutils-libs-devel cups-devel bind-utils libxslt \
docbook-style-xsl openldap-devel autoconf python-crypto pam-devel
```


Installing samba
----
```
cd /root/samba
tar -zxf samba-4.4.5.tar.gz
cd samba-4.4.5
./configure.developer
make
make install
```
Samba is located under `/usr/local/samba`.


Additional jobs
----

#### Updating `PATH`
```
echo 'export PATH=$PATH:/usr/local/samba/bin:/usr/local/samba/sbin' >> /etc/profile
```

#### Making init script for samba
Put the following lines into `/etc/rc.d/init.d/samba4`. You can choose a name other than `samba4`.
```bash
#! /bin/bash
#
# samba4 Bring up/down samba4 service
#
# chkconfig: - 90 10
# description: Activates/Deactivates all samba4 interfaces configured to \
# start at boot time.
#
### BEGIN INIT INFO
# Provides:
# Should-Start:
# Short-Description: Bring up/down samba4
# Description: Bring up/down samba4
### END INIT INFO
# Source function library.
. /etc/init.d/functions

if [ -f /etc/sysconfig/samba4 ]; then
. /etc/sysconfig/samba4
fi

CWD=$(pwd)
prog="samba4"

start() {
echo -n $"Starting $prog: "
/usr/local/samba/sbin/samba
sleep 2
if ps ax | grep -v "grep" | grep -q /samba/sbin/samba ; then success $"samba4 startup"; else failure $"samba4 startup"; fi
echo
}
stop() {
echo -n $"Shutting down $prog: "
killall samba
sleep 2
if ps ax | grep -v "grep" | grep -q /samba/sbin/samba ; then failure $"samba4 shutdown"; else success $"samba4 shutdown"; fi
echo
}
status() {
/usr/local/samba/sbin/samba --show-build
}

case "$1" in
start)
start
;;
stop)
stop
;;
status)
status irattach
;;
restart|reload)
stop
start
;;
*)
echo $"Usage: $0 {start|stop|restart|status}"
exit 1
esac

exit 0
```
Then run following commands:
```bash
chmod 755 /etc/rc.d/init.d/samba4
ln -s /etc/rc.d/init.d/samba4 /etc/rc3.d/S80samba4
chkconfig --add samba4
chkconfig samba4 on
service samba4 restart
```

