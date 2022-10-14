### Useful Gcloud commands:



#### Project related commands


List available projects:

```

gcloud projects list

```


Set project:

```

gcloud config set project terraform-base-349707


```



#### Auth and Login related:

Get access token OAUTH:

```

gcloud auth print-access-token

```


Other login method:

```

gcloud auth login

```

### GKE / K8s Related:

Login to GKE

```

gcloud container clusters get-credentials gitlab-staging --zone europe-west1-b --project terraform-base-349707

```

Can then do:

```

kubectl get pods -A 

```
