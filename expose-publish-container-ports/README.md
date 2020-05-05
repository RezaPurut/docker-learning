# Exposing and Publishing Container Ports
1. Exposing means make a port available to be mapped
```
docker container run -d --expose 3000 nginx
```
2. Expose and create mapping. First port after `-p` is the host port. Port after `:` is container port that we want to map
```
docker container run -d --expose 3000 -p 80:3000 nginx
```
3. If you try to curl the example above, it won't work because no service is listening on port 3000

4. Below will work for nginx since nginx is listening on port 80. But port 3000 is not being mapped with anything.
```
docker container run -d --expose 3000 -p 8080:80 nginx
```
5. Mapping both tcp and udp ports
```
docker container run -d -p 8081:80/tcp -p 8081:80/udp nginx
```
6. Randomly assign ports `-P`
```
docker container run -d -P nginx
```
7. Check port mapping of a container
```
docker container port [Container_NAME]
```
