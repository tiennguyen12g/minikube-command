# minikube-command

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
