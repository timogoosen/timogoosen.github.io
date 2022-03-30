### Eternal while loop single line:

Here I'm using it to do a basic healthcheck:

```

while true;do curl -I 'https://devops-tutorials.site/health'; done


```

### How to create a list of comma seperated AWS ARN's from a textfile with resource names:

Here is the resource list:

(name it 1.txt)
```
bucketone
buckettwo
bucketthree
bucketfour

```

Here is the script loop.sh:

```
#!/usr/bin/env bash

while read p; do
  echo "\"arn:aws:glue:eu-west-1:444455556666:database/$p\","
done <1.txt

```

Run loop.sh

```

$ bash loop.sh

"arn:aws:glue:eu-west-1:444455556666:database/bucketone",
"arn:aws:glue:eu-west-1:444455556666:database/buckettwo",
"arn:aws:glue:eu-west-1:444455556666:database/bucketthree",
"arn:aws:glue:eu-west-1:444455556666:database/bucketfour",

```
