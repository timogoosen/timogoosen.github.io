
## EKSCTL

Create cluster:

```

eksctl create cluster --name my-eks-cluster --nodes 3 --nodes-min 3 --nodes-max 5 --node-type t2.micro --region us-west-2 --profile timo

```

See nodes:

```

$ kubectl get nodes

NAME                                           STATUS   ROLES    AGE    VERSION
ip-192-168-2-102.us-west-2.compute.internal    Ready    <none>   110s   v1.14.7-eks-1861c5
ip-192-168-71-119.us-west-2.compute.internal   Ready    <none>   108s   v1.14.7-eks-1861c5
ip-192-168-85-169.us-west-2.compute.internal   Ready    <none>   113s   v1.14.7-eks-1861c5



```

Delete cluster again:

```

 $ eksctl delete cluster --name my-eks-cluster --region us-west-2 --profile timo

 ```
