### Kubectl Debugging


Run a debugging pod, for example for testing connections:

```
kubectl run -i --tty --rm debug --image=alpine --restart=Never -- sh

#

```