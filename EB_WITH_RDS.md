## EB With RDS

You can use EB With RDS and have the environment spun up
in parrallel with the database. You can do it with:

```

$ eb create --instance_type t2.micro --database.engine mysql --database.username dbuser testing

```

See the disclaimer in the following document:

* [EB With RDS Official AWS Docs](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.RDS.html)
