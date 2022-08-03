## Creating Soft Links Using Ansible

# TASK
The Nautilus DevOps team is practicing some of the Ansible modules and creating and testing different Ansible playbooks to accomplish tasks. Recently they started testing an Ansible file module to create soft links on all app servers. Below you can find more details about it.

Write a playbook.yml under `/home/thor/ansible` directory on jump host, an inventory file is already present under `/home/thor/ansible` directory on jump host itself. Using this playbook accomplish below given tasks:

Create an empty file `/opt/finance/blog.txt` on `App Server 1`; its user owner and group owner should be tony. Create a symbolic link of source path `/opt/finance` to destination `/var/www/html`.

Create an empty file `/opt/finance/story.txt` on `App Server 2`; its user owner and group owner should be steve. Create a symbolic link of source path `/opt/finance` to destination `/var/www/html`.

Create an empty file `/opt/finance/media.txt` on `App Server 3`; its user owner and group owner should be banner. Create a symbolic link of source path `/opt/finance` to destination `/var/www/html`.

Note: Validation will try to run the playbook using command ansible-playbook -i inventory playbook.yml so please make sure playbook works this way without passing any extra arguments.

## SOLUTION

* cd into folder mentioned in the task 
    - cd  /home/thor/ansible/
    - cat inventory
    - ansible all -a "ls -ltr /opt/finance" -i inventory

* Create a playbook as per the task
    - vi playbook.yml
    - cat playbook.yml

* command to execute the playbook 
    -  ansible-playbook -i inventory playbook.yml

* validate the task by running this command
    -  ansible all -a "ls -ltr /opt/finance" -i inventory