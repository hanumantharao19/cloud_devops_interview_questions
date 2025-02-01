#docker
## 1) what is docker container
docker contianer is nothing it is run time environement .then we can able to login the container and see the detatls

## 2) what is the containerisation ?
 a)we can include application code, os and other software liabries as docker image
 b)run the docker iamges as contianer to host the application
 c)we can able run the docker images any where ever we want 
 d) we can able run image any where like that it does not deppends on the os
 e) we are  ne need to allocate any resources like RAM and CPU  to the containerisation

## 3) what is difference between virtualiation and containerisation
virtualiation:
a) we can install the vm ware software (hyperveser) on the physical machine
b) create the mutiple machine with required os ,RAM and CPU

containerisation:
a)we can include application code, os and other software liabries as docker image
b)run the docker iamges as contianer to host the application

## 4) what is dokcer file?
a)Docekr file is used to  build docker image
b) Docker file  is place where we  can pass instructions to buiild the docker image.

## 5) what is docker image?
docker is read only template whcih contains all softewares liabries
 or

docker is read only template which contains all instructions to build the docker contianer

## 6) how to build the docker image?
```
docker build -t <imagename> .
```
## 7) how to run the docker contianer?
```
docker run -d <imaagename> 
```

## 8) how to login into container?
```
docker exec -it <cintainerid> /bin/bash

```

## 9)how to check the contianer logs?
```
docker logs -f <continaer id>
```

## 10)how to check the running contaieners?
```
docker ps
```
## 11) how to check the all containers( running and exist)
```
docker ps -a
```
## 12) how to stop and start the container?
```
docker stop <container id>
docker start <contaier id>

```
## 13) how to remove the container?
```
docker rm <container id>
```
## 14) how to remove the running  container?
```
docker rm -f <container id>

```
## 15) how to tag the exising image to the docker registry or any registry?
```
docker tag  tagname  <registryname>/tagname
```
## what is difference between docker stop and docker pause?
- The main difference between the paused and stopped states is that the memory portion of the state is 
  cleared 
- when a container is stopped, whereas, in the paused state, its memory portion stays intact.
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
- 1) There can only be one CMD instruction in a Dockerfile.
If you list more than one CMD then only the last CMD will take effect.
2) CMD Paremters can able to replace with command line arguments 
## ENTRYPOINT
- 1)ENTRYPOINT should be use only one time in the docker file
- 2)ENTRYPOINT command and parameters will not be overwritten from command line. 
- Instead, all command line arguments will be added after ENTRYPOINT parameters

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
docker pull imagename
```

## 24) To attach running container
```
# docker attach containeid
```

## 25) how to remove the Docker image
```
docker rmi imagename
```
## 26) To know the docker information
```
docker info

```

## 27) Expose your application to host server
```sh
docker run -d  -p <host_port>:<container_port> --name <container_Name> <image_name>:<Image_version/tag>

docker run -d --name httpd_server -p 8080:80 httpd:2.2
```

