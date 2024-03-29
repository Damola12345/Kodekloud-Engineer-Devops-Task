# Puppet Multi-Packages Installation

## Task

Some new changes need to be made on some of the app servers in Stratos Datacenter. There are some packages that need to be installed on the `app server 3`. We want to install these packages using puppet only.

Puppet master is already installed on `Jump Server`.

Create a puppet programming file `news.pp` under /etc/puppetlabs/code/environments/production/manifests on master node i.e on Jump Server and perform below mentioned tasks using the same.

Define a class multi_package_node for agent node 3 i.e `app server 3`. Install `app server 3` `net-tools and unzip` packages on the agent node 3.

Notes: :- Please make sure to run the puppet agent test using `sudo` on agent nodes, otherwise you can face certificate issues. In that case you will have to clean the certificates first and then you will be able to run the puppet agent test.

:- Before clicking on the Check button please make sure to verify puppet server and puppet agent services are up and running on the respective servers, also please make sure to run puppet agent test to apply/test the changes manually first.

:- Please note that once lab is loaded, the puppet server service should start automatically on the puppet master server, however it can take upto 2-3 minutes to start.

## SOLUTION

* Go through the folder mentioned in the task and create puppet files 
    - cd /etc/puppetlabs/code/environments/production/manifests/

    - vi news.pp
        ```bash
        class multi_package_node {
        $multi_package = [ 'net-tools', 'unzip']
            package { $multi_package: ensure => 'installed' }

        }

        node 'stapp03.stratos.xfusioncorp.com' {
            include multi_package_node
        }
        ```

    - cat news.pp

* Login in  App server  (stapp03, ) & switch to root  user 
    -  ssh Banner@stapp03
    -  sudo su -

* Run Puppet agent to pull the configuration from puppet server
    - puppet agen -tv

* Validate the task by running
    - rpm -qa |grep -e net-tools -e unzip
