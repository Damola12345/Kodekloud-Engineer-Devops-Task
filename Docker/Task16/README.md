# Docker EXEC Operations

## TASK

One of the Nautilus DevOps team members was working to configure services on a kkloud container that is running on `App Server 3` in Stratos Datacenter. Due to some personal work he is on PTO for the rest of the week, but we need to finish his pending work ASAP. Please complete the remaining work as per details given below:


- a. Install apache2 in `kkloud` container using apt that is running on `App Server 3` in Stratos Datacenter.

- b. Configure Apache to listen on port `8086` instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on `localhost`, `127.0.0.1`, container ip, etc.

- c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

## SOLUTION

* Login in  App server  (stapp03, ) & switch to root  user 
    -  ssh Banner@stapp03
    -  sudo su -

* Run Below command to check existing docker images 
    - docker ps -a

* Login on docker container (ubuntu ) & install apache2
    - docker exec -it kkloud /bin/sh
    - apt install apache2 -y
    - cd /etc/apache2
    - sed -i 's/Listen 80/Listen 8086/g' ports.conf
    - sed -i 's/:80/:8086/g' apache2.conf
    - sed -i 's/#ServerName www.example.com/ServerName localhost/g' apache2.conf

* Start apache2 service & confirm the running status
    - service apache2 start
    - service apache2 status

* Validate the task by Curl
    - curl -Ik localhost:8086

## Problem i encounter and fixed

* I made a mistake with port and i tried to fix it 
    - 
    ```bash
        service apache2 start
        The apache2 configtest failed.
        Output of config test was:
        AH00526: Syntax error on line 5 of /etc/apache2/ports.conf:
        Invalid address or port
        Action 'configtest' failed.
        The Apache error log may have more information.
        ```

* I install vi editor and edit the below config and changed the port 
    - apt-get update
    - apt-get -y install vim
    - vi /etc/apache2/ports.conf  

