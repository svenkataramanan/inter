# EKS cluster
## Create EKS cluster using eksctl
eksctl is a very easy tool to create EKS cluster. Executing ``` eksctl create cluster``` will create the cluster for us with all the default values.
Instead of creating with all default values, we can provide values for the ones we want to override. Provide the override values in a YAML file. I have used _[eks-tw.yaml](./Kubernetes/eks-tw.yaml)_ file.
```
eksctl create cluster -f eks-tw.yaml
```
This would take few minutes to create the cluster.

## EKS cluster validation
To check the creation of the cluster 
```
eksctl get cluster
```
eksctl also creates the config file for _kubectl_. Run kubectl to verify that the nodes are created
```
kubectl get nodes
```

## EKS cluster status
Based on the yaml file, the current cluster has the capacity 3, means that there are 3 nodes running in the node group. Run the command 
```
eksctl get nodegroup --cluster EKS-TW-cluster
```
## EKS cluster scale up
To increase the node count from 3 to 5, run the command
```
eksctl scale nodegroup --cluster=EKS-TW-cluster --nodes=5 --name=ng-1 
```
This scales up the number of nodes in the node group

## EKS cluster scale down
To decrease the node count from 5 to 3, run the command
```
eksctl scale nodegroup --cluster=EKS-TW-cluster --nodes=3 --name=ng-1 
```
This scales down the number of nodes in the node group

***************
## Delete EKS cluster
To delete an EKS cluster, run the command
```
eksctl delete nodegroup --config-file=eks-tw.yaml --include=ng-1 --approve
```

