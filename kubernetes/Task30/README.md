## Rolling Updates in Kubernetes

# TASK
We have an application running on Kubernetes cluster using nginx web server. The Nautilus application development team has pushed some of the latest changes and those changes need be deployed. The Nautilus DevOps team has created an image `nginx:1.19` with the latest changes.


Perform a rolling update for this application and incorporate `nginx:1.19` image. The deployment name is `nginx-deployment`

Make sure all pods are up and running after the update.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

## SOLUTION
* At first run below commands to check 
    -  kubectl get po,deploy

* Check what deployment version is running on the container
    - kubectl get deploy -o wide

* Update the image version to nginx:1.18 from nginx:1.19
    - kubectl set image deployment/nginx-deployment nginx-container=nginx:1.19 --record=true

* Check the status of the pods
    - kubectl get po,deploy
    - kubectl get deploy -o wide

* Check the rollout history 
    - kubectl rollout history deployment