### Useful Gcloud commands:

Get access token OAUTH:

```

gcloud auth print-access-token

```

Set default project:

```

gcloud config set project terraform-base-349707


```

Other login method:

```

gcloud auth login

```

Login to GKE

```

gcloud container clusters get-credentials gitlab-staging --zone europe-west1-b --project terraform-base-349707

```

Can then do:

```

kubectl get pods -A 

```
