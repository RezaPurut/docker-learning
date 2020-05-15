# Networking Commands
1. List all Docker network commands
```
docker network -h
```
Result:
**`connect`** - Connect a container to a network
**`create`** - Create a network
**`disconnect`** - Disconnect a container from a network
**`inspect`** - Display detailed information on one or more networks
**`ls`** - List networks
**`prune`** - Remove all unused networks
**`rm`** - Remove one or more networks

2. List all Docker networks on the hos
```
docker network ls
docker network ls --no-trunc
```
3. Inspect the network (get detailed info)
```
docker network inspect [NAME]
```
4. Creating a network
```
docker network create br00
```
5. Deleting a network
```
docker network rm [NAME]
```
6. Remove all unused networks
```
docker network prune
```
