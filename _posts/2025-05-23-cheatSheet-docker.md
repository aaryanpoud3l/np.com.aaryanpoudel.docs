---
title: "Cheatsheet for Docker"
date: 2025-05-23T15:42:00+01:00
description : "Cheatsheet for Docker"
categories : ["CheatSheets"]
tags : ["blog","cheatsheet",'tldr']
---

### Image
```sh
docker run imageName
docker build -t yourImageName .
docker images
docker rmi imageName
docker image prune
```

### Container
```sh
docker ps
docker ps -a
docker container stats

docker start containerName
docker stop containerName

docker rename oldName newName
docker rm containerName
docker rm -f containerName #If running
docker container prune

docker exec -it containerName sh #Run Shell
```

### Docker Compose
```sh
docker run -d -name yourContName imageName
docker compose build
docker compose up -d
docker compose up -d --build
```