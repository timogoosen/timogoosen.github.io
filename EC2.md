## Get list of Debian AMI's in a region:

Get Debian 10 AMI's in EU-west-1:

```

aws ec2 describe-images --region eu-west-1 --owners 136693071363 --filters 'Name=architecture,Values=x86_64' 'Name=name,Values=debian-10*' --query 'sort_by(Images, &CreationDate)[].[CreationDate,Name,ImageId]' --output table
```

Will output something like:


```

---------------------------------------------------------------------------------------
|                                   DescribeImages                                    |
+--------------------------+--------------------------------+-------------------------+
|  2019-09-09T08:52:00.000Z|  debian-10-amd64-20190909-10   |  ami-06a53bf81914447b5  |
|  2019-10-15T13:39:57.000Z|  debian-10-amd64-20191015-47   |  ami-02498d1ddb8cc6a86  |
|  2019-11-13T17:43:59.000Z|  debian-10-amd64-20191113-76   |  ami-03f98a7b7f2a1cd77  |
|  2019-11-18T18:58:10.000Z|  debian-10-amd64-20191117-80   |  ami-0e9cc061cd3259f22  |
|  2020-02-10T18:43:04.000Z|  debian-10-amd64-20200210-166  |  ami-006d280940ad4a96c  |
|  2020-04-25T15:04:18.000Z|  debian-10-amd64-20200425-243  |  ami-04b94e71a96cb4031  |
|  2020-04-29T16:09:27.000Z|  debian-10-amd64-20200429-248  |  ami-0a84f8748a1b89900  |
|  2020-05-11T18:44:06.000Z|  debian-10-amd64-20200511-260  |  ami-0c731bd1cf5334080  |
|  2020-06-10T14:58:41.000Z|  debian-10-amd64-20200610-292  |  ami-07a3d047ffae3d87f  |
|  2020-06-10T20:29:40.000Z|  debian-10-amd64-20200610-293  |  ami-019745dc682c2e518  |
|  2020-08-03T13:55:46.000Z|  debian-10-amd64-20200803-347  |  ami-093185e1a0acee74b  |
|  2020-09-28T16:20:16.000Z|  debian-10-amd64-20200928-405  |  ami-0bf0495c4dad764c2  |
|  2020-09-28T23:58:55.000Z|  debian-10-amd64-20200928-407  |  ami-0ec224441e69e034e  |
|  2020-10-13T14:57:14.000Z|  debian-10-amd64-20201013-422  |  ami-009762633c0bca7c5  |
+--------------------------+--------------------------------+-------------------------+

```


See here for more info:


* [Debian AMIs on Debian Wiki](https://wiki.debian.org/Amazon/EC2/HowTo/awscli)


The default username should be "admin".