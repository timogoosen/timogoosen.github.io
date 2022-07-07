### Handy Bash Stuff commonly used CI/CD Pipelines

Some handy stuff used in CI/CD stuff.


## Write an API key to a file from environment variable:

Here we go:

```

echo "website_api_token=\"$TOKEN\"" > gradle.properties


```

Put file as string in CI/CD env variable.
This example uses google service account saved in file /tmp/sa.json

```
export GCR_SECRET=`cat /tmp/sa.json`
```