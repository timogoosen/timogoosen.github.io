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




### AWS S3

Bulk rename stuff based on prefix /mix of regex:


Moves any files with this name format: 

20210715T125704Z_20210715T125734Z_3207c6ea.log.gz into folder 20210715/ 
```


aws s3 mv s3://cloudflare-access-logs/cloudflare-logpush/website.co.ug/ s3://cloudflare-access-logs/cloudflare-logpush/website.co.ug/20210715/ --recursive --exclude="*" --include "20210715T*.log.gz" --dryrun --profile cloudflare-stuff

```


### Encrypt URL with KMS

Normally if you try encrypt a url with KMS you would get the error:

```
Error parsing parameter '--plaintext': Unable to retrieve
```

I found this useful issue on github, explaining how to do it:

* [Encrypt URL with KMS](https://github.com/aws/aws-cli/issues/2867)


```

  aws \
    --profile "testing" \
    kms encrypt \
    --key-id "$KEY" \
    --plaintext fileb://<(echo -n 'https://hooks.slack.com/workflows/supersecretstuff/urlissecret') \
    --output text \
    --query CiphertextBlob

```