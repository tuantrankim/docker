# docker

https://www.youtube.com/watch?v=pTFZFxd4hOI

 Consistently run, build and ship applications
```
$docker version
$docker-compose up
$docker-compose down --rmi all
$docker run

(similar to Github)
DEV========>REGISTRY==========>TEST/PROD
Docker=====>Docker Hub========>Docker 
### Install docker
In Windows : HyperV and Container Windows feauture must be enabled.
WSL 2 installation is incomplete message: click on the link to update Linux kernel
```

### Create new project and open vs code
```
mkdir hello-docker
cd hello-docker
code .
```
#### Add new file app.js
console.log("Hello Docker!");
#### Run the app
node app.js

### INSTRUCTIONS
```
- Start with an OS
- Install Node
- Copy app files
- Run node app.js
```
### Create instruction file Dockerfile
  Goto hub.docker.com to search an image. e.g: node on a small linux distribution alpine
  
```
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
```
  
###  Build or create an image
```
~/hello-docker
$docker build -t hello-docker .
OR with tag
$docker build -t tuantrankim/hello-docker:v1 .
```
### Push the image to docker hub
```
docker login --username=your_docker_user_name
docker tag local-image:tagname new-repo:tagname
docker push new-repo:tagname
e.g.
$docker login --username=tuantrankim
$docker tag 14a9f0ebbf02 tuantrankim/hello-docker:v1

e.g.
docker push tuantrankim/hello-docker:v1
```

 ### View list images
```
$docker images
OR
$docker image ls
```
### Run the image (docker run = docker container run
```
docker run hello-docker
docker run tuantrankim/hello-docker:v1

docker run -d --restart=always --name web -p 8000:8080 tuantrankim/hello-docker:v1
-d: background running
-p: port mapping

docker run -it --name web -p 8000:8080 tuantrankim/hello-docker:v1
-it: interactive mode

```

###
```
$docker pull ubuntu
vs
$docker run ubuntu

View running docker process
$docker ps
view all include stopped container
$docker ps -a

Start a container in an interactive mode (it in short)
$docker run -it ubuntu


```
### Install packages using apt

```
View all packages installed
> apt list
Install nano
> apt install nano
Nano may not exist in package database, so need to update packages database
> apt update
Then install
> apt install nano
Uninstall nano
> apt remove nano

```

# LINUX
```

/: root
bin: binary or programs
boot: files relate to booting
dev: devices
etc: editable text configuration
home: home directory users are stored
root: home directory of the root user
lib: library files like software library dependencies
var: variables, files are updated frequently like logs, application data..
proc: running processes
```

# Linux command
```
pwd: print working directory
ls: list files, directories 
ls -l: long listing with details
cd: change directory
mkdir: make directory
mv: move or rename file/directory
touch: new files

root@48bb299fe454:/#
- root: current login user
- @48bb299fe454: name of the machine
- / : at root directory
- # : high privilege bc of login as root
- or $: low privilege

To see location of the shell program
echo $0

View history of command
history

Run the command at 2nd position
!2

```

## https://labs.play-with-docker.com
```
docker version
docker pull codewithmosh/hello-docker
docker image ls

docker run codewithmosh/hello-docker

goto dockerhub and create "new-repo"

$docker login --username=your_docker_user_name
$docker tag 14a9f0ebbf02 your_docker_user/your_docker_repo/spring-boot-docker:v1

docker tag local-image:tagname new-repo:tagname
docker push new-repo:tagname

e.g.
docker push tuantrankim/new-repo:2


```

## advance package tool (apt) is a package manager
```
Help
# apt

View all packages in package database(not all package installed)
# apt list

View installed packages
# apt list --installed

First update the package database
# apt update

Then install nano
# apt install nano

Can use dpkg to have better list of packages
$ dpkg --list | grep nano
$ dpkg --list | more

If a package install or not
$ apt list -a nano

Remove nano
$ apt remove nano

Install python
$ apt install python
```

# Dockerfile expose port
```
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 8080
EXPOSE 44311

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["ImsAPI.csproj", "."]
RUN dotnet restore "./ImsAPI.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "ImsAPI.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ImsAPI.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ImsAPI.dll"]
```

## Build
$ docker build -t tuantrankim/imsapi:latest .

## Run
$ docker run --name imsapi_test -d -it --restart=always -p 8080:8080 -p 43311:43311 --shm-size 2g tuantrankim/imsapi:latest
$ docker run -p 5000:80 -p 5001:443 -e ASPNETCORE_ENVIRONMENT="Development" --name tuantest_imsapi -d imsapi


## Reset ubuntu password for wsl2 

cmd> ubuntu config --default-user root

cmd> ubuntu

$ passwd

New password
