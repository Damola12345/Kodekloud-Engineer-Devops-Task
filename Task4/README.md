# Docker Ports Mapping

## TASK
- The Nautilus DevOps team is planning to host an application on a nginx-based container. There are number of tickets already been created for similar tasks. One of the tickets has been assigned to set up a nginx container on `Application Server 3` in `Stratos Datacenter`. Please perform the task as per details mentioned below:

- a. Pull `nginx:alpine-perl` docker image on `Application Server 3`.

- b. Create a container named news using the image you pulled.

- c. Map host port 8085 to container port 80. Please keep the container in running state.

## SOLUTION

* Login in  App server  (stapp03, ) & switch to root  user 
    -  ssh Banner@stapp03
    -  sudo su -

* Run Below command to check existing docker images 
    - docker images

* Pull Docker image  on server  
    - docker pull nginx:alpine-perl

* Verify the pull image
    - docker images

* command to run container
    - docker container run -d --name news -p 8085:80 nginx:alpine-perl 
    - docker ps

* Validate the task
    - curl http://localhost:8085