### Kubernetes SSL Secrets


## Checks to do:

1. Check cert and the key match using openssl
2. Check that the cert chain works


### Check cert and key match:

Check the cert:

```

openssl x509 -in tls.crt -noout -modulus


```


Check that the key matches:

```

openssl rsa -in tls.key -noout -modulus


```

Its best to just name your key tls.key and cert tls.crt.
Just for the sake of convention.

### How to create the cert with chain:



See example:

```
cat victoriousmarketing.co.za.crt > tls.crt
cat DigiCertCA.crt >> tls.crt
cat TrustedRoot.crt >> tls.crt

```

You can also just open tls.crt and append a ca bundle content in a text editor.

Just remember to check that stuff matches:

```
openssl rsa -in tls.key -noout -modulus

openssl x509 -in tls.crt -noout -modulus

```









Create Kubernetes SSL Secrets:


```

	
kubectl create secret tls test.hairlab.co.za --key="/tmp/test.hairlab.co.za.key" --cert="/tmp/test.hairlab.co.za.cert"


```
