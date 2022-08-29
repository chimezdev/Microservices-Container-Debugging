# PROCEDURES

# Prerequisites
Familiarity with frontend development using JavaScript and HTML
Backend development using NodeJS
AWS: RDS, S3, IAM
Git for version control
Command line ( I use Linux)

# You should have an understanding of what Microservices and Monoliths applications are.
`Microservices` are Independently-deployed components of a system that communicate with one another through network communication such as REST APIs, GraphQL, Pub/Sub, Queue etc to achieve a bigger task
No. of engineers, parallel development and choice of technology are some business requirement that should make you choose Microservices
`Monoliths` are self-contained applications deployed as a single unit. Consideration for using Monoliths includes: Network latency and system complexity 
Note: Business requirements should drive your choice of choosing either of the above.

# Refactoring a Monolith application to a Microservice
Understand the application you are working on
Consider looking at Dependency graph
Employ Strangler pattern

# Overview

This is a very simple, bare-bones NodeJS project created for you to use with Docker. This project has an error in it that we want to diagnose after the Docker image is built and run in a container

# It is assumed you have installe and configured the following
AWS CLI
Created an IAM user with Admin permisions
Configured the AWS CLI and IAM Credentials locally

`CONTAINERS` 
We often have to install different dependencies for our code to run. And it is often a nightmare having our code run in development environment and not run in our production environment. Containers help solve these by packaging all of our dependencies such that our application will run on any environment. Containers are ephemeral instances, stateless and are expected to be terminated anytime.
`Docker` 
A platform that helps us manage the creation and life-cycle of our container. Offers container services known as Docker container.
`Dockerfile` instructional file on translating an application into a docker image.
`Docker image` snapshot of dependencies and code required by applications to run in a docker container.
`Docker container` Grouped software dependencies and packages that make it easier and more reliable deploy software.
`Container Registry` A centralized place to store container images.


## Local Setup

**_Note_**: This is only needed if you want to run the app locally. You don't need to install the dependencies or run the server if you are running the code inside a Docker container.

 Clone the repo: https://github.com/chimezdev/Udacity-ALX-Project-3.git
- Install dependencies: `npm install`
- Run server: `node server.js`

## Container Setup

- Build image: `docker build -t simple_node .`
- Run container with image: `docker run {image_id}` where `image_id` can be retrieved by running `docker images` and found under the column `IMAGE ID`
- You can run ` docker run -d <img id>` including the -d flag to run the container in the background. This will enable you to run other commands in your terminal while the container is running.

## Container Teardown
-open another terminal, run `docker ps` which will show running containers and their id under the column `CONTAINER ID` copy this id
- Remove container: `docker kill {container_id}` 

# Debugging Containers
run `docker ps` to get the running container id or `docker ps -a` to include terminated containers. 
To get meta-data for a container, run `docker inspect` 
`docker logs` prints all logs for a running container
`docker exec -it <container id> sh` will allow you ssh into the container. 
`ps aux` to exit out of the container after debugging