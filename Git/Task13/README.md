# Git Create Branches

## Task

- Nautilus developers are actively working on one of the project repositories, `/usr/src/kodekloudrepos/apps`. They recently decided to implement some new features in the application, and they want to maintain those new changes in a separate branch. Below are the requirements that have been shared with the DevOps team:


- On Storage server in Stratos DC create a new branch `xfusioncorp_apps` from master branch in `/usr/src/kodekloudrepos/apps` git repo.

- Please do not try to make any changes in code.

## SOLUTION

* -  Login on to storage server  & Switch Root user
    - ssh natasha@ststor01
    - sudo su -

* - Cd into project repositories
    - cd /usr/src/kodekloudrepos/apps
    - ll

* - Checkout  to master to create a new branch from master
    - git checkout master
    - git checkout -b xfusioncorp_apps 
    - git status
    - git branch -a 