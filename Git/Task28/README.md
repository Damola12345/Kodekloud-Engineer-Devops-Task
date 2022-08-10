## Git Repository Update


# TASK

The Nautilus development team started with new project development. They have created different Git repositories to manage respective project's source code. One of the repo `/opt/apps.git` was created recently. The team has given us a sample `index.html` file that is currently present on jump host under `/tmp`. The repository has been cloned at `/usr/src/kodekloudrepos` on storage server in Stratos DC.

Copy sample index.html file from jump host to storage server under cloned repository at `/usr/src/kodekloudrepos`, add/commit the file and push to master branch.

# SOLUTION

* SCP `index.html` file from jump server to the storage server
    - sudo scp /tmp/index.html  natasha@ststor01:/tmp
    - ssh natasha@ststor01
    - sudo su -

* Go to project repositories as per the task  
    - cd   /usr/src/kodekloudrepos/app/
    - cp /tmp/index.html  .

* Add, commit and push the index.html file
    - git add index.html
    - git commit -m "adding index.html"
    - git push origin master
    - git status