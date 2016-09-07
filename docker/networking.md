Docker networking
====


Creating new bridge network
----
```bash
docker network create \
   --subnet=192.168.0.0/24 \ # Or any other subnet
   --gateway=192.168.0.1 \ # Choose your favorite gateway
   -o "com.docker.network.bridge.name"="dockerInterface" # Network interface name
   network-name
```


Todo
----
- [ ] Docker network types
