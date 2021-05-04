### AWS-CLI 

There are two versions of the AWS CLI since 2020.
They are:

* AWS CLI Version 1.9
* AWS CLI Version 2

### AWS-CLi Version 1.9:

List user profiles in ~/.aws/credentials: (Bit hacky)

```
$ cat ~/.aws/credentials | grep -o '\[[^]]*\]'

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

