# Creating a network with Subnet and Gateway
1. Create a bridge network with a subnet and gateway
```
docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 br02
```
2. list the docker network (optional).
```
docker network ls
```
3. Check if the bridge interface exists or not.
```
ifconfig
```
4. Inspect network
```
docker network inspect br02
```
5. Prune all unused networks.
```
docker network prune
```
6. Create a network with an IP range.
```
docker network create --subnet 10.1.0.0/16 --gateway 10.1.0.1 \
--ip-range=10.1.4.0/24 --driver=bridge --label=host4network br04
```
7. Inspect the `br04` network. Check at IPAM->Config. Check Labels as well.
```
docker network inspect br04
```
8. Create a container that will be using the `br04` network.
```
docker container run --name network-test01 -it --network br04 centos /bin/bash
```
9. Install Net Tools in the Centos image (optional).
```
yum update -y
yum install -y net-tools
```
10. Get the IP info for the container.
```
ifconfig
```
11. Get the gateway info the container.
```
netstat -rn
```
12. Get the DNS info for the container.
```
cat /etc/resolv.conf
```
13. Exit container.
```
exit
```
