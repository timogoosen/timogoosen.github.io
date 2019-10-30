## AWS Certificate Manager

AWS Certificate manager is AWS's SSL certificate issuer.
You can easily and free (as far as I remember) create SSL certificates and easily add them to your load balancer.

## Ways of Validating SSL Certs

There are two ways to validate an SSL cert:

* Email: This will send an email to one of the emails registered to the registrar, all you need to do is click on the link and this will prove that you own the domain.
* DNS: You can add a DNS record either with route53 or with your own DNS host to prove domain ownership. This one can be tricky sometimes, but once you get the hang of it, it is quite rewarding.

### DNS Validation Format:

The format you need to use in raw DNS is:
```
...
_3b396ed1e69010620c926960d51eae40 300 IN CNAME _e94ae79994726df6ca4cdae6d162a0e0.kirrbxfjtw.acm-validations.aws.
...
```
This is to register the domain name: *.devops-tutorials.site to use an SSL certificate from AWS Certificate Manager.

The format that AWS gave me (which didn't help that much) was:
```

Domain Name,Record Name,Record Type,Record Value
*.devops-tutorials.site,_3b396ed1e69010620c926960d51eae40.devops-tutorials.site.,CNAME,_e94ae79994726df6ca4cdae6d162a0e0.kirrbxfjtw.acm-validations.aws.


```
