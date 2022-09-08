### TERRAFORM_GCP


This will show you how to get terraform working with GCP using a google cloud storage backend.


This is what the backend should look like:

```

terraform {
  backend "gcs" {
    bucket = "terraform-dns-demo" # Can have different env's states in same bucket
    prefix = "terraform/state"

  }
}



```

To get temporary service creds to run terraform on your workstation, use this command:
(These creds expire after a while)

```

gcloud auth application-default login


```

Or get temporary OAUTH Token like this:

```

gcloud auth print-access-token

```

Can also do it like this:


```

export GOOGLE_OAUTH_ACCESS_TOKEN=$(gcloud auth print-access-token)

```
