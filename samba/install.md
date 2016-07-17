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
# yum install perl gcc attr libacl-devel libblkid-devel \
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
