## My Borgmatic Notes

Validate your config:

```
$ sudo validate-borgmatic-config

```

### Consistency checks:

You can run them from commandline:

```
borgmatic check --only archives

```

Or from your config

```

consistency:
    checks:
        - data

```

* [Consistency checks borgmatic config](https://torsion.org/borgmatic/docs/how-to/deal-with-very-large-backups/)

