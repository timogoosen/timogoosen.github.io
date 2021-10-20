## Terraform upgrade:

Upgrade notes for upgrading between different versions.

### Upgrade from 0.12 to 0.13

```
echo "0.13.7" > .terraform-version

tfenv install 0.13.7

tfenv use 0.13.7

terraform 0.13upgrade

```

Then run the following:

```
terraform init -reconfigure


```

Make sure to have the version number in version.tf:

```


terraform {
  required_version = ">= 0.13"
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "~> 3.37.0"
    }
...
```

### Upgrade from 0.13 to 0.14

