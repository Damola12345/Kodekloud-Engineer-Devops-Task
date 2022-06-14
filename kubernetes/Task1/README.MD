# Set Limits for Resources in Kubernetes

## TASK 
- Create a pod named httpd-pod and a container under it named as httpd-container, use httpd image with latest tag only and remember to mention tag i.e httpd:latest and set the following limits:

- Requests: Memory: 15Mi, CPU: 100m

- Limits: Memory: 20Mi, CPU: 100m

- Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

## SOLUTION
* To run the pod.yml file:
    - kubectl create -f pod.yml