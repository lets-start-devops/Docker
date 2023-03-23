# Welcome To Docker
## Docker Commands



> This guide containts the commands that were ran
> during the workshop. 



## Installation

Please follow the instructions mentioned in the [Docker Website](https://www.docker.com/products/docker-desktop/) to run docker containers.


## Docker Containers Commands:

### List Containers

```sh
docker container ls
docker container ls -a          --> all
docker container ls -l          --> last
docker container ls -q          --> container id
```


### Create Container
```sh
docker container create --name=httpd httpd

docker container start <name/id>

docker container rename <oldname> <newname>

docker container run httpd

docker container run -it ubuntu  press CTRL + P + Q to exit without stoping the container

docker container run -d httpd

docker container run --restart=always httpd  --> no / on-failure/always/unless-stopped

docker container run -d -p 8081:80 httpd    --> server port:container-port
```

### Logging into the Container:

```sh
docker container exec <container name/id> <command to execute>
docker container exec -it <container name/id> /bin/bash
docker container attach <container name/id>
docker container run -it ubuntu   
```
✨Note✨
- press CTRL + P + Q to exit without stoping the container

### Inspect Container
```sh
docker container inspect <name>
docker container stats
docker container top <name>
docker container logs <name>
docker container logs -f <name>             ---> stream the logs
docker system events --since 60m            ---> docker events like if a container start stop
```

### Stop/Delete Containers:

```sh
docker container pause/unpause <name>
docker container stop <name>
docker container rm <name>              --> stop before removing
docker container stop $(docker container ls -aq)  -> delete all containers
docker container rm $(docker container ls -aq)  -> delete all containers
docker container prune --> stop and delte all
```

#### Copy Files in Container



```sh
docker container cp c:/tmp/index.html httpd:/etc/index.html
docker container cp httpd:/etc/index.html c:/tmp/index.html 

```

