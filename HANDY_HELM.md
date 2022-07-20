### Handy Helm Charts

#### Install Mongodb


Install Mongodb (non sharded)
```
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install my-release bitnami/mongodb

```


Get root password:

```


export MONGODB_ROOT_PASSWORD=$(kubectl get secret --namespace default my-release-mongodb -o jsonpath="{.data.mongodb-root-password}" | base64 -d)


echo $MONGODB_ROOT_PASSWORD=$(kubectl get secret --namespace default my-release-mongodb -o jsonpath="{.data.mongodb-root-password}" | base64 -d)
 ```