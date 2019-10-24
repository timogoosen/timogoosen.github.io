### How to install Elasticbeanstalk CLI

## Create virtualenv Python3:

Create the virtualenv , assuming you have Python3 installed:

```
$ virtualenv -p python3 myenv
Running virtualenv with interpreter /usr/local/bin/python3
Already using interpreter /usr/local/opt/python/bin/python3.7
Using base prefix '/usr/local/Cellar/python/3.7.4/Frameworks/Python.framework/Versions/3.7'
New python executable in /Users/timo/Desktop/elastic-beanstalk/myenv/bin/python3.7
Also creating executable in /Users/timo/Desktop/elastic-beanstalk/myenv/bin/python
Installing setuptools, pip, wheel...
done.
```

Now activate the virtualenv:

``` 
$ source myenv/bin/activate
(myenv) $

```

Now install the Elastic Beanstalk cli in the Virtualenv:

``` 
(myenv) $ pip install awsebcli --upgrade 
```

****
