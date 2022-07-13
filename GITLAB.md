### Gitlab


* [Give yourself admin privileges from CLI](https://forum.gitlab.com/t/how-do-i-change-my-profile-to-admin/35888/2)
* [Unlock locked out Webinterface user using CLI](https://docs.gitlab.com/ee/security/unlock_user.html)

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


