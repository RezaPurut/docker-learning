# Executing Container Commands
Three ways:
  * Dockerfile
  * During a Docker run
  * Using the exec command
 
## 1. Dockerfile
Dockerfile will be covered in another notes.
 
## 2. Docker run
will start up a new container and run a process within that new container
 
Example below will start a /bin/bash or terminal process in the container and user also will be in the terminal until the user exit.
```
docker container run -it nginx /bin/bash/
```
Exiting the /bin/bash will cause the container to stop as well.
 
## 3. exec
run a command in an existing container
```
docker container exec -it [NAME] /bin/bash
docker container exec -it [NAME] ls /usr/share/nginx/html/
```
Exiting /bin/bash will not cause the container to stop. 
