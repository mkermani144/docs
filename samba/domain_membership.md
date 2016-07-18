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
- In taskbar's system tray, right click on networks icon and click __Open Network and Sharing Center__.
- In the left hand of the page, click __Change adapter settings__.
- Right click on your network adapter and click __Properties__.
- Double click __Internet Protocol Version 4__.
- Enter ip address of samba server in __Preferred DNS server__ in bottom of the page and click __OK__.
