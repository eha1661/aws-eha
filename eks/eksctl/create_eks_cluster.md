

# eksctl

__eksctl__ is a simple CLI tool for creating and managing clusters on EKS - Amazon's managed Kubernetes service for EC2.
It is recommended for quick provising (test) for eks clusters. 

__________________________________________________________________________________________________________________________
## 1. Commands

* list clusters
``` bash
eksctl get cluster [--name=<name>][--region=<region>]
```

* Create a cluster using config file and save creds locally
``` bash
eksctl create cluster --config-file=<path> --kubeconfig=./config-cluster
```

* Delete the cluster and its associated nodes
``` bash
eksctl delete cluster --name=<cluster-name>
```
__________________________________________________________________________________________________________________________
## 2. test deployement
In order to test our cluster, we create a deployement and a loadbalancer server 

1. create deployement
```
kubectl apply -f deployement.yml
kubectl get deployement
```

2. check if the application runs correctly. connect to it using port-forward
```
kubectl get pods
kubectl port-forward <hello-kubernetes-XXXX> 8080:8080
```
> http://localhost:8080 


3. create loadbalancer service
```
kubectl apply -f service-loadbalancer.yml
kubectl get service
```

4. use the url to check the app "LoadBalancer Ingress"
```
kubectl describe service hello-kubernetes
```


>  __note__
* Configure kubeconfig Use KUBECONFIG environment variable to point to config file 
``` bash
export KUBECONFIG=$(pwd)/config-cluster
```

__________________________________________________________
resource
* [Offial doc](https://eksctl.io/)
* [Config file schema](https://eksctl.io/usage/schema/)

