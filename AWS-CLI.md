### AWS-CLI 

There are two versions of the AWS CLI since 2020.
They are:

* AWS CLI Version 1.9
* AWS CLI Version 2

### AWS-CLi Version 1.9:

List user profiles in ~/.aws/credentials: (Bit hacky)

```
$ grep -o '\[[^]]*\]' < $HOME/.aws/credentials | sed 's/^\[\(.*\)\]$/\1/'


[default]
[TIMO]
[test-rimu]
...



```


### AWS-CLi Version 2:

List user profiles in ~/.aws/credentials:

```
$ aws configure list-profiles
default
testing
app-key
staging-static-user
static-2
static-dev-user
not-testing
....

```

### Get Current user ARN:

With AWS-CLI Version 1.9:

```

$ aws iam get-user --profile testing-account-full-sqs-access
{
    "User": {
        "Path": "/",
        "UserName": "timo-test",
        "UserId": "AIDATLUYLEHUGJNZXHTQF",
        "Arn": "arn:aws:iam::redacted:user/timo-test",
        "CreateDate": "2021-05-25T14:36:28Z",
        "Tags": [
            {
                "Key": "testing",
                "Value": "by hand"
            }
        ]
    }
}

```

### Download Cloudwatch logs to local:

This downloads cloudwatch logs in text so you can grep through them locally:


```
aws logs get-log-events --log-group-name prod-app --log-stream-name nginx/nginx/be7486d3666e46979d596e92cf438154 --output text > a.log --profile prod-app
```