# actionable docker
install it from => https://docs.docker.com/engine/install/

# common commands

```bash
# Shows you all the images that you have on your machine
docker images
# Shows you all the containers you are running on your machine
docker ps
# Lets you start a container
docker run mongo
# adding port mapping
docker run  -p 27017:27017 mongo
# starting in detatch mode
docker run -d -p 27017:27017 mongo
# Lets you build an image.
docker build -t image_name .
#Lets you push your image to a registry
docker push
# stop a docker conatiner
docker kill <id>
# execute command in container
docker exec ls /path/to/folder
# bash in interactive mode
docker exec -it /bin/bash
# login to docker via cli
docker login
# Push to the repository
docker push your_username/your_reponame:tagname
# Checking the logs
docker logs <container_id>
# remove docker image
docker rmi mongo --force
```
---
# Dockerfile
- WORKDIR: Sets the working directory for any RUN, CMD, ENTRYPOINT, COPY instructions that follow it.
- RUN: Executes any commands in a new layer on top of the current image and commits the results.
- CMD: Provides defaults for executing a container. There can only be one CMD instruction in a Dockerfile.
- EXPOSE: Informs Docker that the container listens on the specified network ports at runtime.
- ENV: Sets the environment variable.
- COPY: Allow files from the Docker host to be added to the Docker image

```dockerfile
# Base image
FROM node:20
# commands
WORKDIR /app

COPY . .

RUN npm install
RUN npx prisma generate
RUN npm run build

EXPOSE 3000

CMD ["node", "dist/index.js"]
```
2. build and run with port mapping
3. passing env variables
```bash
docker run -p 3000:3000 -e DATABASE_URL="postgres://avnadmin:AVN.a.aivencloud.com:25579/defaultdb?sslmode=require" image_name
```
# layers caches and optimization
```dockerfile
FROM node:20

WORKDIR /usr/src/app

COPY package* .
COPY ./prisma .

RUN npm install
RUN npx prisma generate

COPY . .

EXPOSE 3000

CMD ["node", "dist/index.js", ]
```
# Volumes
- to make data persisted after you kill the container
```bash
# create a volume
docker volume create volume_database
# Mount the folder in mongo which actually stores the data to this volume
docker run -v volume_database:/data/db -p 27017:27017 mongo
# Kill the container
docker kill <container_id>
# Restart the container
docker run -v volume_database:/data/db -p 27017:27017 mongo
```
# Networks
```bash
# Create a network
docker network create my_custom_network
# Start the backend process with the network attached to it and give it a name
docker run -d -p 3000:3000 --name backend --network my_custom_network image_tag
# Start mongo on the same network
docker run -d -v volume_database:/data/db --name mongo --network my_custom_network -p 27017:27017 mongo
# Check the logs to ensure the db connection is successful
docker logs <container_id>
```
# bind mounts
```bash
docker run -v /file/in/dockerfile /path/to/system-file -p 27017:27017 mongo
```
# pushing to dockerhub
1. create repository on dockerhub
2. create dockerfile
3. build dockerfile image
---
```bash
docker build -t repository_name:tagname
```
4. push dockerfile
---
```bash
docker login
docker push repository_name
```
