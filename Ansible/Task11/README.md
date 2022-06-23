# Ansible Ping Module Usage


## TASK
- The Nautilus DevOps team is planning to test several Ansible playbooks on different app servers in Stratos DC. Before that, some pre-requisites must be met. Essentially, the team needs to set up a password-less SSH connection between Ansible controller and Ansible managed nodes. One of the tickets is assigned to you; please complete the task as per details mentioned below:

- a. Jump host is our Ansible controller, and we are going to run Ansible playbooks through thor user on jump host.

- b.Make appropriate changes on jump host so that user thor on jump host can SSH into `App Server 3` through its respective sudo user. (for example tony for app server 1).

- c. There is an inventory file `/home/thor/ansible/inventory` on jump host. Using that inventory file test Ansible ping from jump host to `App Server 3`, make sure ping works.

## SOLUTION

* - check the ansible inventory file on jump server host
    - cd  /home/thor/ansible/
    - ll
    - cat inventory

* - Generate a SSH key on Jump Host
    - ssh-keygen -t rsa -b 2048

* - Copy SSH key to setup password-less authentication to the host
    - ssh-copy-id  banner@stapp03

* - Validate the task by below command
    - ansible stapp03 -m ping -i inventory -v