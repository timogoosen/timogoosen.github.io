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

## Deploy:

To deploy a zip, put the following in your .elasticbeanstalk/config.yaml

```
...
    deploy:
  artifact: app.zip

```

Then run this on the machine that you are deploying from:


```

$ zip -r app.zip .

```

That recursively creates a zip in the current directory you are at. 
The zip can be deployed with:
```
$ eb deploy --debug

```

In another console you can check the current activity with:
```
$ eb events -f

```

## Create env with RDS also configured:

You can create an environment with RDS with the following:
```
$ eb create --instance_type t2.micro --database.engine mysql --database.username dbuser eb-poc-env-with-rds

RDS Password:
```


## Enable Cloudwatch Instance logs

You can enable instance logs for Elasticbeanstalk that will log to Cloudwatch. This can be done via the command line with:
```
$ eb logs --cloudwatch-logs enable

```
