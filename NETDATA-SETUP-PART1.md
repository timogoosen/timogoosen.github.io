## Install Netdata on Master Node on Debian

Install Net data use quick install script.

```
# bash <(curl -Ss https://my-netdata.io/kickstart.sh)

```

Netdata Receiver config:

```
# /etc/netdata/edit-config stream.conf


```
On receiving node [stream].enabled = no for receiver nodes
https://docs.netdata.cloud/streaming/#options-for-the-receiving-node

OPTIONS FOR THE RECEIVER NODE



Install Nginx and httpasswd app:

```
# apt-get install nginx apache2-utils

```

Create http auth file:

```
# htpasswd -c /etc/nginx/netdata-access timo


```


Use this config:


```
upstream netdata-backend {
    server 127.0.0.1:19999;
    keepalive 64;
}

server {
    listen 51.161.11.19:80;
    server_name example.com;

    auth_basic "Authentication Required";
    auth_basic_user_file netdata-access;

    location / {
        proxy_set_header X-Forwarded-Host $host;
        proxy_set_header X-Forwarded-Server $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://netdata-backend;
        proxy_http_version 1.1;
        proxy_pass_request_headers on;
        proxy_set_header Connection "keep-alive";
        proxy_store off;
    }
}

```


Put this config in :


```


# cd /etc/nginx/sites-enabled/

# mv default ../

# vim default


```


Install certbot:(Gonna use ssl cert from letsencrypt with Nginx)


```

# apt-get install certbot python-certbot-nginx


```


Create SSL cert

netdata.envisage.cloud

```
# certbot --authenticator standalone --installer nginx \
  -d netdata.timo.cloud --pre-hook "service nginx stop" --post-hook "service nginx start"

```


Next on Master node enable TLS support

https://docs.netdata.cloud/web/server/#enabling-tls-support


```

# cp /etc/letsencrypt/live/netdata.timo.cloud/fullchain.pem /etc/netdata/ssl/cert.pem

# cp /etc/letsencrypt/live/netdata.timo.cloud/privkey.pem /etc/netdata/ssl/key.pem


# chown -R netdata:netdata /etc/netdata/ssl/


```

You can edit your netdata config with:

```

# EDITOR=vim ./edit-config netdata.conf


```


Now edit your netdata.conf and add this:


```

[web]
    ssl key = /etc/netdata/ssl/key.pem
    ssl certificate = /etc/netdata/ssl/cert.pem

```


Now restart netdata on master node:

```

# service netdata restart


```
