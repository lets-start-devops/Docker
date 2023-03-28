# Welcome To Docker
## Docker Commands



> This guide containts the commands that were ran
> during the workshop. 



## Installation

Please follow the instructions mentioned in the [Docker Website](https://www.docker.com/products/docker-desktop/) to run docker containers.

## Docker Login Command

> docker login


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

### Copy Files in Container



```sh
docker container cp c:/tmp/index.html httpd:/etc/index.html
docker container cp httpd:/etc/index.html c:/tmp/index.html 

```

### Volumes

```sh
docker volume create <vol name>
docker volume inspect test  -->  df -h | grep /test from container

 docker volume remove <vol name>

docker container run --mount source=<vol name>,destination=/<path> httpd

docker container run --mount source=<vol name>,destination=/<path> httpd

docker container run --mount type=bind,source=F:\My-Devops-Class-Workspace\Docker\httpd\index.html,destination=/usr/local/apache2/htdocs/index.html -d -p 8083:80 httpd         ---> mount a directory to from the docker host to the container
```

✨Note✨
- By default volumes are mounted ain ReadWrite mode, use 'readonly' flag while mounting the flag to a container

## Build & PUSH Docker Image

In order to build a docker image create a `Dockerfile` having the set of instructions catering your needs. Once done, run the below commands :- 

```sh

docker image build . -f <Dockerfilename> -t <tag to give to the docker>:<version>

docker push <tag to given to the docker image>:<version>

 docker history   --> to investigate the changes done on your image

```
✨Note✨
- If you do not wish to create a docker file but instead use an existing container to build an image then make the desired changes in your container and run commit command. The `-a` flag stands for `author`. This com,mand will save it as an image.  

>docker container commit -a "Shivakumar Darapu" clever_poitras podus:apache2