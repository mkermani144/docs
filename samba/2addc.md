Setuping samba 4 as an active directory domain controller
====


#### Preconditions
* OS: Centos 7
* Samba version: 4.4.5
* Samba installation type: building from source
* hostname: dept
* samba realm: department.net
* samba domain: department
* server IP address: 192.168.89.180, static


Provisioning samba
----
It is recommended that you set an SID for your domain so that you can provision samba again without having to make windows hosts member of new samba domain.
```bash
samba-tool domain provision --use-rfc2307 --domain-sid=S-1-5-*-*-*-* --interactive
```
You will see the program asks you for realm, domain, etc.

__Special note: You cannot have the same name for your domain and your server host name. If you do so, you will get some errors.__
```
Realm: department.net
Domain [department]: # Enter
Server Role (dc, member, standalone) [dc]: # Enter
DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: [SAMBA_INTERNAL]: # Enter
DNS forwarder IP address (write 'none' to disable forwarding) [*.*.*.*]: # Enter
Administrator password: # Type in your password
Retype password: # Retype password
...
...
```
At the end, you should see something like this:
```
Server Role:           active directory domain controller
Hostname:              dept
NetBIOS Domain:        DEPARTMENT
DNS Domain:            department.net
DOMAIN SID:            S-1-5-*-*-*-*
```
Set local SID same as domain sid:
```
net setlocalsid S-1-5-*-*-*-*
```
Ensure that provisioning has been done successfully via the following command:
```bash
smbclient //localhost/netlogon -UAdministrator -c 'ls'
```
The command should return something like this:
```
Domain=[DEPARTMENT] OS=[Unix] Server=[Samba 4.4.5]
 .                                   D        0  Sat Jul  5 08:40:00 2016
 ..                                  D        0  Sat Jul  5 08:40:00 2016

               49386 blocks of size 524288. 42093 blocks available
```


Resources
----
[samba website](http://www.samba.org)

https://imanudin.net/2014/11/16/how-to-install-samba4-active-directory-on-centos-7-part-1/
