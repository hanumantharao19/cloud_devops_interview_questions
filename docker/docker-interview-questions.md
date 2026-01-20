#docker
## 1) what is docker container
- A Docker container is a lightweight, portable runtime environment that runs an application along with its dependencies.
- You can login into the container to check or debug the application

## 2) what is the containerisation ?
- Containerization is the process of packaging an application along with its OS libraries and dependencies into a Docker image, which can run anywhere consistently.

## Benefits:

- Portable across any OS

- Consistent runtime environment

- No need to allocate fixed CPU or RAM manually
## 3) what is difference between virtualiation and containerisation
## virtualiation:
- a) we can install the vm ware software (hyperveser) on the physical machine
- b) create the mutiple machine with required os ,RAM and CPU

## containerisation:
- a)we can include application code, os and other software liabries as docker image
- b)run the docker iamges as contianer to host the application

## 4) what is a dokcer file?
- A Dockerfile is a text file containing instructions to build a Docker image.

## 5) what is a docker image?
- A Docker image is a read-only template containing all software, libraries, and instructions to create a container.

- Image → Container (runtime instance)

## 6) How to Build a Docker Image?
```
docker build -t <imagename> .
```
## 7) how to run a docker contianer?
```
docker run -d <imaagename> 
```
## 8) how to login into a container?
```
docker exec -it <cintainerid> /bin/bash
```
## 9)how to check the contianer logs?
```
docker logs -f <continaer id>
```
## 10)how to check running contaieners?
```
docker ps
```
## 11) how to check the containers( running and exist)
```
docker ps -a
```
## 12) how to stop and start container?
```
docker stop <container id>
docker start <contaier id>
```
## 13) how to remove a container?
```
docker rm <container id>
```
## 14) how to remove a running  container?
```
docker rm -f <container id>
```
## 15) how to tag an exising image for registry?
```
docker tag  <imagename>  <registryname>/<imagename>:tagname
```
## what is difference between docker stop and docker pause?
- Docker stop: Stops container and clears memory
- Docker Pauses container, memory remains intact
## 17) what is purpose RUN instruction?
- RUN instruction is used to execute any command and install any software in the contianer
## 18) what is the  purpose of  COPY instruction?
- COPY instruction is used to copy the file from docker host to docker container

## 19) what is the purpose of ADD instruction?
- 1)ADD instruction  is used to copy the file from docker host to docker container
- 2)ADD instruction  is used to copy the file from internet  to docker container

## 20) what is the purpose EXPOSE intruction?

- EXPOSE instruction is used to expose the application port

## 21) what is difference between CMD and ENTEYPOINT
## CMD:
- CMD defines the default command to run when the container starts.
- Only one CMD is allowed; if multiple are defined, the last one is used.
- CMD can be overridden by passing a command at runtime.
## ENTRYPOINT
- ENTRYPOINT defines the main command of the container.
- Only one ENTRYPOINT is allowed in a Dockerfile.
- ENTRYPOINT cannot be overridden; runtime arguments are appended to it.

## 22) can please write one sample docker file?
```
FROM centos:latest
MAINTAINER  hanumantharao1986.medikonda@gmail.com
RUN yum -y install httpd
COPY index.html /var/www/html/
EXPOSE 80
ENTRYPOINT ["/usr/sbin/httpd","-D","FOREGROUND"]
```
## 23) To pull the image from dokcer repositary
```
docker pull <imagename>
```
## 24) To attach running container
```
# docker attach <containeid>
```
## 25) how to remove the Docker image
```
docker rmi <imagename>
```
## 26) To know the docker information
```
docker info
```
## 27) Expose your application to host server
```sh
docker run -d  -p <host_port>:<container_port> --name <container_Name> <image_name>:<Image_version/tag>
## example
docker run -d - -p 8080:80 -name httpd_server httpd:2.2
```



