## Testing Ansible code

Maybe usually your ansible code runs via a CI/CD system and you would like to test it on a test instance:

```
# This is the file: host.yml
[hosts]
52.208.116.114 ansible_user=admin hostname=52.208.116.114 ansible_ssh_private_key_file=/Users/timo/.ssh/id_rsa
```

Now run it from your machine you are coding on like this:

```

ansible-playbook --inventory=playbooks/host.yml playbooks/test.yml
```