## Terraform Cheatsheet

Validate Terraform code:
```
$ terraform validate
```

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

Destroy:

```

$ terraform destroy -target module.acm_dev3.aws_acm_certificate.main_virginia -target module.acm_dev3.aws_acm_certificate.main_singapore -var-file=common/base.tfvars

```


