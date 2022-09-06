# Docker

## Links

- <https://www.section.io/engineering-education/build-and-dockerize-a-full-stack-react-app-with-nodejs-and-nginx/>

## How to write Dockerfile files

<https://takacsmark.com/dockerfile-tutorial-by-example-dockerfile-best-practices-2018/#dockerfile-best-practices>

## How to install docker | docker install

```sh
# First good to run:
sudo apt-get update && sudo apt-get upgrade
# Then:
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
# If you want skip using `sudo` add pi user to docker group:
sudo usermod -aG docker pi
# Restart pi
sudo reboot
docker version
```

Pre-made containers are called images.

[https://github.com/btholt/complete-intro-to-containers](https://github.com/btholt/complete-intro-to-containers)

[https://btholt.github.io/complete-intro-to-containers/docker-cli](https://btholt.github.io/complete-intro-to-containers/docker-cli)

## Useful commands

docker info

docker kill docker_name

docker run -dit node:12-stretch

docker run -it node:12-stretch bash

docker container prune

docker image list

docker ps —all

docker image prune

docker exec -it docker_name bash

docker kill $(docker ps -q)

docker restart docker_name

docker search name

docker start —init docker_name

docker start —init —rm —publish 3000:3000 docker_name

## Dockerfile

It is a series of instructions - very procedure. Each line is an instruction.

## Steps to run projects

1. Create Dockerfile

```Dockerfile
FROM node:16-alpine
ENV NODE_ENV=production
COPY . .
RUN npm install --production
RUN npm install pm2 -g
CMD ["node", "server.js"]
CMD ["pm2-runtime", "server.js"]
EXPOSE 3000/tcp
EXPOSE 3000/udp
```

2. Build image

```sh
docker build -t micro-networks:v1 .
```

3. Run image as container

```sh
docker run -d -p 3000:3000 6a6837f62c1c
```

<!-- Remember about open ports to system -->
<!-- -d detach mode, close connection and write container id on start -->

## Publish image to dockerhub docker.io

```sh
docker login
# latest is a tag name
docker tag image_name:latest dockerhub_user_name/image_name:latest
docker push dockerhub_user_name/image_name:latest
```

Now you can pull image from hub and run it:

```sh
docker pull dockerhub_user_name/dockerhub_user_name:latest
docker run -it dockerhub_user_name/dockerhub_user_name:latest
# my personal example:
docker run -it -p 3000:3000 tullece/micro-network:arm6-latest
docker run -it tullece/micro-dns:arm6-latest
```

Full proces of publishing and running docker:

```sh
docker build -t micro-network:arm6-latest .
docker tag micro-network:arm6-latest tullece/micro-network:arm6-latest
docker push tullece/micro-network:arm6-latest
docker stop ae62e554aef3
docker pull tullece/micro-network:arm6-latest
# If we run container in host network setting port is not needed -p 3000:3000
docker run -d --network host tullece/micro-network:arm6-latest
```

## Restart all containers

```sh
docker restart $(docker ps -q)
docker restart $(docker ps -a -q)
# or for docker-compose
docker-compose restart
```

## Stop all containers

```bash
docker kill $(docker ps -q)
```

## Remove all images / remove all containers

```sh
# Remove all containers
docker rm $(docker ps -a -q)
docker rm -vf $(docker ps -a -q)
# Remove all images
docker rmi -f $(docker images -a -q)
# Prune system with
docker system prune
```

## Remove all stopped containers

```sh
docker container prune
```

## Chceck docker logs

```sh
docker logs {docker_name or docker_container_id}
```

## Jak skierować domenę bezpośrednio na port 8080, bo teraz po uruchomieniu nginx trzeba wpisać w pasku adresu domena.pl:8080

Należy odpalić container przy uzyciu -p ```80:80``` a nie jak to jest w dokumentacji hub docker dla nginx tam znajdziemy tylko: ```8080:8080```

W naszym przypadku będzie to:

```sh
docker run --name some-nginx -d -p 80:80 nginx
```

## How to overwrite configuration locally from server and user as volumes | nginx local configuration nginx

## How to run command on running server

```sh
docker exec -it 65c366f04b86 cat /etc/nginx/nginx.conf
# -i, --interactive          Keep STDIN open even if not attached
# -t, --tty                  Allocate a pseudo-TTY
```

[use-a-pre-existing-network](https://docs.docker.com/compose/networking/#use-a-pre-existing-network)

Problem exists because `host` in docker is representation of machine network. [Read](https://codeblog.dotsandbrackets.com/communication-between-docker-containers/)

<https://docs.docker.com/compose/compose-file/compose-file-v3/>

> You need use container name in fetch methods

## Differce between `expose` and `ports`

expose ports to linked services (not to host) within docker containers.

## Why create-react-app is not auto reloading

This issue was in file Dockerfile The workdir was /var/app/ while in my docker-compose.yml I mounted current working directory to /var/app/frontend, I just removed that /frontend and works fine.

## Develop docker-compose build

Command:

```sh
docker-compose up --build --force-recreate
```

> Avoid issue when docker won't up, because of provided empty volume

- `--build` - Build images before starting containers.
- `--force-recreate` - Recreate containers even if their configuration and image haven't changed.

## Example of Dockerfile file

```Dockerfile
FROM node:12.18.3

LABEL version="1.0"
LABEL description="This is the base docker image for the Tweet Sentiment Analysis frontend react app."
LABEL maintainer = ["danielmurph8@gmail.com", "dylanedwards290@gmail.com"]

WORKDIR /app

COPY ["package.json", "package-lock.json", "./"]

RUN npm install --production

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

`FROM`: Defines the image we will use as the basis for our container. In this context, we use Node Version 12.18.3.
`LABEL`: Defines the metadata for our Dockerfile, including information about the version, description, and maintainers.
`WORKDIR`: Sets the working directory for the application. If the working directory does not already exist, it is created by Docker.
`COPY`: Copy a file or files into the Docker container. On line 9, we list several files to copy and then specify where to copy them. The final path specified is the location the files are copied to (in this case, the working directory).
`RUN`: Specifies a command that should be run by Docker. I typically use this command to install dependencies, debug, and execute commands in the container. In this context, we run npm install --production to only install production dependencies.
`EXPOSE`: Tells Docker which ports the container should listen on during runtime. In this context, we expose port 3000 since that is the port that React is running on.
`CMD`: Specifies the command that should be executed when the docker container starts. In this context, we run npm start since that is the command that starts the frontend.

## Example of docker-compose file

```yml
version: '3'

services:
    backend:
      env_file:
          "./backend/backend.env"
      build:
        context: ./backend
        dockerfile: ./Dockerfile
      image: "dmurphy1217/twitter-sentiment-backend"
      ports:
        - "5000:5000"
    frontend:
      build:
        context: ./client
        dockerfile: ./Dockerfile
      image: "dmurphy1217/twitter-sentiment-frontend"
      ports:
        - "3000:3000"
      links:
        - "backend:be"
```

## Example of `docker run command`

```sh
docker run -dp 3000:3000 `-w /app -v "$(pwd):/app" ` node:12-alpine `sh -c "yarn install && yarn run dev"
```

## How to login to remote registry

```sh
docker login nexus.dtc.prod.company.plc
```

## Remove all containers and docker images

```sh
docker system prune
```

### Dockerfile run from different location

```sh
CMD [ "npm", "--prefix", "packages/app1-server", "start" ]
```

## Build docker image for a different platform - armhf | amd64

```sh
docker build . -t my_service --platform=linux/armhf
```

## How to push/publish image to remote/not default registry

```sh
docker images
docker tag docker-image:0.1.0 nexus.dtc.prod.company.plc/docker-image:0.1.0
docker push nexus.dtc.prod.company.plc/docker-image:0.1.0
## Use internal network name instead of machine host name
## Docker course

```sh
echo "HELLO" > hello.txt
docker run -v $(pwd):/app alpine cat /app/hello.txt
docker run -it alpine /bin/sh
docker run node:latest node -e "console.log(process.version)"
docker run -e NAME=world node:latest node -e "console.log(process.env.NAME)"
docker run -p 3306:3306 -d --name mysql-container -e MYSQL_USER=user MYSQL_PASSWORD=password MYSQL_ROOT_PASSWORD=root --rm mysql:5.7
docker build -t tag-name:latest .
docker network create alpine-network
docker run -it -d --rm --name alpine-1 --network alpine-network alpine /bin/sh
-t (tag name)
-e (evaluate)
-d (detached mode)
-it (interactive)
--rm (remove container on stop)
curl localhost:3000/health
```

```text
Difference between `RUN` and `CMD` in Dockerfile
- `RUN` is creating another layer of docker container but `CMD` is able to run command inside of container

multistage build - use container to build another container/files for another container
```

???
$ docker info  -f '{{.OSType}}/{{.Architecture}}' //linux/x86_64
???
