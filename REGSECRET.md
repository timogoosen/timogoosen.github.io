#### Use Gitlab docker registry with Kubernetes


Use the following to create the secret:


```
kubectl create secret docker-registry gitlabregistrykey
--docker-server=registry.gitlab.com --docker-username="somegitlabusername"
--docker-password="blahblah"
--docker-email="example@gmail.com" -n gitlab

```

To be able to push to gitlab registry make an ENV var in your CI/CD pipeline:

DOCKER_AUTH_CONFIG


Then put this value in that env val:

```

{
    "auths": {
        "registry.gitlab.com": {
            "auth": "blahblahinbas64"
        }
    }
}


```


### Using Google Artifact or Container Registry Service Account with EKS or any non-gcp K8s:


To create the regsecret to be able to pull from eu.gcr.io:


```

kubectl create secret docker-registry regsecret \
 --docker-server=eu.gcr.io \
 --docker-username=_json_key \
 --docker-password="$(cat /tmp/secret-gcr.json)" \
 --docker-email=any@valid.email

```


Your service account just as you would paste it in json in CI/CD would be saved locally in /tmp/secret-gcr.json
