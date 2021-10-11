#  :whale: Docker

- what is docker and  container ? 
- difference  of  vm and containers
- main commands
- debugging  A container



:package: **Container** : a way  to **package** application with **all** the **necessary** **dependencies** and **configuration** 

:arrow_forward: portable artifact , easily shared and moved around

:arrow_forward:Make Development and deployment more efficient

   Storage

- Container Repository

- Private Repository 

- Docker hub

Before Containers

- Installion process different on each os  enviroment

- many steps where some ting could go wrong 

After Containers

- own isolated enviroment 

- packaged with all needed configuration 

- one command to install the app 

- run same app with 2 different versions

  

## what is a container?

layers of images

mostly linux base image, because small in size

Application image on top 



 how to use docker?

- **step** **1**: find your images  in dockerhub or ..

- **step2**: pull or  run it  

  `docker  run/pull  x : V  / x (the latest)` 

  **checking**  `docker ps` 

  `docker ls`    

Image is ...(**not running**)

- the actual package
- artifact, that can be moved around

Docker Container is ...(**running**)

- actually start the application

- container environment is created

## Docker vs Virtual Machine

 docker image  have just application layer  and vm has his own  kernel and application layer

docker container is much smaller and faster

vm is more compatible  you can run it in every  OS and hosts



## basic commands

1. **docker image** : to check the images on  your host

2. **docker pull  x** : to pull docker image from repositories

3. **docker run  x** : to run and create docker container
-  -p*host_port:container_port*    :  for port  >   `docker run redis  -p 6000:6037`  
	-  version :  docker run redis:6.9
	- -d  for detached mode 
	- --name   name for container
	- it also  do  pulling command too . 

4. **docker ps** : show all the container in  your host
 - -a : show you list of all  images (running  or not)
5. **docker stop  container_ID**
6. **docker start  container_ID** (restart stoped container)

## troubleshooting  in container

- docker  log  container_id
- docker exec -it  container_id  /bin/bash 
- 

