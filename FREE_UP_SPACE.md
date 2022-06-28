### Free up space 

Systemd based systems:

This cleans up /var/log/journal
```

journalctl --vacuum-size=100M

```