# Ansible Blockinfile Module

## TASK
The Nautilus DevOps team wants to install and set up a simple httpd web server on all app servers in Stratos DC. Additionally, they want to deploy a sample web page for now using Ansible only. Therefore, prepare the required playbook to complete this task. Find more details about the task below.

We already have an inventory file under `/home/thor/ansible` on `jump host`. Create a `playbook.yml` under `/home/thor/ansible` on `jump host` itself.

Using the playbook, install httpd web server on all app servers. Additionally, make sure its service should up and running.

Using blockinfile Ansible module add some content in /`/var/www/html/index.html` file. Below is the content:

Welcome to XfusionCorp!

This is Nautilus sample file, created using Ansible!

Please do not modify this file manually!

The `/var/www/html/index.html`file's user and group owner should be apache on all app servers.

The `/var/www/html/index.html` file's permissions should be `0644` on all app servers.

Note:

- a. Validation will try to run playbook using command ansible-playbook -i inventory playbook.yml so please make sure playbook works this way, without passing any extra arguments.

- b. Do not use any custom or empty marker for blockinfile module.

## SOLUTION

* cd into folder mentioned in the task 
    - cd  /home/thor/ansible/
    - ll

* Create a playbook as per the task
    - vi playbook.yml
    - cat playbook.yml

* command to execute the playbook 
    -  ansible-playbook -i inventory playbook.yml

* validate the task by running this command
    - ansible all -a 'ls -l /var/www/html/' -i inventory
    - curl http://stapp01
    - curl http://stapp02
    - curl http://stapp03