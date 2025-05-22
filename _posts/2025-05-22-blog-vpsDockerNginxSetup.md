---
title: "VPS Docker Deployment Using Nginx"
date: 2025-05-22T23:33:00+01:00
categories: ['Setups']
tags: ["setup,linux"]
---

# Nginx Docker Setup on a VPS

```
mkdir ~/dockerDemo/html && cd ~/dockerDemo;
echo 'hello world from docker using nginx' > html/index.html
touch Dockerfile docker-compose.yml nginx.conf

#nginx.conf
events {}
http {
    server {
        listen 80;
        server_name sub.domain.com www.sub.domain.com>

        root /usr/share/nginx/html;
        index index.html;
        location / {
            try_files $uri $uri/ =404;
        }
    }
}

#Dockerfile
FROM nginx:alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY html/ /usr/share/nginx/html/

#docker-compose.yml
services:
  nginx:
    build: .
    ports:
      - "80:80"
    restart: always

#Build image and serve
docker compose build
docker compose up -d

#Verify the docker is serving the html site
#Checking Locally
curl localhost:80 
# After pointing to the subdomain via cloudflare
curl http://sub.domain.com 
```