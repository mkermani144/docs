Making a windows host member of a domain
====


#### Preconditions
* Host OS: Windows 7
* Samba version: 4.4.5
* samba domain: department.net
* server IP address: 192.168.89.180


Configuring dns
----
You should use samba server ip address as DNS for your windows host. In order to do so:

1. In taskbar's system tray, right click on networks icon and click __Open Network and Sharing Center__.
2. In the left hand of the page, click __Change adapter settings__.
3. Right click on your network adapter and click __Properties__.
4. Double click __Internet Protocol Version 4__.
5. Enter ip address of samba server in __Preferred DNS server__ in bottom of the page and click __OK__.


Joining host to the domain
----

1. Go to start menu, right click on __Computer__ and select __Properties__.
2. Click __Change settings__ in _Computer name, domain and workgroup_ section.
3. In _Computer Name_ tab (the default you'll see), click __Change__ button.
4. Switch from Workgroup to Domain and typein your domain name (e.g. department.net).
5. Click __OK__.
6. Unless something is wrong in your server, you should see a page asking for a name and password. Enter administrator as name and your admin password (the one you chose in provisioning samba) as the password and click OK.
7. You should see welcome message. Click OK and __restart your system__. The host will be member of the domain afterwards.


Resources
----
[samba website](http://www.sambe.org)
