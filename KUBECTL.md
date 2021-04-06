## Kubectl Cheatsheet

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