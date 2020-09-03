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
# Assigning IPs to a container (when you want to assign specific IP to a container)
1. Create a new container and assign an IP to it
```
docker container run -d --name network-test02 --ip 10.1.4.102 --network br04 nginx
```
2. Get the IP info for the container.
```
docker container inspect network-test02 | grep IPAddr
```
# Networking two containers
1. Create a new bridge network. internal flag telling docker we do not want network to be bound to any interfaces.
```
docker network create -d bridge --internal localhost
```
2. Create a MySQL container that is connected to localhost. `e` flag is environment flag.
```
docker container run -d --name test_mysql \
-e MYSQL_ROOT_PASSWORD=P4sSw0rd0 \
--network localhost mysql:5.7
```
3. Create a container that can ping the MySQL container (to test it).
```
docker container run -it --name ping-mysql \
--network bridge \
centos
```
4. Connect ping-mysql to the localhost network.
```
docker network connect localhost ping-mysql
```
5. Restart and attach to container. `i`-interactive, `a`-attach.
```
docker container start -ia ping-mysql
```
6. Ping the mysql container.
```
ping test_mysql
```
7. Create a container that can't ping the MySQL container
```
docker container run -it --name cant-ping-mysql \
centos
```
8. Create a Nginx container that is not publicly accessible.
```
docker container run -d --name private-nginx -p 8081:80 --network localhost nginx
```
9. Try curl. It will fail because it is internal and not bound to any interfaces on the docker host. Can curl the private ip.
```
curl localhost:8081
```
10. Inspect private-nginx to get the private ip. Then can curl the private ip.
```
docker container inspect private-nginx
curl <private-ip>
```
