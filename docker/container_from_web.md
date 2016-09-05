Accessing docker container from web
====


Preconditions
----
* OS: Ubuntu 14.04
* Docker version: 1.11.2
* Docker container IP address: 172.17.0.2


Pulling (unofficial) butterfly image
----
```bash
docker pull garland/butterfly
```


Starting butterfly
----
```bash
docker run -p 12345:12345 -it --rm garland/butterfly bash
# Notes:
# Expose your own favorite port
# Pass --rm only if you want to remove container after stop
butterfly.server.py --host=172.17.0.2 --port=12345 --unsecure
```
Then open your browser and open 172.17.0.2:12345. You will get into the container bash.


Todo
----
- [ ] Make connection secure
