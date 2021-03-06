## Terraform Cheatsheet

* [My Terraform Local Dev Setup](https://timogoosen.github.io/TERRAFORM_SETUP)

Validate Terraform code:
```
$ terraform validate
```

## Quick Reference:

* [Load Secrets Manager secret from KMS](https://timogoosen.github.io/SECRETS_MANAGER_FROM_KMS)



Lint Terraform code:
```
$ terraform fmt -ls
```

Download and update modules in root of module:
```
$ terraform get
```

Refresh

```
$ terraform refresh

```

Pull the state:

```

$ terraform state pull staging

```

Import a resource:

```

$ terraform import -var-file=common/staging.tfvars aws_security_group.elb_sg sg-07f3fabbb69c1a80f

```
Sometimes if you try import a resource and you dont have any code related to that resource you will get an error, then do this:

```
resource "aws_subnet" "public" {
  # (resource arguments)
}
```
Then try import it: (Now you can import it/them)

```

terraform import -var-file=common/prod.tfvars  aws_subnet.public[2] subnet-02dfb6a3254ba7909
terraform import -var-file=common/prod.tfvars  aws_subnet.public[1] subnet-0e26b354f4a0af2bc
terraform import -var-file=common/prod.tfvars  aws_subnet.public[0] subnet-04ca788ee17dd95a0

```


Destroy:

```

$ terraform destroy -target module.acm_dev3.aws_acm_certificate.main_virginia -target module.acm_dev3.aws_acm_certificate.main_singapore -var-file=common/base.tfvars

```


Use specific PR in terraform module:

```
source = "git@github.com:timogoosen/some-terraform-module?ref=CPE1048"

```

Then 

```
terraform init

```