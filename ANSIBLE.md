### ANSIBLE

List hosts

This is if you run into an issue parsing your hosts file see here:

*[Unable to parse](https://stackoverflow.com/questions/53205687/ansible-unable-to-parse-etc-ansible-hosts-as-an-inventory-source)

```
$ ansible all --list-hosts
```


Run Ansible playbook against single host:

```
debops install-tool.yml -i "machine.com," -u timo

```

Run Ansible play book against localhost:

[Ansible ssh Error Local host connection](https://stackoverflow.com/questions/37184699/ansible-ssh-error-connection-in-localhost)



### Debops

Can be used instead of ansible-playbook command.
