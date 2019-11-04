### Using Cloudmapper:

* [Saving Money on AWS With Cloudmapper](https://www.swipeix.com/blog/frugal-aws-usage-saving-money-while-using-aws)


Here are my notes how to use cloudmapper:

* Make sure you have an aws profile setup in ~/.aws/credentials
*


### Usage notes

The account name is the name specified in config.json:

```

venv) $  cp config.json.demo config.json

venv) $ vim config.json

venv) $ python3 cloudmapper.py collect --account timo --profile timo


venv) $ python3 cloudmapper.py prepare --config config.json


 venv) $ python3 cloudmapper.py webserver



```
