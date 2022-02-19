## How to change a cadddy config:


Edit the config:
```
sudo vim /etc/Caddfile

```

Now validate the config:

```
sudo caddy -validate

```

Now reload caddy :

```
sudo systemctl reload caddy;sudo journalctl -fu caddy

```


### Caddy Syntax

Basic reverse proxy with caddy 2:

```

website.devops-tutorials.club {
  reverse_proxy http://127.0.0.1:8000 
}

```

Run with caddy 2 config with caddy 2:

```

sudo caddy run --config /etc/Caddyfile

```