### K3s:


Access K3s from outside cluster.

Make a hole in the UFW firewall for 6443.

Then take this config:

```
sudo cat /etc/rancher/k3s/k3s.yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: 
    REDACTED
    server: https://127.0.0.1:6443


```


And change 127.0.0.1 to the actual IP of your server.


Then drop this in :

``` 

~/.kube/config

```

And run 

```

kubectl get pods -A

```

You are now connected to k3s from outside.