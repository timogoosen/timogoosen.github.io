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
