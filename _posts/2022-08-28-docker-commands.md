---
layout: post
author: aishwarya
---

# Docker Commands Reference
This post gives an overview on some commonly used Docker CLI commands, as well as some advanced commands that could help in the future.

### Docker Basic Commands
- Pull a docker Ubuntu image from Docker hub
```docker pull ubuntu```

This downloads the image tagged "latest" by default. To download a specific tag, say 20.04, use

```docker pull ubuntu:20.04```
- Check which images are available on the device
```docker images```
- Check if any containers are running
```docker ps```
Add the ```-a``` argument to list all containers (even stopped ones).
- Launch a container "container1" from the Ubuntu image downloaded earlier
```docker run --name "container1" -dit ubuntu bash```
- Launch container, mapping port 8080 of docker host with container port 3000
```docker run -p 127.0.0.1:8080:3000/tcp -dit ubuntu bash```
- Run a command on the container without entering it
```docker exec -d container1 touch /newfile```
- Enter a docker container from Powershell
```docker exec -it container1 bash```
- Stop a container
```docker stop container1```
- Start a container
```docker start container1```
- Remove a stopped container
```docker rm container1```
- Remove an image, ensure no containers use this image
```docker rmi ubuntu```


### Advanced commands
- Create an image from a running container
```
docker stop container1
docker commit container1 mynewimage
```
- Inspect a container (for running container)
```docker inspect container1```
- Attach a volume to a container
```docker run -p 127.0.0.1:3000:3000/tcp --name=project -dit -v c:\Users\username\Documents\:/home/it5007/ ubuntu bash```
- Copy a file from laptop to container's /home folder
```docker cp .\trial.txt container1:/home/```
- Save a docker image as a tar file
```docker save -o mynewimage.tar mynewimage:latest```
- Import an image tar file into a docker image
```docker load -i mynewimage.tar```

Please note that this is a very basic overview of some commonly used Docker commands. If you would like to explore the whole plethora of docker CLI commands, please refer to https://docs.docker.com/engine/reference/run/.