### Gitlab


* [Give yourself admin privileges from CLI](https://forum.gitlab.com/t/how-do-i-change-my-profile-to-admin/35888/2)
* [Unlock locked out Webinterface user using CLI](https://docs.gitlab.com/ee/security/unlock_user.html)
* [Grant Access to private gitlab container registry from CI Job](https://docs.gitlab.com/ee/ci/docker/using_docker_images.html#access-an-image-from-a-private-container-registry)




Maintenence stuff:

* [Rake cleanup tasks](https://docs.gitlab.com/ee/raketasks/cleanup.html)


### General


The general gitlab config file:

```

# vim /etc/gitlab/gitlab.rb

```

## Good practices for upgrades and testing:

* Comment out secrets for backups when testing stuff on a staging instance using a prod image
* Comment out email creds during upgrades or testing
* Change url if doing something testing related with a instance backup from prod 

E.g:

```


external_url 'https://staging-gitlab.timo.test'
# external_url 'https://gitlab.timo.test'
```

### Grant access to private gitlab registry from CI JOB:


Do this:

```
echo -n "my_username:my_password" | base64

```

Take the output and put it in a file in this format:

```

{
    "auths": {
        "registry.example.com:5000": {
            "auth": "(Base64 content from above)"
        }
    }
}

```

Then put it in an env variable in your CI job as:

```

DOCKER_AUTH_CONFIG

```


### Create secret in Kubernetes to pull from gitlab private registry:


```


kubectl -n test-app create secret generic gitlab-registry \
    --from-file=.dockerconfigjson=/tmp/docker.json \
    --type=kubernetes.io/dockerconfigjson

```

