# docker

https://www.youtube.com/watch?v=pTFZFxd4hOI

 Consistently run, build and ship applications

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

### Create new project and open vs code
mkdir hello-docker
cd hello-docker
code .

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
  
  Build or create an image
```
~/hello-docker
$docker build -t hello-docker .
```

  View list images
```
$docker images
OR
$docker image ls
```
Run the image
```
docker run hello-docker
```
###
$docker pull ubuntu
vs
$docker run ubuntu

Any container ?
$docker ps
view all include stopped container
$docker ps -a

Start a container in an interactive mode
$docker run -it ubuntu

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
```
