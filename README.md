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
1.8 Get all nodes
```
kubectl get nodes
```
1.9 Describe node
```
kubectl describe node <node-name>
```
2.0 Get all ip on minikube
```
minikube ssh
ip link show
```
2.1 Get all pods and services
```
kubectl get pod,svc -n kube-system
```
2.2 Get all IP in pod
multi-network-pod = name pod;
```
kubectl exec -it multi-network-pod -- ip addr
```
2.3 Get all route in pod
```
kubectl exec -it multi-network-pod -- ip route
```

#### 2. Open Kubernetes dashboard
2.1 Run PowerShell with permission Administrator
2.2 Start server
```
 minikube start --driver=hyperv          
```
2.3 Check node work.
```
minikube ssh
curl -I https://index.docker.io
output:
HTTP/1.1 200 OK
date: Mon, 10 Jun 2024 02:03:03 GMT
content-type: text/html; charset=utf-8
x-xss-protection: 1; mode=block
x-docker-correlation-id: c243d07b-4e2a-49aa-8527-b570d65c6708
x-docker-app-version: v4332.0.0
accept-ch: Sec-CH-Prefers-Color-Scheme
vary: Sec-CH-Prefers-Color-Scheme, Accept-Encoding
x-frame-options: deny
x-content-type-options: nosniff
strict-transport-security: max-age=31536000
```

2.4 Install add-on before open dashboard
```
minikube addons enable metrics-server
```
2.5 Launch Kubernetes dashboard
```
minikube dashboard
```

#### Minikube Hyper-V windows
Reference: https://minikube.sigs.k8s.io/docs/drivers/hyperv/
1. Enable Hyper-V
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```
2. Start
```
minikube start --driver=hyperv 
```
3. Set default
```
minikube config set driver hyperv
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
#### 2. This error is likely caused by:
        - The kubelet is not running
        - The kubelet is unhealthy due to a misconfiguration of the node in some way (required cgroups disabled)
** Fixed by set specific kubernetes version
```
1. minikube delete
2. minikube start --kubernetes-version=v1.29.2
```
