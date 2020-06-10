## Add http auth:



You can create the file containing the username and password like this:
```

# apt install apache2-utils


# htpasswd -c /etc/nginx/.htpasswd user1



```

You could also create the username and password and just echo it to a file
in a bashscript. You don't have to use htpasswd for example in a dockerfile
you could just create the file containging the username and password directly.
To prove my point:
```


$ htpasswd -c /tmp/.htpasswd user1

$ cat /tmp/.htpasswd
user1:$apr1$I/8CdqA1$IX1Wbs.vdp2AeiJGbHxaj1
```

To add http auth to nginx:

```
server {
        listen 80;
        server_name site.com;
        location / {
                auth_basic "Username and Password are required";
                auth_basic_user_file /etc/nginx/.htpasswd;
                root /var/www/html/reports;

                autoindex on;
        }
}


```

This add's http auth to a directory with timestamped directories where Jmeter drops its reports. The line that starts with autoindex is a nice way to show the list of directories and update them as Jmeter creates more reports in that directory for Nginx to serve. The HTTP auth protects our reports from being viewed by someone who does not have the password.



## Show real IP behind reverse proxy:

See what IP is being shown in logs:

```
# cd /var/log/nginx
# tail -f fireweb_access.log
```
For example:

```

10.67.240.1 - - [09/Jun/2020:12:34:06 +0000] "GET /fonts/glyphicons-halflings-regular.woff2 HTTP/1.1" 200 23320

```

Now change the Nginx config:

```
# cd /etc/nginx
# vi nginx.conf

```
Put the IP in from the log above:

```

http {
...
        set_real_ip_from  10.67.240.1;
        real_ip_header    X-Forwarded-For;
...
```

Now validate nginx config and reload:
```
# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
Now reload the config:

```
# systemctl reload nginx

```
You can now check the Nginx access logs and you should see the real IP.
