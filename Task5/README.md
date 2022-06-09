# Ansible Copy Module

## TASK
There is data on jump host that needs to be copied on all application servers in Stratos DC. Nautilus DevOps team want to perform this task using Ansible. Perform the task as per details mentioned below:



- a. On jump host create an inventory file `/home/thor/ansible/inventory` and add all application servers as managed nodes.

- b. On jump host create a playbook `/home/thor/ansible/playbook.yml` to copy `/usr/src/dba/index.html` file to all application servers at location `/opt/dba/`.

Note: Validation will try to run the playbook using command ansible-playbook -i inventory playbook.yml so please make sure the playbook works this way without passing any extra arguments.

## SOLUTION

* cd into folder mentioned in the task and create inventory & playbook files 
    - cd  /home/thor/ansible/
    - ll
    - vi inventory
        ```bash
        stapp01 ansible_host=172.16.238.10 ansible_ssh_pass=Ir0nM@n  ansible_user=tony

        stapp02 ansible_host=172.16.238.11 ansible_ssh_pass=Am3ric@  ansible_user=steve

        stapp03 ansible_host=172.16.238.12 ansible_ssh_pass=BigGr33n ansible_user=banner
        ```
    - cat inventory

* Check the inventory file is working correctly by listing folder on all the app servers and also  Create a playbook as per the task
    - ansible all -a "ls -ltr /opt/" -i inventory
    - vi playbook.yml
        ```bash
        - name: Ansible copy
          hosts: all
          become: yes
          tasks:
            - name: copy index.html to security folder
              copy: src=/usr/src/dba/index.html dest=/opt/dba
        ```
    - cat playbook.yml

* command to execute the playbook 
    -  ansible-playbook -i inventory playbook.yml

* validate the task by running this command
    -  ansible all -a "ls -ltr /opt/dba" -i inventory