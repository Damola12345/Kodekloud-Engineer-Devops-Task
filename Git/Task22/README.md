## Resolve Git Merge Conflicts


# TASK

Sarah and Max were working on writting some stories which they have pushed to the repository. Max has recently added some new changes and is trying to push them to the repository but he is facing some issues. Below you can find more details:

SSH into storage server using user `max` and password `Max_pass123`. Under `/home/max` you will find the story-blog repository. Try to push the changes to the origin repo and fix the issues. The `story-index.txt` must have titles for all 4 stories. Additionally, there is a typo in The Lion and the Mooose line where Mooose should be Mouse.

Click on the Gitea UI button on the top bar. You should be able to access the Gitea page. You can login to Gitea server from UI using username `8080`sarah and password `Sarah_pass123` or username `max` and password `Max_pass123`.

Note: For these kind of scenarios requiring changes to be done in a web UI, please take screenshots so that you can share it with us for review in case your task is marked incomplete. You may also consider using a screen recording software such as loom.com to record and share your work.

## SOLUTION
* First login on storage server  & Switch to  root user 
    - ssh max@ststor01
    - cd /home/max/story-blog/
    - git config --global --add user.email max@stratos.xfusioncorp.com
    - git config --global --add user.name max
    - git pull origin master

* Edit the merge conflict story file need to do change 
    - vi story-index.txt
    ```bash
        1. The Lion and the Mouse
        2. The Frogs and the Ox
        3. The Fox and the Grapes
        4. The Donkey and the Dog
        ```
    
* Add and commit the story  file
    -  git add story-index.txt
    - git commit -m "fix typo err"
    - git push origin master
    - git status