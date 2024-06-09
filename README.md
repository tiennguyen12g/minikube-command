# minikube-command
### Reference
https://kubernetes.io/docs/tutorials/hello-minikube/
#### 1. Command
1.1 Start minikube
```
minikube start
```
1.2 Check kubernetes cluster is running
```
kubectk cluster-info
```
1.3 Get all clusters
```
kubectl get services
```
1.4 Create simple node
```
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
```
1.5 Check all node deployed
```
kubectl get deployments
```
1.6 Get all pods
```
kubectl get pods
```
1.7 View config
```
kubectl config view
```

## B. Error
#### 1. Unable to resolve the current Docker CLI context "default": context "default": context not found: open C:\Users\tienn\.docker\contexts\meta\37a8eec1ce19687d132fe29051dca629d164e2c4958ba141d5f4133a33f0688f\meta.json: The system cannot find the path specified.

when run "minikube service hello-node" it throw this error.
fix
```
docker context use default
```
output:  
C:\Users\tienn>docker context use default
default
Current context is now "default"
