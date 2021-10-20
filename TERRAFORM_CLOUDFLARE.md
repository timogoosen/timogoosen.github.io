## CloudFlare Terraform 

Notes on using Cloudflare Provider for Terraform



## SRV Record:

* [SRV Records in Terraform with Cloudflare](https://www.endpoint.com/blog/2018/06/srv-dns-terraform-cloudflare/)

Example from article:


```

resource "cloudflare_record" "_sip_tls" {
  domain = "${var.domain}"
  name   = "_sip._tls.${var.subdomain}"
  type   = "SRV"
  data   = {
    service  = "_sip"
    proto    = "_tls"
    name     = "${var.subdomain}."
    priority = 100
    weight   = 1
    port     = 443
    target   = "sipdir.online.lync.com."
  }
}

```