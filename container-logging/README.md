# Container Logging
1. Show information logged by a running container
```
docker container logs [NAME]
```
2. Show information logged by all containers participating in a service:
```
docker service logs [SERVICE]
```
3. Logs need to be output to STDOUT and STDERR
For Nginx:
```
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
```
