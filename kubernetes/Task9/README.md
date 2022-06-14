## Rolling Updates And Rolling Back Deployments in Kubernetes

# TASK
There is a production deployment planned for next week. The Nautilus DevOps team wants to test the deployment update and rollback on Dev environment first so that they can identify the risks in advance. Below you can find more details about the plan they want to execute.


- Create a namespace `xfusion`. Create a deployment called `httpd-deploy`under this new namespace, It should have one container called `httpd`, use `httpd:2.4.27` image and 4 replicas. The deployment should use `RollingUpdate` strategy with maxSurge=1, and maxUnavailable=2. Also create a `NodePort` type service named  `httpd-service`and expose the deployment on `nodePort: 30008`.

- Now upgrade the deployment to version `httpd:2.4.23` using a rolling update.

- Finally, once all pods are updated undo the recent update and roll back to the previous/original version.

Note: The kubectl utility on `jump host` has been configured to work with the kubernetes cluster.

## SOLUTIONS

* Get all namespace 
    - kubectl get namespace 

* Create namespace
    - kubectl create namespace  xfusion

* Run below command to create deployment and service 
    - kubectl apply  -f deploy.yml
    - kubectl apply  -f service.yml
    - kubectl get pods -n xfusion
    - kubectl get deployment -n xfusion

* Run below command to Perform  rolling update
    - kubectl set image deployment httpd-deploy  httpd=httpd:2.4.43 --namespace xfusion --record=true

* Rollback the deployment as per task  
    - kubectl rollout undo deployment httpd-deploy  -n xfusion 
    - kubectl rollout status deployment httpd-deploy  -n xfusion 
    - kubectl get pods -n xfusion
    - kubectl get deployment -n xfusion -o wide

