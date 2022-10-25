###CERTBOT-ZEROSSL


Using certbot with zerossl:


```

$ sudo certbot certonly --manual --preferred-challenges=dns -d k8s-zerossl.hairlab.co.za -d nonexistent.k8s-zerossl.hairlab.co.za --server https://acme.zerossl.com/v2/DV90


```