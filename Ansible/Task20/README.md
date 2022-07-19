## Using Ansible Conditionals

# TASK
The Nautilus DevOps team had a discussion about, how they can train different team members to use Ansible for different automation tasks. There are numerous ways to perform a particular task using Ansible, but we want to utilize each aspect that Ansible offers. The team wants to utilise Ansible's conditionals to perform the following task:

An inventory file is already placed under `/home/thor/ansible` directory on jump host, with all the Stratos DC app servers included.

Create a playbook `/home/thor/ansible/playbook.yml` and make sure to use Ansible's when conditionals statements to perform the below given tasks.

Copy `blog.txt` file present under `/usr/src/data` directory on jump host to `App Server 1` under directory. Its user and group owner must be user tony and its permissions must be `0644` .

Copy `NodePort`story.txt file present under `/usr/src/data` directory on jump host to `App Server 2` under `/opt/data` directory. Its user and group owner must be user steve and its permissions must be `0644` .

Copy `media.txt`file present under `/usr/src/data` directory on jump host to `App Server 3` under `/opt/data` directory. Its user and group owner must be user banner and its permissions must be `0644`.

NOTE: You can use ansible_nodename variable from gathered facts with when condition. Additionally, please make sure you are running the play for all hosts i.e use - hosts: all.

Note: Validation will try to run the playbook using command ansible-playbook -i inventory playbook.yml, so please make sure the playbook works this way without passing any extra arguments.

## SOLUTION

* cd into folder mentioned in the task 
    - cd  /home/thor/ansible/
    - cat inventory
    - ansible all -a "ls -ltr /opt/data" -i inventory
    - ll /usr/src/data/

* Create a playbook as per the task
    - vi playbook.yml
    - cat playbook.yml

* command to execute the playbook 
    -  ansible-playbook -i inventory playbook.yml

* validate the task by running this command
    -  ansible all -a "ls -ltr /opt/data" -i inventory