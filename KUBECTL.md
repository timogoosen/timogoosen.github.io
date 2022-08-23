## Kubectl Cheatsheet


List container images on K8's cluster:

```

for image in $(kubectl get pods --all-namespaces --output=jsonpath='{..image}'); do     echo $image; done

```

Open shell in container in namespace:

```

kubectl -n pr-311-1-pae4yo exec backend-0 --container php-fpm  -it -- /bin/bash


```

Get Namespaces (shortcut):

```

kubectl get ns

```

Get all pods:

```

kubectl get pods --all-namespaces

```

Shortcut get all pods in all namespaces:

```

kubectl get pods -A

```

View resources (memory and CPU on a pod):

```

kubectl get pod prod-some-app-chrt-prod-only-1619163300-xljjl -o yaml

```


### Deleting stuff:


Delete all resources in a given namespace:

```
kubectl delete all --all -n test-namespace

```