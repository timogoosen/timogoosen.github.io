## Using Elasticbeanstalk

Deploy with Debugging options:

```
$ eb deploy --debug

```

Some other debugging options:

```
$ eb status --verbose

$ eb health --refresh

```

Create env and SSH Into it:

```

$ create eb-poc-env-without-rds
$ eb ssh esh eb-poc-env-without-rds

```
