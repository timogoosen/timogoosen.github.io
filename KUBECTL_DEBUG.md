### Kubectl Debugging


Run a debugging pod, for example for testing connections:

```
kubectl run -i --tty --rm debug --image=alpine --restart=Never -- sh

#

```

Remember to specify the namespace if you want to test connectivity to a container or pod in a specific namespace:

```

kubectl -n pritunl run -i --tty --rm debug-2 --image=alpine --restart=Never -- sh

```

