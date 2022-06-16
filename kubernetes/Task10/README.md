## Create Namespaces in Kubernetes Cluster

# TASK
The Nautilus DevOps team is planning to deploy some micro services on Kubernetes platform. The team has already set up a Kubernetes cluster and now they want set up some namespaces, deployments etc. Based on the current requirements, the team has shared some details as below:

- Create a namespace named `dev` and create a POD under it; name the pod `dev-nginx-pod` and use nginx image with latest tag only and remember to mention tag i.e `nginx:latest`.

Note: The kubectl utility on `jump host` has been configured to work with the kubernetes cluster.

## SOLUTION
* At first run below commands
    -  kubectl get namespace
    -  kubectl get pods

* Create namespace
    - kubectl create namespace dev
    - kubectl get namespace

* Run the below command to create a pod
    - kubectl run dev-nginx-pod --image=nginx:latest -n dev --dry-run=client -o yaml > pod.yml
    - kubectl get pods -n dev