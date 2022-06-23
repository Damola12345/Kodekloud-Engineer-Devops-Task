# Git Manage Remotes

## TASK
- The xFusionCorp development team added updates to the project that is maintained under /opt/apps.git repo and cloned under /usr/src/kodekloudrepos/apps. Recently some changes were made on Git server that is hosted on Storage server in Stratos DC. The DevOps team added some new Git remotes, so we need to update remote on /usr/src/kodekloudrepos/apps repository as per details mentioned below:



- In /usr/src/kodekloudrepos/apps repo add a new remote dev_apps and point it to /opt/xfusioncorp_apps.git repository.

- There is a file /tmp/index.html on same server; copy this file to the repo and add/commit to master branch.

- Finally push master branch to this new remote origin.

## SOLUTION
* first login on storage server  & Switch to  root user 
    - ssh natasha@ststor01
    - sudo su -

* Navigate to the cloned directory 
    - cd /usr/src/kodekloudrepos/apps
    - ll
    - git status
    - git branch -a

* Add Remote repo as per the task 
    - git remote add dev_apps /opt/xfusioncorp_apps.git

* Copy HTML file from tmp to repo and add
    - cp /tmp/index.html .
    - ll

* initialize the new remote repo  
    - git init
    - git status

* Add and commit the index.html file and also push the master branch to new remote origin.
    - git add index.html
    - git status
    - git commit -m "index.html"
    - git branch -a
    - git push -u dev_apps  master