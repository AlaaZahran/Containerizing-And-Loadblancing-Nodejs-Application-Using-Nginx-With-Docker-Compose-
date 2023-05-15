
# Containerizing-And-Loadblancing-Nodejs-Application-Using-Nginx-With-Docker-Compose


![image](https://github.com/AlaaZahran/Containerizing-And-Loadblancing-Nodejs-Application-Using-Nginx-With-Docker-Compose-/assets/46306526/f534f888-aa42-47ef-ac4e-8f24934ea648)



# Description

This project aims to build and Containerize three tier application  so it is includes many steps :

1- Create a docker file to build nginx image to run a container that used as a load balancer between two web server

2- Create a docker file to build two web servers based on node.js, that function to count the number of visitors

3- build a docker-compose file that contains four containers (1=> nginx, 2=>web server 1=> redis database ) and assign volumes to each container

# Nginx Steps

1- Create nginx configration to use it as Loadblaner 

2- Create Dockerfile that use nginx official image
and copy nginx.conf into /etc/nginx/conf.d/default.conf to set default configration 

# Two Web applications Steps


1- Create server.js to count the number of visits of the web application and store results in redisDB.

2- Create package.json file which includes all the dependencies  and script that start server.js file. 

1- Create Dockerfile that use node:alpine base image , copy package.json and server.js inside /app  , install and start npm 

# Docker Compose File

it used to create 4 containers as following :

1- server 1,2 :

  will create 2 containers using Dockerfile for each one , listen on port 5000 and maps ports [81,82] from host side  and attach volumes to each one .

2- nginx : 

will use Dockerfile for nginx and listen on port 80  which maps port  80 from host side , depend on server 1,2 and attach volume to it .

3- redis:

will use redis official image to run container that store number of web visitors and attach volume to it .

# Deployment 

run the following command :
```
docker compose up -d
```





















