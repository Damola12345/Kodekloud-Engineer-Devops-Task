# Puppet Setup Database

## Task

The Nautilus DevOps team had a meeting with development team last week to discuss about some new requirements for an application deployment. Team is working on to setup a mariadb database server on Nautilus DB Server in Stratos Datacenter. They want to setup the same using Puppet. Below you can find more details about the requirements:



- Create a puppet programming file `games.pp` under `/etc/puppetlabs/code/environments/production/manifests` directory on puppet master node i.e on Jump Server. Define a class mysql_database in puppet programming code and perform below mentioned tasks:

- Install package mariadb-server (whichever version is available by default in yum repo) on puppet agent node i.e on DB Server also start its service.

- Create a database `kodekloud_db10`, a database user `kodekloud_aim` and set password`BruCStnMT5` for this new user also remember host should be `localhost`. Finally grant some usual permissions like select, update (or full) ect to this newly created user on newly created database.

- Notes: :- Please make sure to run the puppet agent test using sudo on agent nodes, otherwise you can face certificate issues. In that case you will have to clean the certificates first and then you will be able to run the puppet agent test.

- :- Before clicking on the Check button please make sure to verify puppet server and puppet agent services are up and running on the respective servers, also please make sure to run puppet agent test to apply/test the changes manually first.

- :- Please note that once lab is loaded, the puppet server service should start automatically on puppet master server, however it can take upto 2-3 minutes to start.

## SOLUTION

* - Switch Root user & cd into the folder
    - sudo su -
    - cd /etc/puppetlabs/code/environments/production/manifests/
    - vi games.pp
        ```bash
        class mysql_database {
            package {'mariadb-server':
              ensure => installed
            }

            service {'mariadb':
                ensure    => running,
                enable    => true,
            }    

            mysql::db { 'kodekloud_db10':
            user     => 'kodekloud_raim',
            password => 'BruCStnMT5',
            host     => 'localhost',
            grant    => ['ALL'],
            }
        }
        node 'stdb01.stratos.xfusioncorp.com' {
          include mysql_database
        }
        ```
    - cat games.pp

* - Validate the puppet files
    - puppet parser validate games.pp

* - Login on database server  (stdb01 ) & switch to root  user 
    - ssh peter@stdb01
    - sudo su -

* - Run Puppet agent to pull the configuration from puppet server     
    - puppet agent -tv

* - check mariadb database server status     
    - systemctl status mariadb 

* - Validate the task by running     
    - mysql -u kodekloud_aim -p kodekloud_db10 -h localhost 
    