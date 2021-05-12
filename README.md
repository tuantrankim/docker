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
  Goto hub.docker.com to search an image. e.g: node
  
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
