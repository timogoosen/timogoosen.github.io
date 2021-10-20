## CloudFlare Terraform 

Notes on using Cloudflare Provider for Terraform



## SRV Record:

* [SRV Records in Terraform with Cloudflare](https://www.endpoint.com/blog/2018/06/srv-dns-terraform-cloudflare/)
* [Official Docs Contain SRV example too](https://registry.terraform.io/providers/cloudflare/cloudflare/latest/docs/resources/record)

Example from article:


```

resource "cloudflare_record" "_sip_tls" {
  zone_id = var.cloudflare_zone_id
  name    = "_sip._tls"
  type    = "SRV"

  data {
    service  = "_sip"
    proto    = "_tls"
    name     = "terraform-srv"
    priority = 0
    weight   = 0
    port     = 443
    target   = "example.com"
  }
}

```