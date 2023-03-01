# Docker Learnings

## Basic commands

 

Docker ps -> list of running containers

Docker ps -a -> list of all running and previously exited containers

Docker stop containerName/containerID -> stops a container

Docker rm containerName -> removes a stopped/ exited container

Docker images -> lists all downloaded images

Docker rmi imageName -> deletes the downloaded image(We have to delete all dependent containers)

Docker exec containerName commandToExecute -> executes a command inside container

Docker attach containerID -> attaches the container logs to terminal

 

 

Docker Run

 

Docker run imageName:version

 

Docker run - STDIN

Docker run -it imageName -> -I to read input from terminal and t to connect to sudo terminal inside container

 

Docker run - PORT mapping

Docker run -p 80:80 imageName

 

Docker run VOLUME - mount

Docker run -v /opt/datadir:/var/lib/mysql mysql

 

Inspect container

Docker inspect containerName -> returns container data in JSON format

 

Container Logs

Docker logs containerName

 

Environment Variables in Docker

 

Docker run -e var1=value imageName:tag

 

We can find the set environment variables for a running container using docker inspect command(under config property with name ENV)

 

Docker network types

 

Bridge: Gets create & attached by default to the container Ex: docker run imageName

None: None of network is attached to container Ex: docker run --network=none imageName

Host: container directly get attached with host port number Ex: docker run --network=host imageName

Disadvanatge: we cannot run multiple containers with same port

 

User-defined network

Used to create isolated network for few specific networks. By default docker host creates only one docker bridge network.

 

Command: docker network create --driver bridge --subnet 182.18.0.0/16 custom-isolated-network

 

List all networks: docker network ls

 

Embedded DNS: docker has inbuilt DNS, which can be used to connect to containers using the container names

 

Docker Volumes

 

Command to create a volume: docker volume create data_volume

Filestructure:

IlMyb4bjqkAAAAASUVORK5CYII=

 

Mounting volumes to container:

Docker run -v data_volume:/var/lib/mysql mysql.        199619

 

Two types of data storages:

Volume Mount: will mount storage under the volume directory.
Bind Mount: will mount any directory from Docker host.
Example: docker run --mount type=bind,source=/data/mysql,target=/var/lib/mysql mysql
