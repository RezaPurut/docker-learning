# Creating Containers
``` docker container run ``` or ``` docker run ```

This command creates a container from a given image and starts the container using a given command

**`--help`** Print usage

**`--rm`** Automatically remove the container when it exits

**`-d`**, **`--detach`** Run container in background and print container ID

**`-i`**, **`--interactive`** Keep STDIN open even if not attached

**`--name string`** Assign a name to the container

**`-p`**, **`--publish list`** Publish a container's port(s) to the host

**`-t`**, **`--tty`** Allocate a pseudo-TTY

**`-v`**, **`--volume list`** Mount a volume (the bind type of mount)

**`--mount mount`** Attach a filesystem mount to the container

**`--network string`** Connect a container to a network (default "default")

### Create a container and attach to it
``` docker container run –it busybox ```

### Create a container and run it in the background
``` docker container run –d nginx ```

### Create a container, name it and run it in the background
``` docker container run –d –name myContainer busybox ```

## Reference
https://stackoverflow.com/questions/51247609/what-is-the-difference-between-docker-run-and-docker-container-run
