###CERTBOT-ZEROSSL


Using certbot with zerossl:


```

$ sudo certbot certonly --manual --preferred-challenges=dns -d test.hairlab.co.za --server https://acme.zerossl.com/v2/DV90 --eab-kid 'REDACTED' --eab-hmac-key 'REDACTED'


```

Then check with dig after adding DNS Entry:

```
dig -t txt _acme-challenge.test.hairlab.co.za

...


;; ANSWER SECTION:
_acme-challenge.test.hairlab.co.za. 300	IN TXT	"Qy5mn5chPSHsmCPpeQnBJTObY0CS98-9JRbsmbWquik"

...

```