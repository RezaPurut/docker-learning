# Container Logging
1. Show information logged by a running container
```
docker container logs [NAME]
```
2. Show information logged by all containers participating in a service:
```
docker service logs [SERVICE]
```
3. Logs need to be output to `STDOUT` and `STDERR`
For Nginx:
```
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
```
Example:
Debug a failed container deploy
```
docker container run -d --name ghost_blog \
-e database__client=mysql \
-e database__connection__host=mysql \
-e database__connection__user=root \
-e database__connection__password=P4sSw0rd0! \
-e database__connection__database=ghost \
-p 8080:2368 \
ghost:1-alpine
```
The above will fail if no 'ghost' database

Check the error using this command
```
docker container logs [NAME]
```
